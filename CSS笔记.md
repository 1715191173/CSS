# CSS笔记

- **块元素 和 内联元素**

  块元素：\<div> \<p> \<h1> \<h2>
  特点：会独占一整行，无论他的内容有多少

  内联元素：
  \<span> span标签专门用来选中文字
  \<img> \<iframe> \<a>
  特点：只占自身大小的元素，不会占用一行

  **注意：** 块元素主要用来做页面中的布局，内联元素主要用来选中文本 设置样式

  一般情况下只是用**块元素**包含**内联元素**，而不会使用**内联元素**包含**块元素**



- **选择器**

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

  

- **伪类选择器**

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

  

- **伪元素**

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
  
  
  
- **兄弟元素选择器**

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

  
  
- **优先级规则**

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

- **文本标签**

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

  

- **列表**

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

    

- **长度单位**

    - 像素px
    - 百分比%
    - em 和 百分比 类似它相当于当前元素的字体大小来计算 
        1em = 1 font0-size

- **字体**

  - font-family属性 设置字体，可以同时指定多个字体，优先使用前面的字体(使用计算机的字体)
  - 字体分类 serif(衬线字体)、sans-serif(非衬线字体)、monospace(等宽字体)、cursive(草书字体)、fantasy(虚幻字体) ——该参数可以用于当全部指定字体本地都没有的时候，用作替补
  - font **三个参数** 字体大小/行高(没有就使用默认) "字体"
  - text-transform 设置文本的大小写
  - text-decoration 设置文本的修饰，例如下划线等等
  - letter-spacing 字符之间的间距；word-spacing 设置单词之间的间距
  - text-align 设置文本的对齐方式 left、right、center、justify(两端对齐)
  - text-indnet 设置首行缩进 建议2em

- **段落**

  - 行间距——实际上CSS没有直接设置行间距的方式，我们只能使用**line-height**来设置行高；我们可以设置具体数值（例如100px或1.5）1.5即是字体大小的倍数
    行间距 = 行高 - 字体大小
    ⭐对于单行文本来说，可以将行高设置为和父元素的高度一致，这样当行文本在父元素中垂直居中。

    



