---
title: node.js Express 框架入门
date: 2017-01-22 14:56:29  
categories: node
tags: 
	- node
	- express
---

### 全栈工程师

掌握多种技能，能利用各种技术独立完成项目或产品的人
<!--more-->
> 前端开发

html css javascript jquery 特效 前端优化 前后端联合优化 各种自动化框架与工具

> 后端开发

linux node.js java restful服务 api的服务 实现中间层 常用框架 async mysql promise blurbird

> 移动端开发

vue ionic angular react react native phonegap 微信

> 数据库

mysql redis memcached mongodb

> 全栈优势

技能全
学习能力强
沟通成本低

### node.js的包管理系统已经成为世界上最大的开源库生态系统

地址：[https://www.npmjs.com/](https://www.npmjs.com/)

简单的说 Node.js 就是运行在服务端的 JavaScript,打破了前后端的语言边界，解放了前端程序员的职责约束，可以在更大的舞台上施展空间。

- Node.js 是一个基于Chrome JavaScript 运行时建立的一个平台，是一个Javascript的运行环境。
- Node.js是一个事件驱动I/O服务端JavaScript环境，基于Google的V8引擎，V8引擎执行Javascript的速度非常快，性能非常好。
- Node.js不但可以解析JS代码，也没有所谓的兼容性问题，更没有浏览器的安全限制。还增加了许多系统API如文件读写，进程管理，网络服务等。

#### 功能越来越强大

其它语言能做的node都能做，在有A 些场景下会做的更好

- 项目管理：npm,grunt, gulp,bower, yeoman
- 桌面应用: node-webkit
- Web开发：express,ejs,hexo, socket.io, restify, cleaver, stylus, browserify,cheerio
- 工具包 underscore,moment,connet,later,log4js,passport,passport(oAuth),domain,require,reap,commander,retry,PDFkit
- 数据库：mysql,mongoose,redis,memcached
- 异步：async,wind,eventProxy,bluebird
- 部署：forever,pm2,nodemon
- 测试：jasmine,karma,protractor
- 跨平台：rio,tty
- 内核：cluster,http,request
- 模板: jade
- 博客: ghost,hexo
- 微信: weui
- 硬件控制: NoduinoWeb
- 操作系统: NodeOS

#### 资源

- [node官网](https://nodejs.org/en/)
  可以看版本的变化，API的变化，新特性的加入
- [npm官网](https://www.npmjs.com/)
  可以搜索需要的模块，以及模块的使用说明
- [github](https://www.github.com/)
  可以查找优秀的项目源码
- [stackoverflow](https://www.stackoverflow.com/)
  如果遇到解决不了的问题可以在此提问

## 抛出Node.js(贴代码)

### Node.js 安装配置

1.打开官网主页
首页会推荐你合适的版本
[https://nodejs.org/en/](https://nodejs.org/en/)

2.如果推荐的版本不合适可以进入下载页面
[https://nodejs.org/en/download/](https://nodejs.org/en/download/)

3.下载完成后，一通下一步搞定 打开命令窗口 node -v看版本号 ，不截图，各位老司机都懂

（npm list -g –depth 0 查看全局的安装包）

### 启动一个服务（例）

```
 require('http').createServer(function(req,res){
    res.end('hello world');
}).listen(8080,'localhost',function(){
    console.log('服务已启动');
});
```

### 开个店铺（例）

```
//一个开店指南
var http = require('http');//需要一个模块，加载 一个模块
var url = require('url');
/**
 *
 * @param request 请求对象
 * @param response 响应对象
 */
var menus = [{name:'豆豉烤鱼',unit:'条'},{name:'东坡肘子',unit:'只'},{name:'水煮牛肉',unit:'盘'},{name:'米饭',unit:'碗'},{name:'汇源果汁',unit:'瓶'}];
var makeMenu = function(){
    var str = '<ul>';
    menus.forEach(function(menu){
        str+=('<li><a href="/'+menu.name+'?unit='+menu.unit+'">'+menu.name+'</a></li>');
    })
    str+= '</ul>';
    return str;
}

var person = function(request,response){
    var urlObj = url.parse(decodeURIComponent(request.url),true);//true表示把查询字符串转成对象
    console.log(urlObj);
    response.setHeader('Content-Type','text/html;charset=utf-8');
    if(urlObj.pathname == '/'){
        response.end(makeMenu());
    }else{
        response.end('客官，一'+urlObj.query.unit+urlObj.pathname.slice(1)+"<a href='/'>back</a>");
    }
}
//装修一个自己的分店
var server = http.createServer(person);
//开店营业，告诉别人自己的IP和端口
server.listen(8080,'localhost',function(){
    console.log('服务已启动');
});


/**
 search: '?unit=ping', 查询字符串
 query: 'unit=ping&age=5', 查询字符串去掉问号
 pathname: '/huiyuan',路径名
 path: '/huiyuan?unit=ping',
 **/
```

## Node.js Express 框架

[Express官网](http://expressjs.com/)

[Express4.x API](http://expressjs.com/zh-cn/4x/api.html)

### Express 简介

Express 是一个简洁而灵活的 node.js Web应用框架, 提供了一系列强大特性帮助你创建各种 Web 应用，和丰富的 HTTP 工具。

使用 Express 可以快速地搭建一个完整功能的网站。

Express 框架核心特性：

- 可以设置中间件来响应 HTTP 请求。
- 定义了路由表用于执行不同的 HTTP 请求动作。
- 可以通过向模板传递参数来动态渲染 HTML 页面。

### 安装 Express

```
npm install express
```

以上命令会将 Express 框架安装在当期目录的 **node_modules** 目录中， **node_modules** 目录下会自动创建 express 目录。以下几个重要的模块是需要与 express 框架一起安装的：

- **body-parser** - node.js 中间件，用于处理 JSON, Raw, Text 和 URL 编码的数据。
- **cookie-parser** - 这就是一个解析Cookie的工具。通过req.cookies可以取到传过来的cookie，并把它们转成对象。
- **multer** - node.js 中间件，用于处理 enctype=”multipart/form-data”（设置表单的MIME编码）的表单数据。

### 第一个 Express 框架实例

```
var express = require('express');
var app = express();
app.get('/',function(req,res){
    res.end('Hello World');
});
app.get('/reg',function(req,res){
    res.end('注册');
});
app.get('/login',function(req,res){
    res.end('登陆');
});
var http = require('http');
var server = http.createServer(app);
server.listen(8080, function () {
  console.log("start...")
});
```

### 请求和响应(API)

**request** 和 **response** 对象的具体介绍：

**Request 对象** - request 对象表示 HTTP 请求，包含了请求查询字符串，参数，内容，HTTP 头部等属性。常见属性有：

1. req.app：当callback为外部文件时，用req.app访问express的实例
2. req.baseUrl：获取路由当前安装的URL路径
3. req.body / req.cookies：获得「请求主体」/ Cookies
4. req.fresh / req.stale：判断请求是否还「新鲜」
5. req.hostname / req.ip：获取主机名和IP地址
6. req.originalUrl：获取原始请求URL
7. req.params：获取路由的parameters
8. req.path：获取请求路径
9. req.protocol：获取协议类型
10. req.query：获取URL的查询参数串
11. req.route：获取当前匹配的路由
12. req.subdomains：获取子域名
13. req.accpets（）：检查请求的Accept头的请求类型
14. req.acceptsCharsets / req.acceptsEncodings / req.acceptsLanguages
15. req.get（）：获取指定的HTTP请求头
16. req.is（）：判断请求头Content-Type的MIME类型

**Response 对象** - response 对象表示 HTTP 响应，即在接收到请求时向客户端发送的 HTTP 响应数据。常见属性有：

1. res.app：同req.app一样
2. res.append（）：追加指定HTTP头
3. res.set（）在res.append（）后将重置之前设置的头
4. res.cookie（name，value [，option]）：设置Cookie
5. opition: domain / expires / httpOnly / maxAge / path / secure / signed
6. res.clearCookie（）：清除Cookie
7. res.download（）：传送指定路径的文件
8. res.get（）：返回指定的HTTP头
9. res.json（）：传送JSON响应
10. res.jsonp（）：传送JSONP响应
11. res.location（）：只设置响应的Location HTTP头，不设置状态码或者close response
12. res.redirect（）：设置响应的Location HTTP头，并且设置状态码302
13. res.send（）：传送HTTP响应
14. res.sendFile（path [，options][，fn]）：传送指定路径的文件 -会自动根据文件extension设定Content-Type
15. res.set（）：设置HTTP头，传入object可以一次设置多个头
16. res.status（）：设置HTTP状态码
17. res.type（）：设置Content-Type的MIME类型

### 路由配置

express 封装了多种 http 请求方式，主要只使用 get 和 post 两种，即 app.get() 和 app.post() 。 app.get() 和 app.post() 的第一个参数都为请求的路径，第二个参数为处理请求的回调函数，回调函数有两个参数分别是 req 和 res，代表请求信息和响应信息 。路径请求及对应的获取路径有以下几种形式：

#### POST实例

演示了在表单中通过 POST 方法提交两个参数

post.html 文件代码如下：

```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <link rel="stylesheet" href="css/post.css">
</head>

<body>
    <form action="http://127.0.0.1:8080/process_post" method="POST">
        <span>user：</span><input type="text" name="first_name">
        <br> 
        <br> 
        <br> 	
        <span>psd：</span><input type="password" name="last_name">
        <br> 
        <br> 
        <input type="submit" value="Submit" class="sub-btn">
    </form>
</body>

</html>
```

post-server.js 文件代码修改如下:

```
var express = require('express');
var app = express();
var bodyParser = require('body-parser');

// 创建 application/x-www-form-urlencoded 编码解析
var urlencodedParser = bodyParser.urlencoded({ extended: false })

// Express 提供了内置的中间件 express.static 来设置静态文件如：图片， CSS, JavaScript 等。
// 你可以使用 express.static 中间件来设置静态文件路径。例如，如果你将图片， CSS, JavaScript 文件放在 public 目录下，你可以这么写：
app.use(express.static('public'));

app.get('/post.html', function (req, res) {
   res.sendFile( __dirname + "/" + "post.html" );
})

app.post('/process_post', urlencodedParser, function (req, res) {
	console.log(req.body)
   // 输出 JSON 格式
   response = {
       user:req.body.first_name,
       pwd:req.body.last_name
   };
   console.log(response);
   res.end(JSON.stringify(response));
})

var server = app.listen(8080, function () {
  console.log("start...")
})
```

### 中间件

中间件是处理HTTP请求的通用函数,用来完特定的任务

```
var express = require('express');
/**
 * 中间件是处理HTTP请求的通用函数,用来完特定的任务
 * 检查用户登陆，分析数据
 * 一个中间件处理完成，才能处理下一个中间件
 * next调用下一个中间件或路由函数
 */
var app = express();

app.use(function(req,res,next){
    res.setHeader('Content-Type','text/html;charset=utf-8');
    next();//每个中间有中止请求的权利，不调next
});

app.use(function(req,res,next){
    //用户是否登陆
    var islogin = true;//假设用户已经登陆
    var url = req.url;
    if('/post' == url){
        return next();
    }
    if('/reg' == url || '/login' == url){
        return res.end('你已经登陆了，不要再访问这个页面了');
    }
    next();

});
app.get('/',function(req,res){
    res.end('/');
});
app.get('/reg',function(req,res){
    res.end('注册');
});
app.get('/login',function(req,res){
    res.end('登陆');
});
app.all('/post',function(req,res){
    res.end('发表文章');
});
app.all('*',function(req,res){
    res.end('你想的页面走丢了');
});
app.listen(8080, function () {
  console.log("start...")
});
```

### 参数接收

```
var express = require('express');
/**
 * 如何接收参数，如何发响应
 */
var app = express();
//静态文件
// app.use(express.static(__dirname));
// app.use(function(req,res,next){
//    console.log(req.host,req.path);
//     next();
// });
app.get('/reg',function(req,res){
   // res.end(JSON.stringify(req.query));
    //向客户端发送响应，并智能处理不同的类型的数据
    res.send(req.query);
});
//取路径参数
app.get('/login/:username/:password',function(req,res){
    // res.end(JSON.stringify(req.query));
    console.log(req.params)
    res.send(req.params.password);
});

app.listen(8080, function () {
  console.log("start...")
});
```

## express-generator生成器

### 使用express生成器生成一个示例项目

1.全局安装生成器命令

```
npm install -g express-generator
```

2.在自定的目录下生成一个项目 执行次命令

```
express -e
```

3.安装package.json里配置的依赖包

```
npm install
```

4.over，并启动服务器

```
npm start
```

### 生成文件说明

**app.js**：express的主配置文件
**package.json**：存储着工程的信息及模块依赖，当在 dependencies 中添加依赖的模块时，运行 `npm install`，npm 会检查当前目录下的 package.json，并自动安装所有指定的模块
**node_modules**：存放 package.json 中安装的模块，当你在 package.json 添加依赖的模块并安装后，存放在这个文件夹下
**public**：存放 image、css、js 等文件
**routes**：存放路由文件
**views**：存放视图文件或者说模版文件
**bin**：可执行文件，可以从此启动服务器

### 小解入口文件app.js

```
var express = require('express');
var path = require('path');
var favicon = require('serve-favicon');
var logger = require('morgan');
var cookieParser = require('cookie-parser');
var bodyParser = require('body-parser');

var index = require('./routes/index');
var users = require('./routes/users');
var ejs = require('ejs');
// var app = express();

// view engine setup
app.set('views', path.join(__dirname, 'views'));
// app.engine('.html', ejs.__express);
// app.set('view engine', 'html');
app.set('view engine', 'ejs');

// uncomment after placing your favicon in /public
//app.use(favicon(path.join(__dirname, 'public', 'favicon.ico')));
app.use(logger('dev'));
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: false }));
app.use(cookieParser());
app.use(express.static(path.join(__dirname, 'public')));

app.use('/', index);
app.use('/users', users);

// catch 404 and forward to error handler
app.use(function(req, res, next) {
  var err = new Error('Not Found');
  err.status = 404;
  next(err);
});

// error handler
app.use(function(err, req, res, next) {
  // set locals, only providing error in development
  res.locals.message = err.message;
  res.locals.error = req.app.get('env') === 'development' ? err : {};

  // render the error page
  res.status(err.status || 500);
  res.render('error');
});

module.exports = app;
```

$$

$$

#### 修改：app.js

如果想把模板后缀改成“.html”时就会用到app.engine方法，来重新设置模板文件的扩展名，比如想用ejs模板引擎来处理“.html”后缀的文件

```
app.set('view engine', 'ejs');
//替换上面代码为下面代码
app.engine('.html', ejs.__express);
app.set('view engine', 'html');
在前面追加，var ejs = require('ejs');
```

了解app.engine()方法之前先看看express应用的安装命令:“express -e ”，其中的 -e 和 -J 表示ejs和jade模板。
app.engine(ext, callback) 注册模板引擎的 callback 用来处理ext扩展名的文件。
PS：__express不用去care，其实就是ejs模块的一个公共属性，表示要渲染的文件扩展名。

> require() 用于在当前模块中加载和使用其他模块；此方法是模块的基础，使用中大概有路径的概念就行。PS：JS文件可以去掉”.js”后缀
>
> exports 表示模块的导出对象，用于导出模块的属性和公共方法。在项目routes文件夹下有index.js和users.js，都使用到exports对象导出对象。PS：一个模块的代码只会在模块第一次被使用时执行，不会因require多次而被初始化多次。
>
> app.set(name, value)和app.get(name)就是你想的那样，set()为设置 name 的值设为 value，get()为获取设置项
>
> app.use([path], function) 使用中间件 function,可选参数path默认为”/“。使用 app.use() “定义的”中间件的顺序非常重要，它们将会顺序执行，use的先后顺序决定了中间件的优先级(经常有搞错顺序的时候);