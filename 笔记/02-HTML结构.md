# 02-HTML结构

## 一些关键词

```
HTML （HyperText Markup language）超文本标记语言-结构，目前最流行的网页制作语言，浏览器会解析它呈现出网页结构。
CSS  （Cascading Style Sheets）层叠样式表-修饰，修饰美化HTML中的标签。
JavaScript   (浏览器最基本的脚本语言)-行为，操作DOM，增加交互等等。
```

- 超文本标记语言

1.HTML标记标签通常被称为HTML标签，整个HTML标签对大小写不敏感，建议小写。

2.HTML标签是由尖括号包围的关键词，比如<html>。

3.HTML标签通常是成对出现的，比如<b>和<b/>。

4.标签对中的第一个标签是开始标签，第二个标签是结束标签。

5.开始和结束标签也被称为开放标签和闭合标签。

6.超文本：页面内容可以包含图片、链接、音乐、程序等非文字元素。

\* HTML不是一门编程语言，而是标记语言，标记语言是由一套标记标签组成的，故HTML是通过标记标签来描述网页的。

- 关于HTML的发展
  - HTML1.0 1993.6
  - HTML2.0 1995.11
  - HTML3.2 1997.1
  - HTML4.0 1997.12
  - HTML4.01 1999.12
  - XHTML1.0 2000.1(xml和xhtml的结合)
  - HTML5 2012

------

## HTML结构详解

```html
<!DOCTYPE html>  <!--文档声明-->
<html  lang="en"> <!--HTML 文档主体部分 language="en"语言-英文 浏览器会弹出是否翻译-->
    <head> <!--头部 必须 写一些网页相关的说明、信息等等，不能用来写展示出来的内容-->
        <!--字符编码-->
        <meta charset="UTF-8"> <!--中国常用的编码 UTF-8 GBK GB2312--> 
        <title>01-HTML结构</title> <!--标题 非常重要 关系到SEO-->
        <meta name="keywords" content=""> <!--因为作弊严重，现在浏览器已经不再检索了-->
        <meta name="description" content="这是网页的描述"> <!--描述 吸引用户点击-->
        <meta name="author" content="SeLiNnnn">
        <meta name="generator" content="WebStorm"> <!--开发工具，没什么必要说明-->
    </head>
    <body> <!--身体 必须 网页展示出来的内容-->
        
    </body>
</html>

```



