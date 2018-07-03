# 一、overflow超出隐藏

- 盒模型的超出隐藏

  | 值             | 描述                                                     |
  | -------------- | -------------------------------------------------------- |
  | <u>visible</u> | 默认值。内容不会被修剪，会呈现在元素框之外。             |
  | <u>hidden</u>  | 超出部分隐藏。                                           |
  | scroll         | 内容不会超出盒子，但是始终会显示滚动条。                 |
  | <u>auto</u>    | 只有当内容超出盒子时，才显示滚动条，不超出则没有滚动条。 |
  | inherit        | 继承父级overflow属性的值。                               |

  ​	超出隐藏可以分解为水平方向和垂直方向的分解属性：overflow-x  overflow-y。即水平与垂直方向超出隐藏。

# 二、样式初始化

```html
body, dl, dd, p, h1, h2, h3, h4, h5, h6 {
    margin: 0;
}

ol, ul, li {
    margin: 0;
    padding: 0;
    list-style: none;
}

img {
    border: none;
}
```

# 三、块级元素与行内元素

- 块级元素：

  *独占一行

  *常见的块级元素：div h1-h6 p ol ul li dl dd dt

  *默认支持宽高。如果没有给宽度，则块级元素宽度默认是父级的100%。

  *默认支持上下边距


- 行内元素：

  *不会独占一行

  *常见的行内元素：span a b i strong em img

  *默认不支持宽高

  *默认不支持上下边距

  *行内元素里不要写块级元素。

- 行内元素与块级元素之间的互相转换 display

  display:block;  变成块级元素

  display:inilne;  变成行内元素

  display:inline-block;  行内块元素(允许水平布局，同时支持宽高和上下margin)

  display:none;  隐藏

![](G:\WEB前端系统班\HTML精英实验班课堂操作&作业\笔记\pic\1.png)

```html
<style>
	 b{
            display: inline-block;
            width: 150px;
            height: 30px;
            background: pink;
            margin-top: 15px;
       }
</style>
<body>
	<b>我是第一个b标签</b><b>我是第二个b标签</b>
	<b>我是第三个b标签</b>
</body>
```

*注意：使用display:inline-block时，标签之间会有空格，且空格的大小是字体大小决定的。在布局的时候不要用空格去产生盒子之间的间隙，而是用margin。如果一定要取消空格，则讲标签写在一行。

# 四、选择器

- 两种命名方式

  id

  ​	*唯一，一个标签只有一个id名，其他标签不能再用这个id

  class

  ​	*不唯一，一个标签可以有多个class，其他标签也可以使用相同的class

  ​	*一个标签有多个class名，在类名之间用空格分开。<div class="nav first"></div>


- 命名规则：(严格区分大小写)

  字母 数字 - _

  *见名知意

  *不能以数字和-开头

  *不推荐使用中文

  *腾讯开发规定：只能用小写，不允许使用下划线和驼峰。

```html
<body>
    <!--header start-->
    <div id="header"></div>

    <!--content start-->
    <div id="content"></div>

    <!--footer start-->
    <div id="footer"></div>
</body>	
```



## 选择器初级写法

| 写法        | 名称         | 举例                        |
| ----------- | ------------ | --------------------------- |
| *           | 通配符选择器 | *{margin:0;}                |
| 标签名      | 元素选择器   | div{width:50px;}            |
| .class名    | class选择器  | .nav{width:20px;}           |
| #id名       | id选择器     | #header{width:50px;}        |
| 父 子 孙... | 后代选择器   | #header div p{margin:10px;} |



选择器的优先级：

​	!important > 内联样式 > id > class > 标签

找出id选择的个数 class选择的个数 标签选择的个数

相同的时候，以后面的为准

```html
<style>
    #main .hh{
    	color: greenyellow;
    }
    p#gg.hh{
        color: red;
    }
    span{
            color: #666 !important;
        }
</style>
<body id="main">
    <p id="gg" class="hh" style="color: blueviolet;">恍恍惚惚</p>
    <span id="gg" class="hh" style="color: blueviolet;">恍恍惚惚</span>
</body>
```

