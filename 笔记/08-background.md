# 一、背景属性

background是一个符合属性，不仅能表示颜色，还能表示图片。

background:color image repeat position/size attachment;

*推荐用复合写法，注意，如果没有position则不能写size，如果position和size都有，必须在position后面写上/区分size。

*注意: background:pink url(''1.jpg"") no-repeat top right fixed;当fixed在复合写法中时，position的百分值是相对于整个显示区窗口的而言的，并不是父级元素。

- background-color
- background-image

   插入背景图片

```html
/* case 1 : 不插入背景图 默认*/
div{background-image: none;}

/* case 2 :　插入背景图*/
div{background-image: url("路径");}
```



- 背景图片平铺方式

  background-repeat

```html
/* case 1 : 背景图片平铺 默认*/
div{background-repeat: repeat;}

/* case 2 :　背景图片不平铺*/
div{background-repeat: no-repeat;}

/* case 3 :　背景图片水平平铺*/
div{background-repeat: repeat-x;}

/* case 4 :　背景图片垂直平铺*/
div{background-repeat: repeat-y;}
```

  

- 背景图片位置

   background-position:(第一个值-水平 第二个值-垂直)left right top bottom center;

```html
/ *case 1 像素 * /
background-position: 50px 50px;
/ *case 2 上右下左中心 * /
background-position: left bottom;
/ *case 3 百分比* /
background-position： 100% 0；
```

*可以在 can i use网站查询样式在浏览器中的兼容性



- 背景图片尺寸

background-size:图片尺寸 css3新属性 IE9以下不支持

```
/ *case 1 填充大小 * /
background-size: 200px 50px;
background-size: 200px;只设置一个值，第二个值按等比例缩放
/ *case 2 完全填满 * /
background-size: cover;宽高比不变，完全填满
/ *case 3 填满某一方向 * /
background-size: contain;保证某一方向完全填满
```



- 背景图片是否滚动

background-attachment :默认滚动

background-attachment:fixed;固定 但图片不会超出父级