# CSS笔记



## 各种细节

#### 块元素 和 内联元素

块元素：\<div> \<p> \<h1> \<h2>
特点：会独占一整行，无论他的内容有多少

#### 内联元素：

\<span> span标签专门用来选中文字
\<img> \<iframe> \<a>
特点：只占自身大小的元素，不会占用一行

**注意：** 块元素主要用来做页面中的布局，内联元素主要用来选中文本 设置样式

一般情况下只是用**块元素**包含**内联元素**，而不会使用**内联元素**包含**块元素**


#### 选择器

```css
/* 
 * class属性用.获取
 * id属性用#获取
 * 元素直接获取 例: p{}
 * 元素后面直接加[title]表示含有title属性的某元素直接被获取 
 * 
 * CSS属性选择器
 * -title属性利用元素后面加[title="..."]获取title为特定名称的元素
 * -title属性利用元素后面加[title=^"..."]获取名称title以...开头的元素
 * -title属性利用元素后面加[title=$"..."]获取名称title以...结尾的元素
 * -title属性利用元素后面加[title=*"..."]获取名称title包含...的元素
 */
p {			
    /* 直接操作全部p元素 */
    font-size: 50px
}
.show {
    /* 操作class属性为show的元素 */
}
#bnt {
    /* 操作id属性为btn的元素 */
}
div.btn_enter {
    /* 操作class属性为btn_enter的div元素 */
}
div span {
    /* 操作父元素是div的span元素 */
}
#box2 p span{
	/* 后代选择器 操作id属性是box2的元素的子元素是p的子元素是span */
}
div > h1{
	// 子元素选择器 选中指定父元素的指定子元素
}
```



#### 伪类选择器

```css
a:link{
	/* 没访问过的css*/
	color: greenyellow;
}
a:visited{
	/* 浏览过的css*/
	color: #cd8c26;
}
a:link{
	/* 没访问过的css*/
	color: greenyellow;
}
a:visited{
	/*
	 * 浏览过的css
	 * 浏览器根据历史记录判断链接是否访问过
	 * 由于涉及到用户隐私，所以只能设置字体
	 */
	color: #cd8c26;
}
a:hover{
	/* 表示鼠标移动到链接上*/
	color: skyblue;
}
a:active{
	/* 超链接被点击的状态*/
	color: #1b1813;
}
p:hover{
    /* 鼠标移动到某个元素上面时 */
    background-color: cornflowerblue;
}
input:focus{
    background-color: pink;
}
p::selection{
    /* 选中某个元素时 */
    background-color: #cd8c26;
}
  /*  低版本火狐浏览器需要用到 */
p::-moz-selection{
      
}
```



#### 伪元素

```css
p:first-letter{
    /* 为p中第一个字符设置特殊格式*/
    color: salmon;
    font-size: 30px;	
}
p:first-line{
    /* 为p中第一行设置特殊格式*/
    background-color: burlywood;
}
p:before{
    /*
     * :before表示元素的最前边的部分
     * :after表示元素的最后边的部分
     * 一般都需要结合content央视一起使用
     * 通过content可以向before或after的位置添加一些内容
     */
    content: "在P标签的前面";
    color: blueviolet;
}
body > p:first-child{
  /* body下的第一个元素p */
    background-color: #f9e4ac;
}
p:nth-child(2){
    /* 选取第二个元素(默认是body下的)
     * 参数为even选取偶数
     * 参数为odd选取奇数
     */
	background-color: #999999;
}
p:first-of-type{
    /* 选取第一个指定的元素 */
    background-color: #cd8c26;
}

  /*  注意：
   *  child是在所有的子元素中排列
   *  type是在当前类型的子元素中排列
   */
```



#### 兄弟元素选择器

```css
span ~ p{
    /* + 设置span后的一个p元素
     * ~ 设置span后的一个p元素
     * 兄弟选择器
     *   前者元素的后紧挨着指定的兄弟元素
     */
	color: blueviolet;
}
```



#### 优先级规则

!important(在样式最后添加)[慎用]           最高
内联样式(即直接在元素中控制)      		1000
id选择器                                           		 100
类和伪类(注意事项见下文)                  	10
元素选择器                                      		 1
通配                                                  		 0
继承的样式                                       		没有优先级

⭐当选择其中包含多种选择器的时候，需要将多种选择器的优先级相加然后再比较
且选择器得优先级计算不会超过它的最大的数量级
如果选择器的优先级一样，则使用靠后的样式
并集的选择器的优先级是单独计算的(例如：p, #content){}
⭐ 关于四个伪类，优先级是一样的 使用顺序：link, visit, hover, active



#### 文本标签

```html
<em></em>表示语气的强调，<i>                         => 浏览器中表现出斜体
<strong></strong>表示强调的内容，比em更强烈，<b></b>   => 浏览器中表现出粗体
<small></small>会比父元素的文字要小一些
<cite></cite>加书名号的内容都可以加该标签               => 浏览器中表现出斜体
<q></q> 针对引用的话(内联元素)                        => 浏览器中表现出自动加双引号 			 
<blockquote></blockquote>(作用用上，块级元素)
<sup></sup>用于上标，<sub></sub>用于下标
<ins></ins>表示插入的内容                            => 浏览器中表现出加上下划线
<del></del>表示删除的内容                            => 浏览器中表现出加删除线
<pre></pre>保留原格式(展示代码) <code></code>保留原格式(不展示代码)
通常使用<code><pre></pre></code>
```



#### 列表

```html
<p>
    有序列表及无序列表
</p>
<ul>
    <li>无序列表a</li>
    <li>无序列表b</li>
    <li>无序列表c</li>
</ul>
<--!
     ul和li为无序列表均为块元素
     type属性可以修改无序列表的项目符号 建议在css中操作
     
     把ul替换为ol即为有序列表，type类型指定需要的类型:1.默认使用阿拉伯数字；2.a/A采取小写或大写字母作为序号；3.i/I采取小写或者大写的罗马数字作为序号
     而且列表之间可以互相嵌套
     ></--!>

<ul>
    <li>
        鱼香肉丝
    	<ol>
        	<li>鱼</li>
            <li>肉丝</li>
        </ol>
    </li>
</ul>


<P>
    定义列表
</P>
<--!
     dl用来创建一个定义列表
     	dt: 被定义的内容
     	dd: 对定义内容的描述
     同样dl和ul和ol之间都可以互相镶嵌
     ></--!>
<dl>
    <dt>武松</dt>
    <dd>景阳冈打虎英雄</dd>
</dl>
```



#### 长度单位

- 像素px
- 百分比%
- em 和 百分比 类似它相当于当前元素的字体大小来计算 
    1em = 1 font0-size
    

#### 字体

- font-family属性 设置字体，可以同时指定多个字体，优先使用前面的字体(使用计算机的字体)
- 字体分类 serif(衬线字体)、sans-serif(非衬线字体)、monospace(等宽字体)、cursive(草书字体)、fantasy(虚幻字体) ——该参数可以用于当全部指定字体本地都没有的时候，用作替补
- font **三个参数** 字体大小/行高(没有就使用默认) "字体"
- text-transform 设置文本的大小写
- text-decoration 设置文本的修饰，例如下划线等等
- letter-spacing 字符之间的间距；word-spacing 设置单词之间的间距
- text-align 设置文本的对齐方式 left、right、center、justify(两端对齐)
- text-indent 设置首行缩进 建议2em(可以用来隐藏文字，这样可以让浏览器搜索到，但是用户看不到)

#### 段落

- 行间距——实际上CSS没有直接设置行间距的方式，我们只能使用**line-height**来设置行高；我们可以设置具体数值（例如100px或1.5）1.5即是字体大小的倍数
  行间距 = 行高 - 字体大小
  ⭐⭐对于单行文本来说，可以将行高设置为和父元素的高度一致，这样当行文本在父元素中垂直居中。

  
  
  

## 整体布局

#### 盒子模型

margin外边距、border边框、内边距padding、元素element（其中height、width都是针对元素而言）

#### 边框border

border-width 边框粗细大小。一个参数：上下左右。两个参数：上下/左右。三个参数：上/左右/下。四个参数：上/下/左/右

border-style 边框线条样式。当需要加上边框时，该属性必须写上。其颜色设置同border-width

border-color 边框颜色。默认黑色。其颜色设置同border-width

border 可以设置边框线条样式、颜色、粗细(不分顺序)【但是不能单独设置各边情况】


#### 内边距padding

内容区与边框之间的距离，可通过padding-top、padding-right、padding-bottom、padding-left设置四个方向的内边距；而且背景会据此延伸


#### 外边距margin

盒子与其他盒子之间的距离。其不会影响可见框的大小，而是会影响到盒子的位置
margin-left和margin-right同时设置为auto时候，则会将两侧的外边距设置为相同的值

⭐关于**垂直外边距**重叠: 
① 在网页**垂直方向**的**相邻**外边距会发生外边距的重叠，即指**兄弟元素**之间的相邻外边距会取得最大值而不是取和
② 如果父子元素的垂直外边距相邻，则子元素的外边距会设置给父元素（可以给元素加border或padding）[最终解决方案](#⭐父子元素影响的布局问题)



#### 内联元素的盒模型

对于**内边距**
内联元素**可以**设置水平方向和垂直方向的**内边距**，且**垂直方向**不会影响页面布局；但是不可以设置width和height

对于**边框**
内联元素可以设置边框，但是**垂直**的边框不会影响到页面的布局

对于**外边距**
支持**水平**方向的外边距，且两个元素之间的外边距是叠加（并不会出现像垂直外边距重叠的现象）

#### 文档流

默认情况下，内容都在html的文档流里，元素在文档流中的特点

**块元素**

1. 块元素在文档流中会独占一行，且自上向下排列
2. 块元素在文档流中**默认宽度**是父元素的100%
3. 块元素在文档流中的**默认高度**被内容/子元素撑开

**内联元素**

1. 在文档流中，只占自身的大小，会默认从左向右排列，若一行中不足以容纳所有的内联元素，则换到下一行继续自左向右
2. 在文档流中，内联元素的宽度和高度默认都被内容撑开



## 一些重要属性

#### display属性和visibility属性

display属性值:
none：元素不会被显示(且**不占位**)
inline：设置为内联元素显示
block：设置为块元素显示
inline-block：行内块元素，含有内联元素和块级元素的特点。可设置宽高又不会独占一行例如\<img>标签

visibility设置为hidden也可以隐藏元素，但是该元素还是会**占位**

#### overflow属性

该属性设置父元素处理溢出的内容，该属性可选值如下：

visible：默认值。溢出的内容可见
hidden：溢出内容会被裁减
scroll：为父元素添加滚动条，通过拖动滚动条来查看完整内容(滚动条始终显示)
auto：根据需求自动添加滚动条



#### 浮动float

浮动可以使元素脱离文档流，当元素脱离文档流以后，他下边的元素会立即向上移动

float可选值：none（默认值，元素默认在文档流排列），left（向页面左侧浮动），right

浮动不会盖住文字，可以通过浮动来设置文字环绕效果

⭐ 内联元素脱离文档流后会变成块元素



#### 由浮动引起的高度塌陷问题

在文档流中，父元素的默认高度是由子元素的撑开的。但是当为子元素设置浮动以后，子元素会完全脱离文档流，这样将无法支撑起父元素的高度，导致父元素的高度塌陷。当父元素的高度塌陷之后，则**父元素往下的元素**都会向上移动，导致布局混乱

**解决：**

1. 将父元素的高度**固定**
2. 设置元素浮动 / 元素绝对定位 / 设置元素为inline-block / 将元素的overflow设置为一个非visible的值(**推荐auto或hidden**)**【推荐】** 开启隐藏的**BFC** (Block Formatting Context) 属性，该属性通常情况默认关闭，但是开启之后元素具有以下属性：
   - 父元素的垂直外边距不会和子元素重叠
   - 开启BFC的元素不会被浮动元素所覆盖
   - 开启BFC的元素可以包含浮动的子元素
3. 当IE浏览器低版本不支持BFC时，可以将zoom属性设置为1(开启hasLayout属性)



#### clear属性解决高度坍塌问题的最终方案

1. 当由于兄弟元素设置浮动导致整体布局产生了影响，clear属性可以用来清楚其他浮动元素对当前元素的影响

   可选值：none（默认值，不清除浮动）, left（清除左侧浮动元素带来的影响）, right（清除右侧浮动元素带来的影响）, both（清除两侧浮动元素带来的影响）

2. 直接在高度坍塌的父元素的最后，添加一个**空白的div**（由于这个div并没有浮动，所以他是可以撑开父元素高度的，然后再设置其clear为both，基本**没有副作用**）——Html结构操作

3. 添加**:after**伪类且按如下设置（原理跟第二点相同，添加一个**空白块元素**） ——CSS操作

   ```css
   .clearfix:after{
       content: "";
       display: block;
       clear: both;
   }
   /*
    *在IE6版本下需要添加如下代码：
    */
   .clearfix{
       zoom: 1;
   }
   ```

   

#### 定位 Position

通过定位position属性可以任意摆放元素，可选值有如下：

###### static

默认值，元素没有开启定位

###### relative

开启相对定位，相对于元素在文本流**原来的位置**进行定位
通过设置position: relative; left/right/top/bottom 四个属性设置偏移量
即相对定位的元素**不会**脱离文档流，也**不会**改变元素的性质(块还是块，内联还是内联)，但是**会**使元素提升一个等级(即覆盖其他元素)

###### absolute

开启绝对定位，相对于**离它最近**的**开启了定位(position不是默认)**的**祖先元素**进行定位，**会**使元素**脱离文档流**，也会**使**元素提升一个等级，且绝对定位**会**改变元素的性质(内联元素变成块元素)

###### fixed

开启固定定位（绝对定位的一种 ），不同的是它相对于**浏览器窗口**进行定位，不会随滚动条滚动，但是 IE6 并不支持



#### z-index 

z-index属性可以用来设置元素的层级，设置一个正整数作为值，值越大越优先显示，当**没有开启定位不能使用z-index**，且父元素的层级再高也不会覆盖子元素

#### opacity

opacity设置元素的透明度，参考值为0-1。且**IE8及以下**需要设置该属性filter: alpha(opacity=a)  0 <= a <= 100

#### 背景

可以同时设置背景颜色和背景图片

```css
      /*
       * 设置背景图片路径
       */
      background-image: url(gaomu.jpg);

      /*
       * 设置背景图片的重复方式
       * repeat, 默认值,背景图片会平铺
       * no-repeat, 不会重复
       * repeat-x, 沿水平方向重复(一行)
       * repeat-y, 沿垂直方向重复(一列)
       */
      background-repeat: repeat-y;
```

**背景位置属性**(background-position)可以调整图片的位置

**背景固定属性**(background-attachment)

属性缩写：直接填写，没有顺序要求

#### 表格Table

表格也是一个块元素，**tr**代表行(其中**th**代表标题)，**td**代表列

补充：在HTML中，当表格非常长的时候，这时候可以将表格分为三个部分：表头 **thead**、表格主体 **tbody**（当年没有添加thead、tobody、tfoot时，默认会把东西全部放在tbody）、表格底部**tfoot** 这些元素是**table的子元素**，**tr的父元素**

```html
<table>
    <tr>
    	<td>A1</td>
        <td>A2</td>
        <td>A3</td>
    </tr>
    <tr></tr>
</table>
```

 

 横向合并单元格，**rowspan** 纵向合并单元格

隔行变色 tr:nth-child(odd){background-color: ...;}

#### 表单Form

必须要有**action**属性，用来指定提交的服务器，**name**属性表示提交内容的名字 
其中input中
type属性 radio，是**单选**选项，name一样的为一组
type属性 checkbox为**多选**选项
\<textarea> 标签为文本域

以下构成下拉列表 且multiple属性设置为multiple，则是展开列表；optgroup属性用于给选项分组

```html
<select>
    <optgroup label="男明星">
        <option>普通的展开列表</option>
    </optgroup>
</select>
```

label标签可以用于指引**相关文字**关联**文本框**(input)，需要**input的id**属性对应**label的for**属性

最后，在表单中可以使用\<fieldset>来为表单项进行分组，其**子元素**\<legend>

#### ⭐父子元素影响的布局问题

[垂直外边距问题](#外边距margin)的解决方法在子元素中加入\<table>兄弟元素

```css
.xxx:bofore{
	content: "";
	display: table;
}
```

最终，解决**高度塌陷**以及**垂直外边距重叠**的方案

```css
.clearfix:brefore,
.clearfix:after{
    content: "";
    display: table;
    clear: both;
}
.clearfix{
    zoom: 1
}
```



#### 框架集

框架集 和 内联框架作用类似，但是框架集可以同时引入多个页面，而内联框架只能引入一个。在H5标准中，推荐使用框架集。

利用\<frameset>创建一个框架集，但是其不能和body出现在同一个页面中，即如果使用框架集则不能使用body标签。rows指定按行排列，cols指定按列排列。例如：

```html
<frameset cols="30%, *, 20%">
    <frame src="..."/>
    <frame src="..."/>
    <frame src="..."/>
</frameset>
```



#### 条件hack 和 属性hack 

由于不同版本的浏览器存在兼容性问题，通过设置hack来来针对性解决