---
title: js常用小组件
date: 2017-01-22 11:56:29  
categories: jquery
tags: 
	- jquery
---

# pc

## scroll滚动到底部加载

```
$(window).scroll(function() {
    if ($(document).scrollTop() + $(window).height() > $(document).height() - 100) {
        $.get(url, function(data) {
            $('#list').append(data);
        });
    }
});
```
<!--more-->
## input–筛选

[input–筛选](http://blog.csdn.net/mrhaoxiaojun/article/details/52512017)

## 根据日期筛选

[根据日期筛选](http://blog.csdn.net/mrhaoxiaojun/article/details/52852971)

## javascript函数节流keyup

[javascript函数节流 keyup](http://blog.csdn.net/mrhaoxiaojun/article/details/52846441)

## 排它区域点击操作它区域

[事件捕获，点击其他body的其他区域，对body特定区域进行操作且排除此区域点击触发](http://blog.csdn.net/mrhaoxiaojun/article/details/52702585)

## 千分位分隔符带小数

[分位分隔符的demo](http://blog.csdn.net/mrhaoxiaojun/article/details/51556855)

## pc直接粘贴到div图片

[pc直接粘贴到div图片](http://blog.csdn.net/mrhaoxiaojun/article/details/51452573)

## 检测当前的浏览器是pc端还是移动端

[检测当前的浏览器是pc端还是移动端](http://blog.csdn.net/mrhaoxiaojun/article/details/50945284)

## Android Or iPhone

[JS判断请求来自Android手机还是iPhone手机，根据不同的手机跳转到不同的链接。](http://blog.csdn.net/mrhaoxiaojun/article/details/50265651)

## 上下数据位移

[上下移动jquery](http://blog.csdn.net/mrhaoxiaojun/article/details/51647681)

## value模拟placeholder

[pc手机&姓名&地址验证&input提示文案兼容ie](http://blog.csdn.net/mrhaoxiaojun/article/details/50947334)

## 非兼容ie，上传图片demo

[非兼容ie，上传图片demo](http://blog.csdn.net/mrhaoxiaojun/article/details/52233193)

## ajaxfileupload，上传

[ajaxfileupload](http://blog.csdn.net/mrhaoxiaojun/article/details/52232142)

## 双击表格td进行编辑，失去焦点完成修改

[双击表格td进行编辑，失去焦点完成修改](http://blog.csdn.net/mrhaoxiaojun/article/details/51243337)

## 获取解析URL地址栏中的参数

[获取解析URL地址栏中的参数](http://blog.csdn.net/mrhaoxiaojun/article/details/50946711)

# m

## 设置描点跳转到指定的位置

```
var hello={};
hello.gotoAnchor= function(options) {
    var anchor = options.el;
    var $body = window.document.documentElement;
    var ua = navigator.userAgent.toLowerCase();
    if (ua.indexOf("webkit") > -1) {
        $body = window.document.body;
    }
    var pos = anchor.offset();
    $body.scrollTop = pos.top - 50;
}
// 调用：
$(".link1").click(function() {
    hello.gotoAnchor({
        el: $('#top1')
    });
})
```