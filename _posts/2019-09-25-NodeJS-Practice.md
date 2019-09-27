---
title: "NodeJS-聊天室练习"
subtitle: 'NodeJS-聊天室练习'
author: "Kevin"
header-style: text
tags:
  - NodeJS
---



`/Users/darkalex001/workspace/node/NodeJsTutorial/HttpForm`



进入 `nodejs.org`

`https://nodejs.org/en/about/`

`vi app.js`

```javascript
var http = require('http');
http.createServer(function (req,res){
    res.writeHead(200,{'Content-Type':'text/plain'});
    res.write("<h1>this is a test page!</h1>");
    res.end("Hello World\n");
}).listen(1337,'127.0.0.1');
console.log('Server running at http://127.0.0.1:1337');
```

`node app.js`

```
Server running at http://127.0.0.1:1337
```

`text/plain` **➜** 发送过去接收到的是文本快，里面含有html标签

`text/html` ➜ 发送过去的是HTML标签，里面已经被解析了

```
this is a test page!
Hello World
```

这样子我们做后端网站就很容易了，数据是由服务器端生成的叫做后端网站

```javascript
var http = require('http');
http.createServer(function (req,res){
    res.writeHead(200,{'Content-Type':'text/html'});
    res.write("<h1>this is a test page!</h1>");
    for(var i=0;i<10;i++){
        res.write("<p>hehe</p>");
    }
    res.end("Hello World\n");
}).listen(1337,'127.0.0.1');
console.log('Server running at http://127.0.0.1:1337');
```

```
this is a test page!
hehe

hehe

hehe

hehe

hehe

hehe

hehe

hehe

hehe

hehe

Hello World
```

`res.write` 只管发送数据，但是不断开链接

`res.end` 发送并结束这次请求

就是是空的`res.end()` 都可以，但是这个东西必须要有

```javascript
var http = require('http');
http.createServer(function (req,res){
    res.writeHead(200,{'Content-Type':'text/html'});
    res.write('<html>');
    res.write('<head>');
    res.write('<title>');
    res.write('</title>');
    res.write('</head>');
    res.write('<body>');
    res.write('<form>');
    res.write('username:<input name="username">');
    res.write('password:<input name="password" type="password"><input type="submit">');
    res.write('</form>');
    res.write('</body>');
    res.write('<title>');

}).listen(1337,'127.0.0.1');
console.log('Server running at http://127.0.0.1:1337');
```

![image-20190926103446122](assets/image-20190926103446122.png)



```javascript
var http = require('http');
http.createServer(function (req,res){
    console.log(req);
    res.end();
}).listen(1337,'127.0.0.1');

function doGet(req,res){

    res.writeHead(200,{'Content-Type':'text/html'});
    res.write('<html>');
    res.write('<head>');
    res.write('<title>');
    res.write('</title>');
    res.write('</head>');
    res.write('<body>');
    res.write('<form method="get">');
    res.write('username:<input name="username">');
    res.write('password:<input name="password" type="password"><input type="submit">');
    res.write('</form>');
    res.write('</body>');
    res.write('</html>');
    res.end();
 
 }
function doPost(req,res){

}
console.log('Server running at http://127.0.0.1:1337');

```

使用git是一种好的习惯，每写一次，都提交一个版本。这样就算产生了问题，都很容易撤销到原来的版本。

版本控制系统是我们的宝藏。

`req.on('data',function(data){...})` ：当接收到新的数据包的时候，就会调用这个函数

`Buffer` 内存（数据）

`req.on('end',function(){...})`  ：当数据包所有的数据都发完的时候



`:sp httpGet.js`



### socket链接

