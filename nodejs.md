# nodeJS
    Node.js是一个基于Chrome V8引擎(编译成原生机器码)的让JavaScript运行在服务器端的运行环境，
    它让JavaScript的触角伸到了服务器端。

#### 为什么要学习nodeJS
    了解前后台交互的过程

    全栈开发---》前台工程师也会写后台

#### nodeJS特性
    单线程

    非阻塞IO

    事件驱动

    node是单线程的
    node擅长高并发处理
    node 擅长I/O密集型处理


###### (1)单线程 
    NodeJS不会为每个连接客户创造一个新的线程,仅用一个线程  

###### (2)非阻塞式IO
    io:输入输出      阻塞io：网络请求，数据库处理，文件读取
 
    非阻塞式IO NodeJS在访问高IO操作后不会等待其完成，
    而是立即去执行其他代码，操作完成后会使用回调函数返回

    保证高效的利用当前线程 不造成硬件浪费
###### (3)事件驱动: 通过事件来驱动整个程序的进行

    由于是单线程，所以把高io的操作 就会移动到事件队列中等待完成，
    完成后通过回调函数的方式返回给线程来进行处理。

    这个循环处理的过程称之为：事件环

#### nodeJS模块优点
     模块有优点：
        减少代码重复，提高利用率
        划分功能，方便管理
        方便使用第三方模块

#### HTTP--------------基本服务器创建过程HTTP模块
##### http模块 是node重要的核心模块
```js
createServer(function(req,res){  //进行服务器创建

}).listen()来监听端口

```
#### 路由
    通过URL路径来区分不同的请求，从而找到不同的功能模块来进行执行。
```js
let http = require("http");
let url = require("url");

http.createServer((req,res)=>{
    res.writeHead(200,{"Context-type":"text/html;charset=utf-8"})
   
    if(url.parse(req.url,true).pathname=="/aa"){
        res.end("aaa")
    }
    if(url.parse(req.url,true).pathname=="/zz"){
        res.end("zzzzz")
    }  

}).listen(8886,(err,res)=>{
    if(err){
        console.log(err)
    }else{
        console.log("------")
    }
})
```
#### Express
    express 是一个简洁而灵活的 node.js Web应用框架, 
    提供了一系列强大特性和丰富的 HTTP 工具

    功能：
    
        扩展了web所需要的基本功能
        丰富了HTTP工具
        可以快速搭建一个网站

    安装: npm install --save express

##### Express----创建api接口
    app.post() 接受post请求;

    app.all() 方法让路由函数接收所有指定URL的HTTP方法。

    路径中使用*通配符可以匹配所有

```js
var express=require("express");
var app=express();

app.get("/user/login",function(req,res){
    res.send({msg:”ok”})
})

app.get("/ser/home",function(req,res){
    res.send({msg:”ok”})
})

var server=app.listen(3000)
```
##### Express--中间件
    中间件 每次接收到请求都会被先调用的函数 。
    就是给一些特定功能添加的一个场所。所有路由都是用的内容可以放入中间件中

    语法:
        app.use(function(req,res,next){
            next（） // 向后执行
        })

#### Express----路由创建
1.创建router文件夹并创建路由文件
1.1 首页路由
```js
var express = require("express");
var router = express.Router();

router.get("/aa",(req,res)=>{
    res.send("首页aa")
});

router.get("/bb",(req,res)=>{
    res.send("首页bb")
})

module.exports = router;//都挂在到router上，并把router暴漏出去
```
1.2 列表页路由 （同上1.1首页路由）


2.在server.js中
```js
var express = require("express");
var app = express();

//引用路由模块
let indexR = require("./routers/indexrouter");
let listR = require("./routers/listrouter");

//使用路由模块
//使用中间件调用分发路由
app.use("/index",indexR)
app.use("/list",listR)

app.listen(8882)
```