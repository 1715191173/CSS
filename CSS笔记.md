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
  ```

  

