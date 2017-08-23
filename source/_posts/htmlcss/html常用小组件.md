---
title: html常用小组件
date: 2017-01-22 10:56:29  
categories: htmlcss
tags: 
	- html
	- css
---

# 常用结构

## 左侧固定，右侧自适应
<!--more-->
NO1.

```
<html>

<head>
    <meta charset="utf-8">
    <title>左侧固定右侧自适应</title>
</head>

<body>
    <style type="text/css">
    html,
    body {
        margin: 0;
        padding: 0;
    }
    
    .all {
        width: 100%;
        height: 100%;
    }
    
    .left {
        width: 200px;
        background: #3f4650;
        position: fixed;
        top: 0;
        left: 0;
        bottom: 0;
    }
    
    .right {
        margin-left: 200px;
        min-width: 980px;
        height: 100%;
        background: #ccc;
        position: relative;
        z-index: 2;
    }
    </style>
    <div class="all">
        <div class="left">我是固定的</div>
        <div class="right">
            <div class="right_in"> 内容</div>
        </div>
    </div>
</body>

</html>
```

NO2.

```
<html>

<head>
    <meta charset="utf-8">
    <title>左侧固定右侧自适应</title>
</head>

<body>
    <style type="text/css">
    html,
    body {
        margin: 0;
        padding: 0;
    }

    .all {
        width: 100%;
        height: 100%;
    }

    .left {
        float: left;
        margin-left: -100%;
        width: 100px;
        height: 100%;
        background: #990;
    }

    .right {
        float: left;
        width: 100%;
        height: 100%;
        background: #F90;
    }

    .right_in {
        margin-left: 100px;
        height: 100%;
    }
    </style>
    <div class="all">
        <div class="right">
            <div class="right_in"> 内容</div>
        </div>
        <div class="left">我是固定的</div>
    </div>
</body>

</html>
```

## 品字布局

```
<html>
<head>
<title>无标题文档</title>
<style type="text/css">
html,body{height:100%; width:100%; overflow:hidden; margin:0; padding:0;}
.a1{width:100%; height:80px; color:#fff; background-color:#369; text-align:center;}
.main{width:100%; height:100%; overflow:hidden; margin:0; padding:0;}
.a2{width:80%; height:100%; color:#fff; background-color:#FF0000; text-align:center;float: left;}
.a3{width:20%; height:100px; color:#fff; background-color:#434343; text-align:center;float: left;}
</style>
</head>
<body>
<div class="a1">div1</div>
<div class="main">
        <div class="a3">div3</div>
        <div class="a2">div2</div>
</div>
</body>
</html>
```

## 图片在DIV中垂直居中的显示方法

```
<html>
<head>
<title>无标题文档</title>
<style type="text/css">
	div{
		width: 600px;
		height: 600px;
		border:1px solid red;
		text-align: center;
	}
	span{
		height: 100%;
		display: inline-block;
		vertical-align: middle;
	}
	img{
		width: 300px;
		height: 300px;
		vertical-align: middle;
	}
</style>
</head>
<body>
<div>
	<span></span>
	<img src="http://fakeimg.pl/300x300/00CED1/FFF/?text=img+placeholder">
</div>
</body>
</html>
```

## 上传图片(本地)

html

```
<div class="task-upimg">
    <a class="text">+添加图片</a>
    <img class="upimg" src="http://css88.b0.upaiyun.com/css88/2016/10/es6-core-features-overview-large.png" >
    <input type="file" class="task-up-input" id="task-up-input" name="task-up-input" value="">
</div>1234512345
```

css

```
.task-upimg {
    width: 172px;
    height: 135px;
    line-height: 135px;
    background: #fff;
    border: 1px solid #ccc;
    border-radius: 2px;
    text-align: center;
    position: relative;
    float: left;
    .text {
        cursor: pointer;
        text-decoration: underline;
        color: #009DF8;
        font-size: 18px;
    }
    .upimg {
        cursor: pointer;
        width: 100%;
        height: 100%;
        display: none;
        position: absolute;
        top: 0;
        left: 0;
    }
    .task-up-input {
        position: absolute;
        left: 0;
        width: 100%;
        top: 0;
        height: 100%;
        opacity: 0;
        filter: alpha(opacity=0);
        font-size: 500px;
        cursor: pointer;
        overflow: hidden;
    }
}
```

## css radio自定义

```
input[type="radio"] {  
    float: left;  
    -webkit-appearance: none;  
    -moz-appearance: none;  
    appearance: none;  
    width: 44px;  
    height: 44px;  
    cursor: pointer;  
    vertical-align: middle;  
    background: url(../img/check.png) no-repeat;  
    background-size: 100%;  
    -webkit-border-radius: 1px;  
    -moz-border-radius: 1px;  
    border-radius: 50%;  
    -webkit-box-sizing: border-box;  
    -moz-box-sizing: border-box;  
    box-sizing: border-box;  
    position: relative;  
    // margin-top: 2px  
}  
  
input[type=radio]:active {  
    border-color: green;  
    background: #ebebeb  
}  
  
input[type=radio]:hover {  
    border-color: #c6c6c6;  
    -webkit-box-shadow: inset 0 2px 2px rgba(0, 0, 0, 0.1);  
    -moz-box-shadow: inset 0 2px 2px rgba(0, 0, 0, 0.1);  
    box-shadow: inset 0 2px 2px rgba(0, 0, 0, 0.1)  
}  
  
input[type=radio]:checked {  
    background: #fff  
}  
  
input[type=radio]:checked::after {  
    content: "";  
    background: url(../img/active.png);  
    width: 44px;  
    height: 44px;  
    background-size: 100%;  
    display: block;  
    position: absolute;  
    top: -1px;  
    right: 0px;  
    left: -1px;  
    margin-left: 2px  
}  
  
input[type=radio]:focus {  
    outline: none;  
    border-color: green  
}
```

## star 评价

```
<!DOCTYPE html>  
<html lang="en">  
  
<head>  
    <meta charset="UTF-8">  
    <title>评价</title>  
    <style>  
    .score-public {  
        width: 210px;  
        position: relative;  
        height: 30px;  
        display: inline-block;  
        vertical-align: middle;  
    }  
      
    .star,  
    .star-gray {  
        position: absolute;  
        left: 0;  
        right: 0;  
        top: 0;  
        bottom: 0;  
        width: 100%;  
        height: 100%;  
        display: block;  
         background: url(./star-all-gray.png) no-repeat;  
    }  
      
    .star {  
        z-index: 2;  
        background: url(./star-all.png) no-repeat;  
        background-size: auto 100%;  
    }  
      
    .star-gray {  
        background-size: auto 100%;  
    }  
    </style>  
</head>  
  
<body>  
    <span class="score-public score ">  
                <span class="star" style="width:50%"></span>  
                <span class="star-gray"></span>  
    </span>  
</body>  
  
</html>
```

## 空心三角实现

```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
    #demo {
        position: relative;
    }
    /*小三角*/

    #demo:after {
        border: solid transparent;
        border-top-color: #fff;
        border-left-width: 3px;
        border-right-width: 3px;
        border-bottom-width: 5px;
        border-top-width: 5px;
        content: " ";
        position: absolute;
        top: 18px;
    }
    /*大三角*/

    #demo:before {
        border: solid transparent;
        border-top-color: #000;
        border-left-width: 5px;
        border-right-width: 5px;
        border-bottom-width: 7px;
        border-top-width: 7px;
        content: " ";
        position: absolute;
        left: -2px;
        top: 18px;
    }
    </style>
</head>
<body>
    <div id="demo">
    </div>
</body>
</html>
```

## 多个div自动等高（不设高度）

```
<html>

<head>
    <title>无标题文档</title>
    <style type="text/css">
    * {
        margin: 0;
        padding: 0;
    }
    
    #wrap {
        /*// (这行代码是重点，否则你会看到页面很长很长)*/
        overflow: hidden;
        padding: 0;
        padding-left: 180px;
        /*（内补丁）*/
    }
    
    #left,
    #right {
        height: auto;
        /*（外补丁）*/
        margin-bottom: -10000px;
        /*（内补丁）*/
        padding-bottom: 10000px;
    }
    
    #left {
        display: inline;
        float: left;
        width: 180px;
        /*（外补丁）*/
        margin-left: -180px;
        background: #0CF;
    }
    
    #right {
        float: right;
        width: 100%;
        background: #FC6;
    }
    </style>
</head>

<body>
    <div id="wrap">
        <div id="left">11111
            <br>111
            <br>11111
            <br>1111111
            <br>
            <br>
        </div>
        <div id="right">dasdasd</div>
    </div>
</body>

</html>
```

## footer粘连

[粘连 Footer 的 5 种方法 | CSS-Tricks](http://blog.csdn.net/mrhaoxiaojun/article/details/51781384)