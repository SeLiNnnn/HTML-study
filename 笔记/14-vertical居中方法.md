# 一、vertical垂直对齐方法

```html
/case 1 为什么不用inline-block/
div {
    display: inline-block;
    width: 150px;
    height: 150px;
    border: 5px solid pink;
}
.first {
    margin-top: 20px;
}
...
<div class="first"></div>
<div></div>
<div></div>
<div></div>
```

![](G:\WEB前端系统班\HTML精英实验班课堂操作&作业\笔记\pic\22.png)

注：只给第一个div加margin-top但整体都下移了。因为使用inline-block后所有盒子都是关于基线对齐。

```html
/case 2 文字受基线的影响/
div {
    display: inline-block;
    width: 150px;
    height: 150px;
    border: 5px solid pink;
}
...
    <div>123</div>
    <div></div>
    <div></div>
    <div></div>
/case 3 如果盒子里都有文字/
	<div>123</div>
    <div>1234</div>
    <div>234</div>
    <div>2345</div>
```

![](G:\WEB前端系统班\HTML精英实验班课堂操作&作业\笔记\pic\23.png)

注：添加文字后，文字也和基线对齐，导致盒子下移。

![](G:\WEB前端系统班\HTML精英实验班课堂操作&作业\笔记\pic\24.png)

注：都有文字后，盒子又都对齐了。



## vertical垂直对齐方式

定义**==行内元素==**的基线相对于该元素所在行的基线的垂直对齐。inline inline-block元素才具备此属性。（img标签属于inline-block）一般用于处理文字与图片之间的对齐方式。

> - top 元素的顶端与行中最高元素的顶端对齐
> - middle 此元素放置在父元素的中部。(小写x的中部)
> - bottom 元素的顶端与行中最低的元素的顶端对齐。



以上值与`line-height`相关的

> - text-top 元素的顶端与父元素字体的顶端对齐
> - text-bottom 把元素的底端与父元素字体的底端对齐。
> - baseline 默认。元素放置在父元素的基线上。比底端对齐的基线稍微偏上一点。

=>加vertical-align的同排元素都要vertical-align； 
=>vertical-align可以解决img下方间隙问题；

```html
/*case 1 垂直居中的方式 适用于允许修改成block布局的元素*/
#wrap{
    width: 800px;
    height: 500px;
    border: 5px solid pink;
    margin: 50px auto;
    text-align: center;/*当p变成inline-block后给父级设定text-align使其水平居中*/
    line-height: 500px;/*使基线垂直居中*/
}
#wrap p{
    display: inline-block;
    vertical-align: middle;/*加上vertical-align后才是真正的使基线居中*/
    width: 100px;
    height: 100px;
    background: red;
}
...
<div id="wrap">
        <p></p>
</div>
```

垂直居中步骤总结：

​	1.给需要垂直居中的元素inline-block;

​	2.给其父元素inline-height和text-align;

​	3.给需要居中的元素vertical-align;

```html
/*case 2 使用定位来实现水平垂直居中 适用于所有元素*/
#wrap{
    position: relative;
    width: 800px;
    height: 500px;
    border: 5px solid pink;
    margin: 50px auto;
}
#wrap p{
    position: absolute;/*浮动定位只要脱离文档流默认把元素变成块级*/
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;/*四个值全部写上且为0，再加上margin:auto即可 间距是margin分配的而不是定位*/
    width: 100px;
    height: 100px;
    background: red;
    margin: auto;
}
...
<div id="wrap">
	<p></p>
</div>
```

```html
/*case 3  适用于在明确知道自身宽高情况下的居中*/
#wrap{
    position: relative;
    width: 800px;
    height: 500px;
    border: 5px solid pink;
    margin: 50px auto;
}
#wrap p{
    position: absolute;
    top: 50%;/*父级高度的50%*/
    left: 50%;
    width: 200px;
    height: 200px;
    background: red;
    margin-top: -100px;/*回去自己高度的一半*/
    margin-left: -100px;/*回去自己高度的一半*/
    /*margin-top: -50%;!*不管是marign还是padding写百分比的时候都是父级宽度的百分值*!*/
}
...
<div id="wrap">
	<p></p>
</div>
```

```html
/*case 4  适用于所有情况，但不兼容低版本IE*/
#wrap{
    position: relative;
    width: 800px;
    height: 500px;
    border: 5px solid pink;
    margin: 50px auto;
}
#wrap p{
    /*使用于所有情况*/
    position: absolute;
    top: 50%;/*参照父级高度的50%*/
    left: 50%;/*参照父级宽度的50%*/
    width: 200px;
    height: 200px;
    background: red;
    transform: translate(-50%,-50%);/*百分比参照于自身*/
}
...
<div id="wrap">
	<p></p>
</div>
```



## 二、cursor指针样式

1、cursor 指针样式 （规定要鼠标进入元素内容区域要显示的光标的类型）

> - default 箭头（通常是一个箭头）
> - auto 默认。浏览器设置的光标
> - pointer 光标呈现为指示链接的指针（一只手）
> - crosshair 十字光标
> - move 此光标指示某对象可被移动
> - text 光标指示文本
> - wait 光标指示正忙（通常是一只表或沙漏）
> - help 光标指示帮助（通常是一个问号或一个气球）

参考资料：<http://www.w3school.com.cn/cssref/pr_class_cursor.asp>

2、自定义指针样式

```html
cursor:url('hand.cur'),pointer;
/*自定义光标样式 需要一个光标图形文件，后缀最好是 .cur .ico*/
/*必须在路径后加上备用指针样式才能显示，如pointer,move等*/
```

# 三、选择器及样式优先级

## 一、选择器优先级

> `*`{} 
> `tagName`{} 
> `.class`{} 
> `#id`{}

总结 `*` < `tagName` < `class` < `id`

------

## 二、选择器特殊情况

1、级别相同的选择器：后写的样式会覆盖前面的；(后来居高)

> .wrap{background:red;} 
> .wrap{background:green;}

2、 复杂后代选择器

> 1）比高低顺序依次是: ID选择器 class选择器 tagName{} ， 
> 2）ID选择器个数不相等，ID个数多的优先级高，后面不用比 
> 2）ID选择器个数相等，则看class个数多的优先级高，后面不用比 
> 3）class 个数相等 ，再看tagName 个数 
> 4）#wrap ul li .list{} 和.wrap ul li #list{}优先级一样（不分先后）

3、 选择器使用原则：准确的选中元素，并且不影响其他元素

## 三、样式的多种形式

一 `行间`样式 —-内部样式

```
1.<div style=''></div>
```

二 `内嵌`（css）样式 —-内部样式

```
1.<style>

2.        #box{}

3.    </style>
```

三 `外链` ( css )样式 —–外部样式

```
1.<link rel='stylesheet' type='text/css' href='url.css'/>
```

> =>注意：需要 设置编码 `@charset 'UTF-8'`; 外链中注意 background-image 路径变化

------

## 四、样式优先级

样式优先级排序：

> 外链css样式 < （内嵌css）样式 < 行间样式

!important 提升优先级（最高） 例如：font-size:12px !important;



## 五、CSS属性书写顺序

建议遵循：布局定位属性 自身属性 文本属性 其他属性 CSS3属性

```html
/*以下只是常用属性，并不是全部*/
/*布局定位属性*/
display / list-style / position (相应的 top,right,bottom,left) /float / clear / visibility / overflow
/*自身属性*/后写自身属性是为了提高渲染效率，防止代码回流。
width / height / margin / padding / border / background
/*文本属性*/
color / font / text-decoration / text-align / vertical-align / white-space / break-word
/*其他CSS3*/
content / cursor / border-radius / box-shadow / text-shadow / background:linear-gradient
```

