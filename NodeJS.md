​									NodeJS笔记6天

# day01

## 1-浏览器的组成部分

```html
1.U(用户交互界面)
2.Socket(网络请求部分)
3.JS Engine(JavaScript引擎)
4.render Engine (渲染引擎/浏览器内核)
5.Storage(数据存储部分)
  sessionStorage,LocalStorage,cookieStorage...
```

##2-浏览器的渲染过程(内核的工作原理)--面试

```html
1.浏览器向服务器发送请求获取到服务器返回的内容之后;
2.获取到内容为:(HTML代码);
3.渲染引擎会将HTML代码首先解析为DOM树;
4.构建渲染树;
5.处理css样式表
6.Reflow Paint :将css样式应用到渲染数中;
7.直接绘制网页
```

## 3-http协议

```html
协议:就是规定通信过程中所传递的格式和规范,目的在于让大家能够理解彼此再说什么
HTTP协议:超文本传输协议

HTTP协议使用场景:
1.主要用于浏览器和服务器通信
2.app和服务器之间的的通信也会使用http协议
向服务器请求数据用get,发送,提交数据用post ,....(delete,put..不常用);
http请求都是明文传输的.

apache监听服务器的端口:
1.获取请求
2.解析请求
3.返回结果

协议名称://域名:端口号/路径?key=value#hash值,(对应的id)

apache去网站根目录中找到对应的文件,使用http协议将找到的文件返回给浏览器
index.php与index.html,静态网页与动态网页的区别:
1-php模块作用:
2-找到php文件,
3-执行php代码,
4-将执行结果返回给apache,
5-apche将最终结果返回给浏览器
```

## 4-静态网页与动态网页的区别

```html
1.静态网页:服务器端不需要执行额外的代码,只需要将网页文件找到之后,直接返回浏览器即可
2.动态网页:服务器端需要执行代码,将最终结果返回给浏览器
```

## 5-前端人员开发与上线的大致流程介绍

```html
数据中心:就是服务器机房

程序员正常的工作都是在自己的电脑上进行的,在开发完之后,将代码上传到服务器,当用户访问网页时,需要通过域名访问服务器,而且将域名往DNS放一份,1.购买域名,2.域名解析(去阿里云买个服务器就行).

1.ftp上传文件,右键上传;
2.git远程仓库;
上传代码是由项目负责人上传代码
```

## 6-nodejs的概念,用处,原因

```html
1-nodejs概念:是一个js运行环境.(执行js代码),和之前在浏览器的代码类似

2-使用nodejs原因:
1.会nodejs优先
2.前端的基础设施(后面的vue,reactor依赖于nodejs);
3.作为前端开发工程师(FE)需要具备一定的服务端开发能力
4.降低多编程语言的开发成本
5.全栈工程师(市场需求低);

3-node.js的用处:
1.可以做后端开发(PHP Java)
2.可以开发PC端应用程序
3.开发CLI(命令行工具command line interface)--用的最多(工作5-6的前端程序员所做的工作,造文字:开发jq,vue的人,用文字的人:程序员)
```

## 7-nodeJS怎么用

```html
node.js的版本:
1.LTS:稳定版(long time) 生产环境用
2.Current(Beta):最新版(测试版)

查看有没有装node,打开cmd,键入node -v
如果有:会显示版本号
如果没有:会提示node不是内部或外部命令,也不是可运行的程序或批处理文件(环境变量没有安装好)
```

## 8-环境变量和配置的说明

```html
环境变量改了要重新运行cmd
在计算机->属性->高级设置->环境变量->高级->系统变量->path->将需要直接打开的app,找到对应的app,右击->属性里面有个起始位置,将起始位置中的代码拷贝到到path中,路径拷贝其中重新运行cmd(分号(;),根目录)
```

## 9-NodeJS的两种执行方式(REPL,使用node.js执行指定的文件)

```html
1.REPL
1.1在cmd里面键入node,启动repl之后,就可以直接写入代码执行了,相当于浏览器中的控制台一样
我们可以在REPL环境中直接输入js代码执行
R:read:读
E:evaluate:执行
P:print:打印
L:loop:循环

1.2直接写入代码,敲入回车就可以写出来.

1.3如何退出repl?
    1-直接输入两次ctrl+C;
    2-输入 .exit也可以退出repl


2.使用node.js执行指定的文件
2.1 js文件的名字不能叫node.js 
2.2 中间不能出现空格 
2.3 不要使用中文 
2.4 不要使用大写的字母
2.5 不要使用特殊字符
function sayHello() {
 console.log( "Hello Node");
}
sayHello();

1.打开cmd
2.输入node  js文件路径;
文件执行完毕会自动退出;

```

## 10-nodejs中书写js代码和浏览器中书写js代码的区别(区别是在于它不换行 )

```html
浏览器中js重组成:
1.ECMAScript(就是一些语法规则)
2.DOM  webapi(提供我们的一些对象供我们使用)
3.BOM   webapi()

nodejs中的js组成
1.ECMAScript
2.node.jsAPI

学对象的方法怎么用?
nodejs中无法使用webapi提供的功能(document  window)
console.log在输出完内容之后 会自动换行
```

### 10.1-使用node.js打印一个三角形

```js
console.log在输出为内容之后,会自动换行
for (var i = 0;i < 10;i++)
var str = "";
                          
process.stdout.write可以用来输出内容,和console.log区别是在于它不换行                     
process.stdout.write("*");
process.stdout.write("*");               
字符串中换行  process.stdout.write("\n"); 
for (var i = 0;i < 10;i++){
  for (var j = 0;j < i;j++){
   process.stdout.write("*");
   }
  process.stdout.write("\n"); 
}
注意:先退出repl,在执行js文件                    
```

### 10.2-console.log与process.stdout.write的区别

```html
1-console.log在输出完内容之后 会自动换行
2-process.stdout.write可以用来输出内容，和console.log的区别在于它不会自动换行！
```

## 11-用nodejs读写文件的操作(异步)(fs.writeFire(文件路径,数据[,options],callback),//读文件:fs.readFire(文件路径,编码格式,回调函数))

```js
1------写文件操作  
//写文件:指的是将文件读入到
文件系统(fire systerm)->fs.writeFire(文件路径,数据[,options],callback)
var str = "窗前明月光,意识低山霜";

//在使用fs之前需要将fs模块引入
var fs = require("fs");

fs.writeFile("./静夜思.txt",str,"utf8",function(err){
    if (err) {
        console.log(err);
    }else {
        console.log("写入文件成功");
    }
})
//是异步的
console.log("123");

2-----读文件操作
//读文件操作:将文件中国的内容读取到js当中

var fs = require("fs");

//读文件:fs.readFire(文件路径,编码格式,回调函数)
// fs.readFile("./静夜思.txt","utf8",function(err,data){
//     //data  读取的数据
//     if(err) {
//         console.log("读取文件失败",err));
//     }
//     else {
//         console.log("读取文件成功,文件内容"+data);
//     }
// })

//读取文件的时候,调用fs.readFile
//如果传递编码格式,则最终获取到的数据时字符串
//如果不传递编码格式,则最终获取的是Buffer对象(需要调用toString才可转成字符串)


fs.readFile("./静夜思.txt",function(err,data){
    //data  读取的数据
    if(err) {
        console.log("读取文件失败",err);
    }
    else {
        //buffer对象是16进制数据的表示形式,他是一个对象
        //如果需要读取到buffer对象转成字符串,需要调用toString方法
        console.log(data.toString("utf8"));
    }
})

```

## 12-笔记的使用说明(live-server)

```js
# 笔记的使用说明

## 安装一个live-server
必须联网安装！

1. 打开cmd
2. 输入 npm install live-server -g

## live-server的使用
1. 找到笔记目录
2. 右键  点击git bash here
3. live-server 回车

键盘快捷键:shit+alt+向下箭头 复制
```

## 13-使用同步的方法读写文件名(//fs.readFileSync(文件路径,编码格式))

```js
//fs.readFileSync(文件路径,编码格式)
var fs = require("fs");
// var str = fs.readFileSync("./静夜思.txt","utf8");
// console.log(str);
//fs.writeFileSync(文件路径,写入文件的数据,编码格式)
fs.writeFileSync("./鹅鹅鹅.txt","鹅鹅鹅,取向箱体盎然","utf8");
```

## 14-关于文件路径的研究

```js
var fs = require("fs");

//写文件的时候,文件的路径./是相对于当前执行命令的目录路径而言的
//并不是当前js文件

// fs.writeFile("./春晓.txt","春眠不觉晓,处处蚊子咬","utf8",function(err){
//     if(err) {
//         console.log("写文件失败",err);
//     }
//     else {
//         console.log("写文件成功");
//     }
// });

//无论在哪个目录执行命名,都最终生成的文件和当前js文件放在一起
//1.直接写绝对路径
//2.由于绝对路径书写过于麻烦,所以node.js中提供了一个代表当前文件所在目录路径的一个变量


//__dirname:指的是当前执行的js文件所在的目录的绝对路径
//__filename:指的是当前执行的js文件的绝对路径
// console.log(__dirname);
// console,log(__filename);

fs.writeFile(__dirname+"./春晓.txt","春眠不觉晓,处处蚊子咬","utf8",function(err){
    if(err) {
        console.log("写文件失败",err);
    }
    else {
        console.log("写文件成功");
    }
});
```

##15-路径的拼接

```js
//在很多情况下,我们需要进行路径的拼接操作
//最常见的做法,就是进行字符串拼接



//nodejs中提供了关于路径拼接的一个方法
//path.join()
//var path = require("path");
//__dirname+"/a"+"/b"+"/c"+"/望庐山瀑布.txt"
//path.join(__dirname,"a","b","c","望庐山瀑布.txt");
//path.join(__dirname,"a/b/c","望庐山瀑布.txt");
//path.join(__dirname,"a/b","c","xyz.txt");
//path.join(__dirname,"a/b/c/望庐山瀑布.txt");
```

## 16-global对象的说明

```html
//如何确定使用的时候是否进行require操作呢?

//global对象
//如果在global对象中,就不需要使用require
//如果没在,就需要使用require
console.log(global);
```

## 17-使用node.js创建一个简单的http服务器应用程序

```js
//web开发的本质:
//请求
//处理
//响应

//1.引入一个模块http
var http= require("http");

//2.创建一个http服务器实例
var server = http.createServer();

//4.给服务器实例注册一个事件 request
//当服务器监听端口的时候,如果有请求到达服务器,request事件就会被触发
server.on("request",function(request,response){
    // console.log("有请求来了!");
    //在接收到浏览器的请求之后,我们需要向浏览器响应内容
    //write方法可以调用多次
    response.write("Hello node");
    response.write("Hello node1");
    response.write("Hello node2");
    response.write("Hello node3");
    response.write("Hello node4");
    response.write("Hello node5");
    //在向浏览器响应完数据之后,需要告诉浏览器,响应结束了
    //必须结束响应过程的
    response.end();
})

//3.调用服务器实例的listen方法监听指定的端口
server.listen(8080,function(){
    //监听成功调用
    console.log("服务器已经启动,可以通过http://localhost:8080来访问了");
})
```

## 18-根据用户请求的地址不同返回不同的内容

```js
//一个端口只能被一个服务器监听
//Response.end("Chinese");//也能响应数据,不过只能响应一次

var http= require("http");

var server = http.createServer();
//如何知道用户请求的是哪个地址?
//request.url

// console.log(request.url)
server.on("request",function(request,response){

    if (request.url == "/index") {
        response.write("this is home page");
    }else if (request.url == "/login"){
        response.write("this is login page");
    }else {
        response.write("bot found");
    }
    response.end();
})

//3.调用服务器实例的listen方法监听指定的端口
server.listen(8080,function(){
    console.log("http://localhost:9999");
})
```

# day02

## 19-使用node.js模拟一个简单的phpStudy服务器

```js
// 使用node.js模式phpStudy服务器的功能
// 功能： 写好的静态网站，可以通过phpstudy来直接访问
// phpStudy起到的作用其实就是，找文件，返回给浏览器！


// 1. 引入http
var http = require('http');

// 2. 创建服务器实例
var server = http.createServer();

var fs = require('fs');
var path = require('path');

// 3. 注册事件
server.on("request", function (request, response) {

    // 返回index.html文件
    if (request.url == "/") {
        fs.readFile(path.join(__dirname, 'public', 'index.html'), 'utf8', function (err, data) { 
            response.write(data);
            response.end();
        })
    } else if (request.url == "/anoceanofsky.css") {
        fs.readFile(path.join(__dirname, 'public', 'anoceanofsky.css'), 'utf8', function (err, data) { 
            response.write(data);
            response.end();
        })
    } 

})

// 4. 监听端口
server.listen(8080, function () { 
    console.log("http://localhost:8080")
})
```

## 20-使用node.js模拟一个简单的phpStudy服务器(修复bug版)

```js
// 使用node.js模式phpStudy服务器的功能
// 功能： 写好的静态网站，可以通过phpstudy来直接访问
// phpStudy起到的作用其实就是，找文件，返回给浏览器！


// 1. 引入http
var http = require('http');

// 2. 创建服务器实例
var server = http.createServer();

var fs = require('fs');
var path = require('path');

// 3. 注册事件
server.on("request", function (request, response) {

    // http://localhost:8080/index.html  request.url /index.html
    // http://localhost:8080/anoceanofsky.css  request.url /anoceanofsky.css

    // http://localhost:8080/150.jpg  request.url  /150.jpg
    
    // 我们把文件读取的路径，直接使用了request.url
    // 这样就避免了很多次的if语句！

    // 读取文件的时候，不要加字符编码了！ 如果加了，图片就不能正常处理
    // 如果不加，则html.css等文件可以正常处理，图片也可以正常处理！

    // 如果用户访问的是 / 那么直接让其访问 /index.html  也就是默认处理
    request.url = request.url == "/" ? "/index.html" : request.url;

    fs.readFile(path.join(__dirname, 'public', request.url), function (err, data) { 
        // 当读取文件失败的时候，直接返回给用户 文件找不到！
        if (err) {
            response.write("file not found");
        } else {
            response.write(data);    
        }
        response.end();
    })

})

// 4. 监听端口
server.listen(8080, function () { 
    console.log("http://localhost:8080")
})
```

## 21-使用fs.readFile读取文件时候的注意事项

```js
var fs = require('fs');
var path = require('path');


// 在读取图片等非字符串文件的时候，我们不能加字符编码参数，否则，读取到的内容不可用
fs.readFile(path.join(__dirname, 'public', '150.jpg'), function (err, data) {
    console.log(data);
})
```

## 22-响应头中Content-Type的作用说明

```js
# Content-Type

在浏览器向服务器发送请求之后，服务器响应数据给浏览器时，会在响应头中添加一个字段，Content-Type。

由于在浏览器中使用的文件类型多种多样，对于不同的类型的文件，浏览器会有不同的处理方式。

1. 浏览器请求回来的是一个js文件。 浏览器会使用js引擎解析并执行js代码
2. 如果浏览器请求回来的是一个css文件， 浏览器会使用渲染引擎将css样式绘制到网页中
3. 如果浏览器请求回来的是一个html文件， 浏览器直接渲染html页面
4. 如果浏览器请求回来的是一个图片， 一般都是用图片的渲染方式将图片展示出来


Content-Type其实就是服务器在告诉浏览器，响应回来的文件是什么类型的。

浏览器会根据这个类型，对文件进行不同的处理！

如果在响应头中没有Content-Type,那么浏览器很可能就不知道要怎么处理这个文件了，比如没有加content-type的css文件，在ie浏览器里面就没有效果了！！


以后再返回数据给浏览器的时候，content-type一定要有！！！
```

## 23-node.js中设置响应头的方式1

```js
var http = require('http');

var server = http.createServer();

server.on('request', function (request, response) { 

    // 如何在Node.js中设置响应头的内容

    // response.setHeader("键", "值")

    // response.setHeader("Content-Type", "text/html;charset=utf8");
    // response.setHeader("shuaige", "panming");
    // response.setHeader("shuaige1", "panming1");
    // response.setHeader("shuaige2", "panming2");
    // response.setHeader("shuaige3", "panming3");
    // response.setHeader("shuaige4", "panming4");

    response.write("你好，世界");
    
    // setHeader方法必须在write方法之前调用！ 下面的代码有问题！
    // response.setHeader("Content-Type", "text/html;charset=utf8");    
    response.end();
})

server.listen(8080, function(){
    console.log("http://localhost:8080")
})
```

## 24-node.js中设置响应头的方式2

```js
var http = require('http');

var server = http.createServer();

server.on('request', function (request, response) { 

    // 如何在Node.js中一次性设置多个响应头的内容

    // 如果使用response.setHeader 那么要调用好多次

    // node.js中提供了一个response.writeHead方法，这个方法就可以用来一次设置多个响应头信息

    response.setHeader("gender", "male");
    
    // response.writeHead(状态码， 状态信息， 响应头对象)；
    // response.wirteHead也不能在response.write之后调用
    response.writeHead(200, "OK", {
        name: "pm",
        age: 18,
        "Content-Type": "text/html;charset=utf-8"
    });

    

    // response.writeHead(404, "Not Found", {
    //     name: "lmd",
    //     age: 38,
    //     "Content-Type": "text/html;charset=utf-8"
    // });

    response.write("你好，别感冒！");

    response.end();
})

server.listen(8080, function(){
    console.log("http://localhost:8080")
})
```

### 两种方式设置响应头的区别

```js
1-response.setHeader(key,value) 只能一次设置一条
2-response.writeHead(statusCode,statusMessage,header对象) 一次可以设置多条
着两个设置响应头的方法 都必须在response,write之前调用

属性:说明(request)
url:获取请求地址中的 路径+参数!
headers:获取请求头中所有的信息,是一个对象
rawHeaders:获取请求头中所有的信息,是一个数组
httpVersion:获取http协议的版本号
method:获取请求方式,是大写字母字符串 GET POST

成员:说明(response)
write:向浏览器响应数据,参数可以是字符串也可以是buffrt对象
end:结束响应,也可以向浏览器响应数据,参数可以是字符串也可以是buffer对象!
setHeader:设置响应头,一次一个
writeHead:设置响应头,状态码,状态信息,响应头一次多个
statusCode:设置状态码
statusMessage:设置状态信息
```

## 25-使用node.js模拟phpStudy(为不同的文件设置不同的content-type)

```js
// 使用node.js模式phpStudy服务器的功能
// 功能： 写好的静态网站，可以通过phpstudy来直接访问
// phpStudy起到的作用其实就是，找文件，返回给浏览器！


// 1. 引入http
var http = require('http');

// 2. 创建服务器实例
var server = http.createServer();

var fs = require('fs');
var path = require('path');

// 引入mime包
var mime = require('mime');

// 3. 注册事件
server.on("request", function (request, response) {
    request.url = request.url == "/" ? "/index.html" : request.url;
    

    // response.setHeader("Content-Type", "image/jpg");
    // 我们需要根据用户请求的不同的文件，给响应头设置不同的Content-Type
    // 如果要自己处理，则需要大量的条件判断！ 所以不做了！！
    // if (是图片) {
    //     response.setHeader("Content-Type", "image/jpg");   
    // } else if (是css) {
    //     response.setHeader("Content-Type", "text/css");           
    // } else if (是html) {
    //     response.setHeader("Content-Type", "text/html");         
    // } else if (是js) {
    //     response.setHeader("Content-Type", "application/javascript");         
    // }

    // 我们可以找一个现成的工具来帮我们做这件事情！
    // mime  
    // 使用步骤：
    // 1. 下载
    //   1.1. 先在命令行中执行 npm init -y
    //   1.2. 在命令行中执行 npm install mime
    // 2. 使用 
    //   1.1. 在代码中引入  var mime = require('mime')

    response.setHeader("Content-Type", mime.getType(request.url));

    fs.readFile(path.join(__dirname, 'public', request.url), function (err, data) { 
        // 当读取文件失败的时候，直接返回给用户 文件找不到！
        if (err) {
            response.write("file not found");
        } else {
            response.write(data);    
        }
        response.end();
    })

})

// 4. 监听端口
server.listen(8080, function () { 
    console.log("http://localhost:8080")
})
```

## 26-mime的使用说明

```js
// mime功能：  可以根据不同的文件类型，获取到不同的Content-Type,就避免了自己去写大量的if语句

// 使用步骤：
// 1. 下载
//   1.1. 先在命令行中执行 npm init -y
//   1.2. 在命令行中执行 npm install mime
// 2. 使用 
//   1.1. 在代码中引入  var mime = require('mime')


var mime = require('mime');

// mime模块中提供了一个方法，可以根据文件的名称或路径获取到文件对应的Content-Type类型
var contentType = mime.getType("a/b/c/index.js");

// 了解即可， 根据Content-Type获取后缀名
var ext = mime.getExtension("video/x-msvideo");

console.log(ext);
```

## 27-request对象和response对象的详细介绍

```js
var http = require('http');
var server = http.createServer();

server.on('request', function (request, response) {
    
    // 给server对象注册的request事件，当服务器接收到浏览器的请求之后，就会出触发
    // 触发之后，回调函数就会被调用！

    // 回调函数被调用的时候，node.js会自动给这个函数传递进来两个参数
    // 1. request: 所有和请求相关的信息，都可以从request对象中获取
        // url: 请求地址中的 路径+参数 
        // headers: 请求头中的内容都以对象的形式保存在header属性中，我们可以用来获取浏览器信息，cookie信息等等
        // rawHeaders: 数组形式保存的请求头信息（不常用）
        // httpVersion: http协议的版本号    
        // method: 获取请求的方式！
    
    
    // console.log(request.rawHeaders);
    // response.write(request.url);
    // response.end();

    // 2. response： 所有和响应相关的api都可以通过response来访问

        //response.write()   给浏览器响应数据，参数可以是字符串，也可以是buffer对象。
        //response.end()    结束响应的，也可以传递参数给浏览器响应数据，参数可以是字符串，也可以是buffer对象。
        //response.setHeader()  设置响应头的，一次只能设置一条，必须在write之前调用
        //response.writeHead()  设置响应头的，一次可以能设置多条，必须在write之前调用， 可以设置状态码和状态信息
        //response.statusCode  
        //response.statusMessage
    
    
    response.statusCode = 404;
    response.statusMessage = "Not Found";
    // response.writeHead(200, "ok", {})
    
    
    response.end("diule");

})

server.listen(8080, function () {
    console.log('http://localhost:8080');
})
```

## 28-npm的简介

```js
# npm

## 是什么？
Node Package Manager
Node包管理工具： 它是全世界最大的开源软件库！

## 三个npm相关的内容
1.npm服务器:存储所有的包
2.npm网站:浏览,搜索所有的包 查看包的文档,作者
3.npm命令行工具:可以用来操作npm服务器,上传包,更新包
```

## 29-使用node.js模拟一个phpStudy服务器

```md
1----phpStudy功能:
1.创建一个简单的php服务器;
2.对/index.html的请求做了处理(找到public目录下的index.html文件响应给浏览器)
3.对/anaceanofsky.css请求做处理(找到public目录下的anaceanofsky.css文件响应给浏览器)
4.直接使用request.url作为查找文件的路径,将所有的资源都给浏览器正常返回.
5.返回图片给浏览器之后,发现图片不能够正常展示(原因在于使用fs.readFile读取图片文件的时候,设置了utf8编码,导致图片数据不正常了,将字符编码参数删掉)
6.我们响应给浏览器的所有内容.都没有Content-Type响应头(如果响应头中没有Content-Type信息,可能有的浏览器就无法对返回的数据进行正常的处理),我们需要给响应头中设置文件对应的Content-Type
7.使用到mime这个第三方包


2----怎么设置响应头
1.response.setHeader
2.response.writeHead

3----request对象和response对象
```

## 30-npm的使用

```md
1-npm的安装
只要你把node安装好了,那么npm会自动的安装好!

2-使用
1.在当前文件夹下创建一个package.json文件
npm init
npm init -y
npm init --yes

2.下载包
npm install 包名
npm install 包名@版本号
npm i 包名
npm i 包名@版本号

3.本地安装和全局安装
###本地安装
npm install 包名

本地安装的包,会被存储当前项目中的node_modules目录中!

###卸载
npm uninstall 包名
右击:卸载

###全局安装
npm install 包名 -g
npm install 包名 --global

只有需要被当做全局命令来使用的包,才需要做全局安装
全局安装之后,这个包就会提供一个全局的命令行工具来给我们使用.
在C盘根目录下有个AppData->Roaming->npm->node_modules下面,或者win+R->%
```

## 31-包的概念说明

```html
1-包的概念
包指的就是一组使用了packsge.json描述的文件
package.json必须符合规范:必须有name 和 version

只要一个文件夹中有一个合法的package.json文件,那么这个文件就可以被称为包!

package.json中保存的就是当前包的所有信息

1.name:包名(只能有小写的英文,包名不能和已有的别人的包的名字重复)
2.version:版本号(主版本号,次版本号,修订版本号)
  1.主版本号更新,则意味着更新后的版本不兼容之前的版本了
  2.此版本号更新,兼容之前的版本,但是会有一定的功能更新
  3.修订版本号,没有功能的更新,只是BUG的修复或小的更新

3.main:模块化中会用到(后续课程讲)
4.script
5.dependencies:着对象中保存的是当前包,(运行时)所依赖的其他的包的信息(包名,版本号)
6.devDependencies:这对象保存的是当前包,(开发时)所依赖的其他包的信息(包名,版本号)

dependencies和devDependencies主要是便于代码共享
程序员A在把代码共享给程序员B的时候,可以直接将node_modules删掉,以缩小传输的文件的大小.程序员B在接收到所有代码之后们只需要执行一步(npm install),就可以自动根据package.json中保存的依赖项信息,下载所有的包!

如果只需要下载运行时需要的包,执行如下的命令
npm install --production

安装时依赖项的保存位置的选择
npm install 包名 默认会将包信息保存到dependencies中
npm install 包名 --save
npm install 包名 -S

如果要将包信息保存到devDependencies中,需要使用下面的命令
npm install 包名 --save-dev
npm install 包名 -D
```

## 32-使用npm上传和下载包

```md
1-使用npm上传包
1.创建一个自定义的包
	1.创建文件夹
	2.给文件夹中创建一个package.json文件(合法,符合规定的);
2.注册一个npm账号
3.在npm命令行工具中登录
	npm login
4.将包上传
	npm publish
	
	
	
1-下载包
npm install 包名
npm install 包名@版本号
npm i 包名
npm i 包名@版本号

npm install 包名1 包名2 ...

npm i 这个命令是用来下载package.json文件中保存的所有依赖项包
```

## 33-使用node.js自己写假数据接口

```js
var http = require("http");

var server = http.createServer();
var fs = require("fs");
var path = require("path");

server.on("request",function(request,response){
    //定义一个数组,里面存储了假的数据
    var data = [
        {id:1,name:"张丹三",age: 18},
        {id:2,name:"李四",age:24},
        {id:3,name:"王五",age:20},
        {id:4,name:"田七",age:25}
    ]

    //设置响应头里面的content-type属性
    response.setHeader("Content-Type","application/json");

    //解决跨域问题
    response.setHeader("Access-Control-Allow-Origin","*");
    response.setHeader("Access-Control-Allow-Headers","X-Requested-with,accept,origin,content-type");

    response.end(JSON.stringify(data));
})
server.listen(8080,function(){
    console.log("http://localhost:8080");
})
```

## 34-使用node.js实现hacker-news的基本页面展示

```js
## 使用node.js实现hacker-news的基本页面展示

1. 创建一个简单的http服务器（4个基本步骤）
2. 设计路由规则（不同的url对应不同的响应内容）
3. 设计了4个路由  首页 添加页 详情页 404页
4. 在首页请求中返回views/index.html文件
5. css和图片的请求都没有处理
6. 又加了一条路由规则 req.url.indexOf("/resources") == 0
7. 在这个路由规则中，以req.url作为文件路径，直接读取文件返回给浏览器，注意要设置Content-Type,用到了mime
8. 添加页和详情页（实现和首页一模一样）
```

## 35-前端渲染和后台渲染

```js
1-前端渲染
前端负责静态页面的编写,页面中所有的数据,都是前端人员通过ajax请求向后台获取数据之后,通过模板引擎的技术渲染在页面中,最终展示出来的
2-后端渲染
前端负责静态页面的编写,页面中所有的数据,都是在浏览器向服务器发送请求的时候,后端服务器接收到请求之后,将数据填充到静态页面中,将带有数据的静态页面返回给浏览器,最终将数据展示出来
```

# day03

## 36-nrm

```js
## nrm
可以用来切换npm下载时使用的服务器！
1. 安装
​```shell
npm install nrm -g  //当安装完nrm之后,命令就可以使用nrm命令了
					//检测是否安装成功 nrm -V 查看版本信息
​```
2. 使用
​```
1.展示所有的可用服务器 nrm ls
2.切换到指定的服务器, nrm use 服务器名称
3.测试服务器的延迟 nrm test 服务器名称       延迟越小,速度越快!
  nrm 显示所有nrm的命令

##注意:
使用nrm切换服务器之后,如果切换的不是官方的服务器了,那么不能进行包上传
上传包只能给官方服务器上传!!!

cnpm尽量别用,问题多,以后用nrm就好 
​```
```

## 37-node.js操作文件保存数据

```js
1.读取所有的数据
fs.readFile(path.join(__dirname,"data.json"),"utf8",function(err,data){
    if(err) {
        data = "[]"
    }
  var newsList = JSON.parse(data);
})

2.读取指定id对应的数据
fs.readFile(path.join(__dirname,"data.json"),"utf8",function(err,data){
    if(err) {
        data = "[]"
    }
  var newsList = JSON.parse(data);
  var news = newsList.find(function(v,i) {
      return v.id == 10;
  })
})

3.添加新数据
fs.readFile(path.join(__dirname,"data.json"),"utf8",function(err,data){
    if(err) {
        data = "[]"
    }
  var newsList = JSON.parse(data);
  var news = {title:"",url:"",text:""};
  news.id = newsList.length == 0 ? 1 :newsList[newsList.length - 1].id +1;
  newsList.push(news);
  
 fs.writeFile(path.join(__dirname,"data.json"),JSON.stringify(newsList),function(err){
     
 })
})
```

## 38-art-template的使用

```js
1. 以文件作为模板
var template = require("art-template");
var html = template(文件路径,数据);

eg:
// 第一种方式： 模板是一个文件
//1. 引包
var template = require('art-template');
var path = require('path');

//2. 创建模板
// 模板在一个文件中创建的

//3. 准备数据
var data = {
    name: "李明达·迟到的人",
    arr: [
        "迟到",
        "抽烟",
        "喝酒",
        "烫头"
    ]
}

// //4. 调用模板引擎渲染数据
var html = template(path.join(__dirname, '05-node模板文件.html'), data);
console.log(html);

2.以字符串作为模板
var tpl = "模板字符串"
var render = template.compile(tpl);
var html = render(数据)

eg:
// 第二种方式： 模板是一个字符串
var tpl = `
    <div>{{name}}</div>

    <ul>
    {{each arr v i}}
        <li>{{v}}</li>
    {{/each}}
    </ul>
`
// 1. 需要将模板转换成一个渲染函数
var render = template.compile(tpl);

// 2. 调用上一步中生成的渲染函数进行数据渲染
var html = render(data);

console.log(html);
```

## 39-hacker-news数据展示的实现（首页，详情页)与添加功能的实现

```js
## hacker-news数据展示的实现（首页，详情页）
1. 先读取data.json中的数据
2. 读取模板文件（index.html details.html）
3. 使用模板引擎将数据渲染到模板中
4. 将渲染结果返回

## hacker-news添加功能的实现
1. 获取用户提交的数据
2. 获取data.json中数据
3. 将提交的新数据添加id只有push到原有数组中
4. 将数组重新保存回data.json
```

## 40-url模块

```js
url.parse方法可以将url地址字符串装换成一个对象
//第一个参数就是要被转换的url字符串
//第二个参数表示是否要将参数转换成对象
var urlObj = url.parse(req.url,true);

//urlObj.query
//urlObj.pathname
```

## 41-hacker-news代码优化

```js
1.将读写数据的方法进行封装(回调函数的使用)
2.将渲染模板的方法进行封装(render函数)
```

## 42-模块化

```js
1.概念
按照特定的逻辑将代码拆分成一个个小模块的过程就是模块化

2-意义
2.1 便于维护
2.2 提高代码的可读性
2.3 便于复用

3-标准
标准的出现时为了让模块更加通用!
3.1 AMD :异步模块定义 依赖前置 require.js
3.2 CMD　：通用模块定义　依赖延迟 sea.js
3.3 CommonJS

4-node.js中的模块化

4.1.定义模块
4.1.1 一个js文件就是一个模块,每个模块有自己独立的作用域

4.2 引用模块
4.2.1 require函数就可以用来引用模块,require函数的返回值就是被引入的模块的导出项(module.exports)
```

## 43- node.js中模块的导出项设置和获取

```js
1. 设置
​```js
module.exports.名字 = 导出的内容
module.exports = 导出的内容
​```

简写形式
​```js
exports.名字 = 导出的内容

// 下面的写法不可以，因为导出的内容是module.exports不是exports
exports = 导出的内容
​```
2. 获取
直接接收require函数的返回值，就可以获取到被引入模块的导出项了！
```

## 44-require函数的加载规则

```js
1-模块的分类
1.核心模块
2.第三方包模块
3.目录模块
4.文件模块

核心模块与第三方包模块的引入
​```js
require("模块名称")
​```
目录模块和文件模块的引入
​```js
require("目录或者文件路径")
​```
```

## 45-加载规则

```js
1. 先找路径对应的js文件，如果找到了，就引入
2. 如果没有找到, 找文件路径对应的json文件，找到了就引入
3. 如果没有找到，找文件路径对应的.node文件，找到就引入
4. 如果没有找到，就去找路径对应的文件夹， 如果找到了
    1. 在文件夹中查找package.json文件， 如果找到
        1. 查看package.json文件中，是否有main属性
            1. 如果有，就直接引入main属性指向的文件
            2. 如果没有main属性， 就找index.js index.json index.node
    2. 如果没有找到package.json文件
        1. 找当前文件夹中index.js进行引入，如果有就引入
        2. 如果没有index.js就找index.json，如果有就引入
        3. 如果没有就找index.node，如果有就引入
        4. 如果没有，就直接报错。
```

## 46-使用模块化改造hacker-news

```js
1-主模块:主要负责启动Http服务器
2-路由模块:主要负责设置路由器
3-数据操作模块:主要负责数据的读写操作

4- 路由处理模块 ： 由于之前我们把所有的路由处理的代码都放到了router.js中，router.js中的代码就比较混乱了，所以讲处理的代码全部提取出来，放到handler.js中
5- 功能扩展模块 ： 主要负责给req和res扩展实用的功能  req.ulrObj  res.render
```
# day04

## 47-node.js中获取post请求参数

```js
在 router.js里面单独给post开辟一个路径
在handler.js加个postAddHandler:function(req,res){
    //1.获取用户请求的数据
  
  	//2.将新的新闻数据添加到data.json中
}


var http = require('http')
var server = http.createServer();

var url = require('url');

server.on('request', function (req, res) {
    // var urlObj = url.parse(req.url, true);
    // console.log(urlObj.query);


    var bufferList = [];
    // 在node.js中获取post请求参数，需要用到两个事件
    req.on('data', function (chunk) { 
        // data事件 是当有post数据被发送到服务器的时候，会触发
        // console.log("有数据来了");
        // console.log(chunk);
        // 每次接收到数据之后，需要先将数据保存起来
        bufferList.push(chunk);
    })

    req.on('end', function () {
        // end事件 是当所有的post数据全部发送完毕之后，会触发
        // 在数据接收完毕之后，我们可以将bufferList中存储的所有的buffer对象拼接起来
        // 转换成字符串来使用
        
        // Buffer构造函数提供了一个concat方法，用来将多个buffer对象拼接成一个buffer对象

        var buffer = Buffer.concat(bufferList);

        console.log(buffer.toString('utf8'));
        // console.log("数据发送完毕了")
    })



    console.log(req.method);
    res.end("ok");
})

server.listen(8080, function () { 
    console.log('http://localhost:8080');
})
```

## 48-将查询字符串转换成对应的对象

```js
var str = "name=limingda&age=25&gender=male";

//在node.js中提供了一个核心模块 querystring 这个模块就可以将查询字符串转换成其对应的对象

var querystring = require('querystring');

var obj = querystring.parse(str);

console.log(obj);
```

## 49-express中注册路由的方式介绍

```md
# express中注册路由的方式

express是一个基于node.js的web开发框架
1.是什么?
能够做和node.js做一样的事情(web开发);
2.能做什么?
能够提高我偶们的开发效率

## 1.使用app.METHOD来注册路由
使用请求方式作为方法名
​```js
app.get(路由路径, function(req, res){

})
get注册路由规则
send发送数据给浏览器
app.post(路由路径, function(req, res){
    
})
app.delete(路由路径, function(req, res){
    
})
​```
特点：
1. 使用该方式注册的路由，必须使用指定的请求方式（注册路由的方法名）来请求，否则请求不到
2. 使用该方式注册的路由，请求的路径必须和注册的路径完全匹配

## 2.使用app.all来注册路由
​```js
app.all(路由路径, function(req, res){

})
​```
特点：
1. 使用该方式注册的路由，所有的请求方式都能够请求到
2. 使用该方式注册的路由，请求的路径必须和注册的路径完全匹配

## 3.使用app.use来注册路由
​```js
app.use(路由路径, function(req, res){

})
​```
特点：
1. 使用该方式注册的路由，所有的请求方式都能够请求到
2. 使用该方式注册的路由，请求的路径只要是以注册的路径开头就可以访问到！
(req.path拿到的是除了路由路径之后的路径部分)
```

```js
var express = require('express');
var app = express();

// app.get("/index", function (req, res) {
//     res.send("首页请求成功");
// })

// app.post('/login', function (req, res) {
//     res.send("登录页面请求成功");
// })

// app.all('/list', function (req, res) { 
//     res.send("列表页面请求成功");
// })

// app.use('/detail', function (req, res) {
//     res.send("详情页请求成功");
// })

// app.use("/", function (req, res) {
//     res.send("这是一个神奇的东西");    
// })

app.use(function (req, res) {
    res.send("这是一个神奇的东西");    
})

app.listen(8080, function () { 
    console.log('http://localhost:8080')
})
```

## 50-express中req对象实用成员

```md
# express中req对象实用的成员

* req.hostname: 域名
* req.originalUrl: 原始url中的:路径+参数
* req.path: url地址中的路径
* req.query: get请求参数对象
* req.body: post请求参数对象,(必须使用body-parser中间件才会有值,否则是undefined)
*req.params :
		? 传参不利用SEO;
		app.get("/index/:id/:age,function(req,res){
          res.send(req.params);
		}")
		http://localhost:8080/index/18/100
		返回一个对象{id:18,age:100}
# express中res对象中实用的成员
* res.send :用来给浏览器响应数据，并且会自动调用end方法结束响应，只能调用一次
   	// send方法可以接受哪些参数？
    // 1. 字符串
    // 2. 对象
    // 3. 数组
    // 4. 数字： 数字会被作为状态码使用
* res.json :返回json数据
* res.jsonp :返回jsonp数据 就是一个函数调用,里面的参数是实际的json数据
* res.redirect : 跳转页面
* res.sendFile :可以直接给浏览器响应文件,并且自动设置content-type属性
* res.status :设置响应状态码,res.status(404).send("ok");
```

### req对象中的属性和方法

```js
// 1.引入express模块
var express = require('express');

// 2.创建express实例
var app = express();

var path = require('path');

// 注册路由
app.get("/index", function (req, res) {
    // res.send("这是中文，你乱码不？");
    // req.hostname: 域名
    // req.originalUrl: url中的路径+参数
    // req.path: url地址中的路径
    // req.query: get请求参数对象,返回的是一个对象

    // res.send(req.query);


    // res.send方法： 用来给浏览器响应数据，并且会自动调用end方法结束响应，只能调用一次
    // send方法可以接受哪些参数？
    // 1. 字符串
    // 2. 对象
    // 3. 数组
    // 4. 数字： 数字会被作为状态码使用

    // res.send();
    // res.json({name: "123"}); 返回json数据
    // res.jsonp({name: "123"}); 返回jsonp数据

    // res.redirect() 跳转页面
    // res.redirect("http://baidu.com");


    // res.sendFile();   //可以直接给浏览器响应文件
    res.sendFile(path.join(__dirname, '1.jpg'));

    // res.render
})

// 3.使用app实例监听指定的端口
app.listen(8080, function () { 
    console.log('http://localhost:8080');
}) 
```

## 51-Router

```js
var router = require("express").Router()
//express中提供了一个函数Router,可以用来创建一个路由对象
//路由对象可以用来注册路由规则
将app改成routers
var router = require("./router");
在app.js里面app.use(router)
```

## 52-req.params的说明

```js
var express = require('express');
var app = express();


// http://localhost:8080/index/18

app.get('/index/:id/:age', function (req, res) {
  	//:id  :age是个占位符
    res.send(req.params);//测试的时候在地址栏通过/index/1/18
})

app.listen(8080, function () {
    console.log('http://localhost:8080');
})
```

## 53-express中post请求参数的获取

```js
var http = require("http");

var server = http.createServer();
//在node.js中获取post请求参数的获取
//需要用到两个事件
server.on("request",function(){
    var bufferList = [];
    req.on("data",function(chunk){
        //触发时机:
        //chunk:数据块
        //data事件 是当有post数据发送到服务器的时候,会触发
        //数据大的时候,会触发多次
        // console.log(chunk);
        //每次接受到数据之后,先将数据保存起来
        bufferList.push(chunk);
    })
    
        req.on("end",function(){
            //end事件 是当所有的post数据全部发送了,会触发
            //在数据接受完毕之后,我们可以将bufferList中存储得到所有的buffer对象拼接成一个buffer对象
            //装换成字符串
            //BUffer构造函数提供了一个Concact方法,用来将多个buffer对象拼接成buffer对象


            var buffer = Buffer.concat(bufferList);

            console.log(buffer.toString("utf8"));
            console.log("数据发送完毕了");
        })
    })

    server.listen(8080,function(){
        console.log("http://localhost:8080");
    })

```

## 54-experss中模板引擎的使用方式介绍

```js
var express = require("express");
var app = express();
var path  = require("path");

app.engine("html",require("express-art-template"));
app.set("views",path.join(__dirname,"templates"))
app.set("view engine","html");
app.get("/",function(req,res){
    var obj = {
        name : "余益鸿",
        age:18
    }

    res.render("index",obj);
})

app.listen(8080,function(){
    console.log("http://localhost:8080");
})
//1.通过app.engine()的方法注册一个模板引擎
//app.engine("模板文件的后缀名",模板引擎提供的处理程序)
//art-template中express的使用,看art-template中文网
//npm i express-art-template
//app.engine("html",require("express-art-template"));

//调用res.render方法进行模板渲染的时候
//express会自动的去 根目录下面的views文件夹中查找文件名对应的文件
//如果文件的名字后缀为 .html,express

//2.指定查找模板文件的目录路径
//app.set("views",目录路径);
//app.set("views",path.join(__dirname,"templates"));

//3.给模板文件设置默认的扩展名
//app.set("view engine","html");
```

## 55-storage.js

```js
var fs = require('fs');
var path = require('path');
module.exports = {
    readNewsData: function (callback) {
        fs.readFile(path.join(__dirname, 'data.json'), 'utf8', function (err, data) {
            if (err) {
                data = '[]'
            }
            callback(JSON.parse(data));
        })
    },
    writeNewsData: function (newsList, callback) {
        fs.writeFile(path.join(__dirname, 'data.json'), JSON.stringify(newsList), function (err) {
            callback();
        })
    },
    addNews: function (news, callback) {
        var that = this;
        this.readNewsData(function (newsList) {
            news.id = newsList.length == 0 ? 1 : newsList[newsList.length - 1].id + 1;
            newsList.push(news);
            that.writeNewsData(newsList, callback);
        })
    },
    getAllNews: function (callback) {
        this.readNewsData(callback);
    },
    getNewsById: function (id, callback) {
        this.readNewsData(function (newsList) {
            var news = newsList.find(function (v, i) {
                return v.id == id;
            })
            callback(news);
        })
    }
}
```

## 56-总结

```js
#node.js 第四天
##post 请求参数的获取
var bufferList = []
req.on("data",function(chunk){
  bufferList.push(chunk);
})
req.on("end",function(){
  var result = Buffer.concat(bufferList;)
  result = result.toString("utf8")
})

##将查询字符串转换成对象
var querystring = require("querystring");
var str = "key=value&key=value1";
var obj = querystring.parse(str);

//qs
##express
1.是什么
是基于node.js的web应用框架
2.能做什么
2.1 能够做和node.js一样的事情(web开发)
2.2 它能够提高我们的开发效率
3.怎么做
	var express = require("express");
	var app = express();
	app.listen(8080,function(){
        console.log("http://localhost:8080");
    })
## express中路由注册的方式
1.app.METHOD
//特点
1-1.必须以特定的方式请求
1-2.路由路径必须和请求的路径完全匹配
app.get(路由路径,function(req,res){})
app.post(路由路径, function(req, res){})
app.delete(路由路径, function(req, res){})

2.app.all
//特点
2-1.任何的请求方式都支持
2-2.路由路径必须和请求的路径完全匹配
app.all(路由路径, function(req, res){})

3.app.use
//特点
3-1 :任何的请求方式都支持
3-2: 请求的路径只能是以路由路径开头即可(req.path拿到的是除了路由路径之后的部分)
path.join(__dirname,'resources',req.path);
// example.com/users?sort=desc
req.path
// => "/users"
app.use(路由路径, function(req, res){})

## req 和 res对象
req和res对象就是node.js中原生的两个对象，只是express给这两个对象中新增了很多有用的成员！

### req
req.hostname:   域名
req.originalUrl:    原始url： 路径+参数
req.path：      路径
req.query：     get请求的参数
req.body:       post请求的参数（必须使用body-parser中间件才会有值，否则是undefined）必须先设置才能拿到值,否则为undefined

req.param:参数,当设置路由路径时,/:参数名

### res
res.send:   发送数据给浏览器并且自动调用end方法，可以传递几乎任何参数，如果传递数字会被作为状态码使用
res.json：  返回一个对象的json字符串
res.jsonp:  返回jsonp格式的数据（函数调用）
res.sendFile: 返回指定的文件内容  会自动设置Content-Type
res.redirect: 跳转页面
res.status: 设置响应状态码
res.status(404).send("ok");
res.render() :必须先设置才能拿到值,否则会报错,在使用之前,就进行配置
	app.engine();//可设置多个
	

##express中post请求参数的获取
使用之前先下载:npm i body-parser,在引入
var bodyParser = require("body-parser");
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({extended:true}));//true 为qs,false为querystring,默认为true

//req.body就可以获取post参数了

##express中模板引擎的使用
//express中为了res新增了一个render方法,这个方法可以直接用来渲染模板,但是需要先进行设置

//1.设置文件后缀名以及其对应的模板引擎
app.engine("html",require("express-art-template"));
//2.设置查找模板文件的目录,如果不设置会自动去views文件中找
app.set("views",目录路径);
//3.设置默认的模板后缀名,如果设置了后缀名,则调用render方法的时候在写后缀了
app.set("view engine",后缀名);
res.render(模板文件名,要渲染的数据);

##路由对象
express中提供了一个函数可以用来创建路由对象,路由对象可以用来注册路由规则
var router = require("express").Router();

//router.get
//router.use
//router.all
app.use(router);

##express实现了hacker-news(练习)

##express实现hacker-news进行模块化改造
1.主模块
2.路由模块
3.路由处理模块
4.数据操作模块
```

# day05

## 57-中间键的介绍(req,res,next)

```js
//中间键:middleware

//1.中间件是什么
就是在整个请求-处理-响应流程中,对请求处理的逻辑代码
本质其实就是一个函数,这个函数会接收三个参数,req,res,next
req:请求对象
res:响应对象
next:调用下一个中间件

//中间件能做什么?
对于数据进行处理,分模块

//2.如何给处理响应的流程中注册中间件?(添加中间键)
1.app.METHOD
2.app.all
3.app.use

//3.中间键中需要做得事情
//每个中间键都必须做如下两件事情中一件
//1.结束响应
//2.手动的调用下一个中间件
//如果这两件事都不做,就直接挂起了

var express = require("express");
var app = express();

app.use(function(req,res){
  //res.send('第一个ok');
  //1.第一种选择,结束响应
  console.log('ok')
  //2.第二中选择,手动的调用下一个中间件
  next();
})
app.use(function(req,res){
   res.send('第二个ok');
})

app.listen(8080,function(){
    console.log("http://localhost:8080");
})

//运行结果:ok
```

## 58-express中间键的调用条件

```js
var express= require("express");
var app = express();

//在express中默认就包含了一个中间件,这个中间件用来返回404的
//这个中间件始终在最后一个位置

//中间件的调用必须满足条件
//app.get("/index",fucntion(req,res,next){}
)
//上面的代码的注册中间件,必须满足条件:
##1.get请求 ,2.请求路径是/index

app.get("/index",function(req,res,next){
   console.log('/index被访问了')
   next();//测试在地址栏输入/index
})
app.get("/login",function(req,res,next){
   console.log('/login被访问了')
   res.end();
})
app.listen(8080,function(){
    console.log("http://localhost:8080");
})
```

## 59-body-parser中间件的原理说明

```js
//app.use(bodyParser.json())的作用;
1.获取了post请求的参数
2.将post请求参数转换成一个对象
3.将这个对象赋值给req.body属性


var express= require("express");
var app = express();
//var bodyParser = require("body-parser");
//app.use(bodyParser.json());//返回值就是一个中间件
var myBodyParser = require("./myBodyParser");
app.use(myBodyParser);
##自己封装就就是为了替代express里面的两句代码

app.post("/index",function(req,res,next){
  //获取post请求参数
  res.send(req.body);//什么都没有返回,为undefind,将其装换成空字符串
  //安装一个body-parser
})

app.listen(8080,function(){
    console.log("http://localhost:8080");
})
```

## 60-实现自己的body-parser

```js
var express= require("express");
var app = express();
var bodyParser = require("mybody-parser");

app.use(bodyParser.json());

app.post("/index",function(req,res,next){
  //获取post请求参数
  res.send(req.body);//什么都没有返回,为undefind,将其装换成空字符串
  //安装一个body-parser
}

app.listen(8080,function(){
    console.log("http://localhost:8080");
})



//将use()里面的提取出来
//./mybody-parser.js
var bodyParser = require("body-parser");
var querystring = require("querystring");
module.exports = function(req,res,next){
    var bufferList =[];
   req.on("data",function(chunk){
       bufferList.push(chunk);
   })
   req.on("end",function(){
       var result = Buffer.concat(bufferList);
     	result = result.toString("utf8");
     //2.将post请求参数转换成一个对象
     //这里获取到的字符串有两种可能:
     //我们需要对用户传递过来的数据格式进行判断(请求头中的Content-Type);
     //req.send(app.get("content-type"))
     //app.get("content-type") 设置的是属性和值两个参数,然后用get获取属性,得到的是值.
     
     if(req.get("content-type").indexOf("urlencoded")!= -1) {
      //2.1.查询字符串(x-www-form-urlencoded)
     result = querystring.parse(result); 
     }else if(req.get("content-type").indexOf("json")!= -1) { 
     //2.2.json字符串(application/json)
     result = JSON.parse(result);
     }else {
         result = {};
     }
     //3将这个对象赋值给req.body属性
     req.body = result;
     //4.调用下一个中间件
     next();//返回都是同一个
   		})
	});//返回值就是一个中间件
}
```

## 61-使用express内置中间件static处理静态资源

```js
var express= require("express");
var app = express();
var path = require("path");
//复制resources文件夹进来
//app.use("/resources",function(req,res,next){
//  res.sendFile(path.join(__dirname,"/resources",req.path));
res.send("ok");
//})

//express.static 可以用来托管静态资源
//下面的代码可以帮组我们直接在浏览器中通过
//http://localhost:8080/css/news.css 访问到resources目录中的css文件
//app.use(express.static("/resources"));

//如果要通过http://localhost:8080/resources/css/news.css 访问到resources目录中的css文件,通过如下形式:
app.use("/resources",express.static("/resources"));

app.listen(8080,function(){
    console.log("http://localhost:8080");
})
```

## 62-mongodb-非关系型数据库

```js
//用文件保存数据:操作困难,用起来不方便
##非关系型数据库:
表和表之间没有关系

##非关系型数据库一般都是内存型数据库
内存型数据库指的是数据保存在内存中的数据库!
  
MySql:关系型数据库,数据保存在硬盘里
mongodb:非关系型数据库,数据暂存在内存中,最终会保存到硬盘中进行持久的存储

##内存的介绍
```

## 63-mongodb安装及使用说明

```js
//mongodb安装  存储的是二进制存储的格式,叫BSON
//查看有没有安装成功:mongo --version
如果报错:mongo不是内部或外部变量,也不是可运行的程序或批处理文件
//原因是环境变量没配置好

mongodb数据库:负责存储数据
mongodb操作软件:可以进行数据的增删改查操作


1-mongodb数据库的启动:
0.创建数据文件夹,创建一个data文件夹,在data文件夹里面创建一个db文件夹,创建一次就好,第二次打开前,先将data里面的lock给删除掉
1.启动mongodb数据库
找到data所在的文件夹,git bash here,键入mongod --dbpath ./data启动数据库
cmd -> mongod --dbpath ./data
数据库开启之后,窗口不能关,关掉就相当于关闭数据库了
切换盘符命令  d: c: 等等

2-mongodb操作软件
  2.1.打开cmd
  2.2.输入mongo
##cmd里面清屏命令:cls 基于windows
##git bash here里面清屏命令:clear基于linux


##软件的打开顺序
1.启动mongodb数据库, mongod --dbpath ./data
2.启动mongodb操作软件   
	2.1.打开cmd
    2.2.输入mongo 是用来连接和管理数据库的,
      mongo --host 域名 --port 端口(一般数据库不会开启远程权限,不安全)
	2.3.show databases;
```

## 64-通过mongodb数据库软件来进行数据库增删改查操作

```js
数据库相关的概念:
数据库:
数据表:
记录:
字段:

在mongodb中术语有所变化
之前的 表 在mingodb中叫    集合
之前的 记录 在mingodb中叫  文档
之前的 字段 在mingodb中叫  列

1.查看mongodb中所有的数据库
show databases;
2.切换到指定数据库
	use 数据库名称  //如:use admin
3.查看所有的表(集合)
     show collections;
     

当我们给数据库中某个指定的集合插入数据的时候,数据库和集合不需要提前....
##数据库的增删改查操作
注意:在mongodb中,不需要提前先把数据库和表创建出来,直接使用就行了!
  
需求:创建一个alibaixiu数据库出来
#即使数据库不存在,也可以直接进行切换操作
use 数据库名称

##db的说明:
db就是当前正在使用的数据库的对象,可以通过这个对象来给当前前的数据库进行增删改查操作: 
1.给指定的集合中插入数据(-----增)
	db.集合名称.insert(对象)
	db.集合名称.insertOne(对象)
	db.集合名称.insertMany([{},{},{},....]])

	db.users.insert({name:"张三",age:18})
	db.articles.insert({title:"biaoti",contents:123})
2.获取集合中所有的数据(-----查)
    2.1db.集合名称.find()
    如果find不传递任何参数,就是查找所有的数据,如果查询特定条件的数据,需要传入参数
    //需求:查找name为张三的数据
	//查找所有find()或者find({})
    2.2 db.集合名称.find({name:张三});
	2.3 db.集合名称.insert(查询条件)
	查询条件是一个对象,对象的属性名就是要找的数据的字段,对象的属性值就是要找的字段的的值

	##如果要查找年龄大于18岁的人?
  	2.4 db.users.find({age:{$gt:18}});
  
    //$gt 大于
    //$lt 小于
    //$eq 等于
    //$gte大于等于
    //$lte小于等于
    //$ne 不等于
    //$in 在某个数值中
    //$nin不在某个数组中

    ##如果查找年龄为18和19的人
    db.users.find({age:{$in:[18,19]}});
3.删除数据
	db.集合名称.deleteOne(条件对象); //只能删除一条,哪怕是条件可以找到多条数据,只删除一条
	db.集合名称.deleteMany(条件对象); //可以删除多条数据
eg:
	删除所有:
	db.集合名称.deleteMany({})

	db.users.deleteOne({name:张三});
	db.users.deleteMany({name:张三});
	


4.修改数据
db.集合名称.updateOne(条件对象,修改操作对象)
db.集合名称.updateMany(条件对象,修改操作对象)

    4.1修改age为18的人的name为张三
    db.users.updateOne({age:18},{$set:{name:"张三"}});
    通过$set来设置
    4.2修改所有age为17的gender为female
    db.users.updateMany({age:{$gt:17}},{$set:{gender:"female"}});

robot安装(图形化工具操作数据库)
create ->save -> connect
```

## 65-node.js中操作mongodb数据库

```js
//通过node.js代码我们也可以实现mogodb的增删改查操作
//
//需要借用mongodb包,npm i mongodb
访问npmjs.com查看文档
1.引入mongoClient
var MongoClient = require("mongodb").MongoClient;
//var　ObjectID= require("mongodb").objectID;
2.创建连接字符串
var connStr = "mongodb://localhost:27017"
3.调用 MongoClient的connect方法连接数据库
 MongoClient.connect(connStr,function(err,client){
     //4.获取数据库对象db
   var db = client.db("alibaixiu");
   	//5.获取要操作的集合(表)
   var users = db.collection("users");
   //6.进行增删改查操作
        //6.1 获取数据(查)
        users.find({}).toArray(function(err,data){
            console.log(data);
        });//toArray因为是异步操作,需要通过一个回调函数返回
   		##获取指定id对应的数据
        ##id不需要设置,会自动生成
		##在使用id进行查询的时候,需要将字符串id转换成mongodb中的id格式......
        			            users.find({_id:ObjectID("243259234682955uhurheug")}).toArray(function(err,data){
            console.log(data);
        });
        //6.2 新增数据
            //一条数据
        users.insetOne({name:"张三",age:17},function(err,data){
            console.log(data.result);
        })
            //多条数据
        users.insetMany([{name:"张三一号",age:17},{name:"张三二号",age:32}],function(err,data){
            console.log(data.result);
        })
       //6.3 删除数据(多条$in)
        users.deleteOne({name:"zzz"},function(err,data){
           console.log(data.result); 
        })
       users.deleteMany({name{$in["yyy","zzz"]}},function(err,data){
         console.log(data.result); 
       })

       //6.4 修改数据()
        users.updateMany({},{$set:{job:"程序员"}},function(err,data){
         console.log(data.result);
 })
   //7.关闭数据库连接
   client.close();
 })
```

# day06

## 66-用mongodb实现hacker-news中的数据操作(storage.js)

```js
//将hacker-news
//将storage.js和data.json删除掉
//新建storage.js 将里面读取数据和操作数据的方法改写成mongodb写的即可
var MongoClient = require("mongodb").MongoClient
var connStr = "mongodb://localhost:27017";

var　ObjectID= require("mongodb").objectID;

function connectDB(callback) {
     MongoClient.connect(connStr,function(err,client){
          var db = client.db("hackernews");
          var news = db.collection("news");
		callback(news);
        client.close();
      })
}


modules.exports = {
    getAllNews:function(callback){
        //下载mongodb,npm i monogdb
      //MongoClient.connect(connStr,function(err,client){
        //  var db = client.db("hackernews");
        //  var news = db.collection("news");
        //
        //  news.find({}).toArray(function(err,data){
        //      callback(data);
       //   })
       // client.close();
             
      	connectDB(function(news){
           news.find({}).toArray(function(err,data){
           callback(data);
      })
    })
 
  },
     getNewsById:function(id,callback){
         //MongoClient.connect(connStr,function(err,client){
         // var db = client.db("hackernews");
         // var news = db.collection("news");
         connectDB(function(news){
            news.find({_id:ObjectId(id)}).toArray(function(err,data){
            //将html中a href= "<%= /details?if='+list[i]._id %>"  模板引擎读取字符串的一个小bug
            callback(data[0]);
         })

        //  })
        //client.close();
      })
    },
     addNews:function(newNews,callback){                            	//MongoClient.connect(connStr,function(err,client){
//     var db = client.db("hackernews");
		connectDB(function(news){
     	db.news.insertOne(news,function(){
        if(data.result.ok == 1) {
              callback();
          }
      });
    })
//    client.close();              
//    },
}

```

## 67-前后端分离实现hacker-news

### 1-后端程序员-写接口

```js
//1.写接口,文件夹,hacker-news.api.backend->  app.js
//npm init -y
//npm i pxpress
//npm i body-parser
//npm i mongodb
var express = require("express");
var app = express();
var bodyParser =require("body-parser")
app.use(bodyParser.json());
app.use(bodyParser.urlencoded());

//解决跨域问题
app.use(function(req,res,next){
  //进行跨域请求头的方式
  	res.set("Access-Control...")
    req.set("Access-Control")
  	next();
})

var router = require("./router");
app.use(router);

app.listen(9999,function(){
    console.log("http:localhost:9999");
})



//2.新建文件,router.js,将storage.js拷贝粗来
var router = require("express").Router();

var hablder = require("./handler");
//我们要给前端提供数据接口
//1.新闻列表数据局接口
router.get("/api/getnewslsit",handler.listHandler)
//2.新闻详情接口
router.get("/api/getnewsdetail",handler.detailHandler)
//3.添加新闻数据的接口
router.post("/api/addNews",handler.addHandler)

moudule.exports = router()


//3.新建一个文件,handler.js
var storage = require("./storage")

module.exports = {
    listHanlder:function(req,res){
    //res.send("你请求了新闻列表接口");
      storage.gegtAllNews(function(req,res){
          res.send(
          errCode:200,
          msg:"获取数据成功",
          data:newsList
          );
      })
	},
  	detailHanlder:function(req,res){
    //res.send("你请求了新闻详情接口");
      storage.getNewsById(req.query.id,function(){}){
          res.send(
          errCode:200,
          msg:"获取数据成功",
          data:news
          )
      }
	},
  	addHanlder:function(req,res){
    //res.send("你请求了新闻添加接口");
      storages.addNews(req.body,function(){
          errCode:200,
          msg:"获取数据成功",
      })
	}
}
                       
//4.接口文档
##新闻列表接口
功能:获取首页的新闻列表数据
接口地址:http://localhost:9999/api/getnewslist
请求方式:GET 
请求参数:无
返回数据格式:JSON
返回数据实例:

                       
##新闻详情接口
功能:获取首页的新闻详情页数据
接口地址:http://localhost:9999/api/getnewsdetail
请求方式:GET 
请求参数:id<String>
返回数据格式:JSON
返回数据实例:
                       
                       
##新闻添加接口
功能:添加新闻数据
接口地址:http://localhost:9999s/api/addNews
请求方式:POST 
请求参数:title<String>  text<String>  url<String>
返回数据格式:JSON
返回数据实例:   
   {
          errCode:200,
          msg:"获取数据成功",                        
   }                    
```

### 2-前端程序员-静态页面,获取数据

```js
//写一个文件夹hacker-news-frontend
//前端一般都是用http协议,用一个简单服务器访问才不会出问题
git bash here -> live-server
//前端用到jquery art-template
//npm init -y
//npm i jquery
//npm i art-template
//在index.html中写入   :script:src 引入
##首页
<script>
   $(function(){
    $.ajax({
      //如果跨域了,找到后端改成跨域的
      url:"",
      success:function(data){
          console.log(data);
        var html = template('tpl',{list:result.data})
        $("#index").html(html);
        //给td加个id为...
        $("#")...
      }
    })
})
</script>

##详情页
//找到详情页 引入jquery,art-template
<script>
  $(function(){
   //1.获取id
  var id = location.search.spli()[1];
  //2发送ajax请求
  $.ajax({
      url:"",
    data:{id:id}
    success:function(){
        ...
    //id=detail
    ###$data里面直接可以访问到传进来的对象本身
    var html = template('tpl',result.data)
    //将list改成$data,下面将item改成$data
    //var html = template('tpl',{item:result.data})
  	$("#detail").html(html);
  	document.title = result.data.title+" |hacker-news"
  ##通过document.title改标题##
    }
  })
})  
</script>


##添加页
//给按钮注册点击事件
//submit.html里面写
$(function(){
  //submit点击的时候触发
    $("form").submit(function(){
      $.ajax({
          url:"http:///localhost:9999/api/addNews",
          type:"post",
          data:$(this).serialize();//$(this)指的是什么
          success:function(data){
          if(data.errCode == 200) {
          	location.href = "./index.html"
      		}
     	 }	
      })
        reurn false;
    })
})
  
将table挖个坑
<script>
	....
</script>
  
  
<script>
	....
</script>
```

## 68-用node.js去写命令行工具

```js
#! node
//告诉系统用node来执行代码
//创建文件夹:createfolder
var fs  =require("fs");

fs.mkdir("./yyhs",function(){
    //创建文件夹也是异步,成功之后会调用function
  	console.log("创建文件夹成功")
  fs.mkdir("./yyhs/yyh1",function(){
    //创建文件夹也是异步,成功之后会调用function
  	console.log("创建文件夹成功")
})
    fs.mkdir("./yyhs/yyh2",function(){
    //创建文件夹也是异步,成功之后会调用function
  	console.log("创建文件夹成功")
})
    fs.mkdir("./yyhs/yyh3",function(){
    //创建文件夹也是异步,成功之后会调用function
  	console.log("创建文件夹成功")
})
    fs.mkdir("./yyhs/yyh4",function(){
    //创建文件夹也是异步,成功之后会调用function
  	console.log("创建文件夹成功")
})
  
  
})


##使用node.js编写命令行工具
//需要给全局提供一个命令,来调用当前文件夹中的代码
//全局命令 在package.json加个属性:
"bin":{
    "yyhcf":"./idnex.js"
}
//在命令行切换npm use 包名
//npm login
//npm publish
//npm install createfolder -g


##总结
要写命令行工具步骤如下:
1.先编写js文件,在Js文件当中实现响应功能
2.在package.json文件中添加一个属性bin
3.bin属性是一个对象,对象中的属性名就是 最终要使用的全局命令的名字
4.对象中的属性值,最终在执行命令的时候,所要执行的js文件的路径
5.在js文件最上面添加一个#! node 告诉操作系统需要使用node.js来执行这个文件
6.将这个包上传到npm
7.使用全局安装的方式安装这个包
8.在命令行中就可以在使用之前bin中添加命令了


//http:require()//node.js获取网上工具
```

## 69-ES6(ECMScript:2015:6)

```js
ES3和ES5,没有ES4,ES6(2015) ES7
大部分用ES3
ES6新增了一些数组和方法,大部分浏览器都支持ES6
##javaScript的语法规范以及标准
//标准的发展是快于浏览器版本2个的

```
## 70-ES6中变量声明语法

```js
// var 变量名;

// es6中新增了两种声明变量的语法
// 1. 通过关键字let声明
// var a = 10;
// console.log(a);

// if(true){
//     var a = 10;
// }
// console.log(a);

// let a = 10;
// let a = 100;
// 1. let声明变量，不可以重复声明
// console.log(a);
// 2. let声明的变量，有块级作用于

// if(true){
//     let a = 10;
// }
// console.log(a);

// 2. 通过关键字const声明
// const a = 10;
// 1. const声明变量，不可以重复声明
// console.log(a);
// 2. const声明的变量，有块级作用于
// if(true){
//     const a = 10;
// }
// console.log(a);
// 3. const声明的变量, 只能在声明的时候赋值，不能二次赋值！
// const a = 10;
// a = 1000;


// for (let i = 0; i < 10; i++){
//     setTimeout(function () { 
//         console.log(i);
//     }, 0)
// }

const fs = require('fs');
const path = require('path');


```

## 71-ES6属性和方法的编写形式

```js
var name = "张三";
var age = 18;

// var obj = {
//     name: name,
//     age: age
// };

// 属性简化如下:
// 当属性名和要给属性赋值的变量名同名的时候，可以简写
// var obj = {
//     name,
//     age
// }

// console.log(obj);

// var obj = {
//     name,
//     age,
//     sayHello: function () { 
//         console.log('Nice to meet you!');
//     }
// }

// 方法简写如下
// var obj = {
//     name,
//     age,
//     sayHello() {
//         console.log('Nice to meet you!');
//     }
// }

// obj.sayHello();
```

## 72-ES6解构赋值*****

```js
var obj = {
    name:"zxy",
  	age:18
}
var name = obj.name;
var age = obj.age;

//ES6中的解构赋值
var {name:name,age:age} = obj;
var {对象中的属性名:要声明的变量名,对象中的属性名:要声明的变量名} = obj
//如果名字一样
var {name,age} = obj
//如果名字不一样
var {name:name1,age:age1} = obj;
console.log(name,age);

var arr1 = [1,2,[3,4]];
var [num1,num2,[num3,num4]]=arr1;
console.log(num1,num2,num3,num4);

var obj = {
    x : "x",
  	y : "y",
   	z : "z"
}
var {x} = obj
console.log({x});//x

```

## 73-剩余元素(rest element)

```js
var arr = [1,2,3];
var [num1,...num2] = arr;
console.log(num1,num2);//1  [2,3]

#剩余元素只能有一个,并且只能是最后一个!
#剩余元素的作用,就是将剩余的所有的元素全部获取到存放到一个好数组中!
```

## 74-对象的扩展语法

```js
var obj = {
    money : 99999999,
  	name : "lmd"
}
//var person = {}

//for (var   k in obj) {
//  person[k] = obj[k];
//}

//在es6中实现上面的代码的功能,非常便捷
var person = {...obj,age:18,gender:"male"};
//...obj是把obj拆解过后拿过来
console.log(person)
```

## 75-模板字符串

```js
var name = "zsss";
var age = 18;

//var str = "我叫"+name+",我今年"+age+"岁";
//var str = `我叫${name},我今年${age}岁`
var str = `我叫${name}
,我今年${age}岁`


//1-可以进行换行,换行不影响
//2-使用反引号引起来
//3-可以直接访问变量 ${变量名}
console.log(str)
```

## 76-es6中的class关键字**********

```js
//1-在js中没有类的概念,js中创建对象使用的构造函数
function Person(name,age) {
    this.name = name;
  	this.age = age;
}
var p = new Person();

Person.prototype.sayHello = function(){
    conslole.log("hello")
}

//2-在ES6中可以通过class来代替构造函数,class内部还是构造函数实现的
class Person {
  //默认会有一个空的构造函数,如果我们自己写了构造函数,则创建对象的时候调用的就是我们自己写的
    constructor(name,age) {
        this.name = name;
      	this.age = age
    }
  //对象中的方法会直接被添加到原型中!
  sayHello() {
     console.log("hello"); 
  }
}
var p = new Person("刘德华,60");
console.log(p);
p.sayHello()



//静态成员:通过构造函数访问的成员就是静态成员 
#Object.create();
#$.ajax
#each 
#get
//通过static关键字可以为class添加静态成员,类名 静态成员
static sayHi() {
    console.log("hi")
}
//实例成员:通过实例对象访问的成员就是实例成员

```

## 77-ES6通过class关键字实现继承******

```js
function Person(){
    this.name = "lsss";
 	this.age = 50
}
function Student(){
    
}
//Student.prototype = new Person();

var stu = new Student();

//想要继承某个类中的内容,只需要写extends要继承的类名
class Student extends Person {
    constructor(){

      //子类中的构造函数,必须先调用super()才能够执行其他操作
      //super就是父类的构造函数
      super();
      this.stuNo = 10086;
    }
}
var stu = new Student();
console.log(stu.name,stu.age);
```

## 78-借用构造函数继承(继承的是属性,方法,等等)

```js
//继承的主要目的是为了:实现复用
function Person() {
    this.name = "彭于晏";
  	this.age = 18;
}
function Student() {
    Person.call(this);//把这两句代码放到其中执行
}
var stu = new  Student();
console.log(stu);

//call 和 apply
//函数的第四种调用模式,上下文调用模式

//1.调用当前函数
//2.将函数的this指向参数中的第一个
//3.将第二个及以后的参数作为函数实参传入
function test () {
    console.log(this)
}
test.call({name:"zs"},1,1,1);
test.apply([{name:"zs"},1,11,1]);
```

## 79-箭头函数*****

```js
//es6中函数表达式的另外一种写法!
//箭头函数

##所有需要使用函数的地方,都需要使用箭头函数
setTimeout(_ => condole.log(123),1000) //一秒打印123
fs.readFile("./1.txt","utf8",(err,data)=>{
    
})

var test  = function() {
    console.log("test");
}
//箭头函数的基本语法
//(参数列表) => {函数体}
var  test = () => {
    cosole.log("test");
}

test();

//箭头函数的简写形式
//1.如果参数只有一个参数,那么参数的小括号可以省略
var print = (msg) => {
    consolee.log(msg);
}
var print = msg => {
    consolee.log(msg);
}
print("123");

//2.如果函数的函数体只有一句带代码,那么函数体的大括号可以省略
var print = (msg) => {
    
}
//简写
var print = msg => 


//3.如果函数体只有一句代码,并且这句代码是return 语句时,则return关键字和大括号都可以省略
var sum = (a,b) => {
    return a +b;
}
//简写
var sum = (a,b) => a+b

//4.补充说明:小技巧
var func = () => {
    console.log("func函数")
}
var func = _ => {				//_:参数名
    console.log("func函数")
}
```

## 80-箭头函数的注意事项说明******

```js
//1.箭头函数中没有this
	//如果在箭头函数中使用了this,则会沿着作用域链向上查找,找到谁就用谁
	##//这个特性特别好用,所有需要var that = this的地方,都可以使用箭头函数来解决问题


var test = () => {
    console.log(this)
}
test();

var obj = {
        sayHello() {
        var test = () => {
        console.log(this)
    	}
    test();
    }
}
obj.sayHello();//obj


//2.箭头函数中没有arguments(伪数组)
//arguments会将所有的函数调用时,会将所有的函数调用时传入的实参存入一个一个伪数组中
//arguments一般会用在函数的实现个数不确定的情况下
function test(a,b,c) {
    
}
test(1,2,34,4)

var test = () => {
    console.log(arguments);
}
test(1,2,34,3);

//箭头函数中没有arguments,那如果要获取不定个的实参,
//rest arguments 剩余参数!
//rest 参数必须是最后一个参数,并且只能有一个!
//rest 参数是一个真数组,可以使用数组的所有的方法和属性! 
var test = (a,...b) => {
    console.log(a);
    console.log(b);
  	a.forEach(v => {
        console.log(v);
    })
}
test(1,2,34,3);


```

## 81-es6的编译工具babel

```js
//解决es6兼容性问题,
//babel的作用:讲es6转换成低版本的js代码,目的就是为了解决兼容性问题
//babel是一个node.js写出来的编译工具
//用之前需要安装 npm i babel-cli -g
//访问babeljs.cn

1.安装
npm install babel-cli -g

//es6代码要转换成低版本的代码
var test = () => {
    console.log("hello");
}
test();

2.使用
//创建配置文件 .babelrc
//配置文件中,需要制定转码规则
...
babel 要转码的文件 -o 转换之后的文件

3.在使用babel的时候,需要给babel设置转码规则
//presets转码规则,npmjs.com搜索转码规则 babel-presets-env

4.转码规则需要下载
npm i babel-presets-env

//chrom 52支持箭头函数,所以不转
//根据不停配置就行转码

只能把我们的语法转换,es6中新增的具体的方法转换不了
//如果想要babel也将es6中新增的方法,进行兼容性处理,需要用到babel的插件
//MDN
//百度搜索:js 数组 es6 方法
var fskeArr = {
    0:"zsss",
  	1:"lssss",
  	2:"wwwww",
  	3:"dqqqqq",
  	length:4
}
var arr = Array.from(fskeArr)//from把伪数组装成真数组

//npm  install babel-plugin-transform-runtime
//配置,在 babelIrc中加入一个属性,解决伪数组装成真数组问题

TS->TypeScript 这个和es6类似,但是可以把js转成强类型的,转码规则是关键
```

## 82-总结

```js

## mongodb将hacker-news项目改写
只需要改写storage.js模块
这个模块提供三个方法： getAllNews  getNewsById  addNews

## hacker-news前后端完全分离
1. 后端只负责提供数据接口
2. 前端负责静态页面编写以及ajax请求数据，和数据渲染！

如果出现跨域，则需要后端人员协助解决
1. CORS 在响应头中设置对应的内容 (后端人员做)
2. JSONP （后端人员返回JSONP格式数据，前端请求的时候需要使用JSONP的方式请求）
3. 反向代理 （后端人员配置）

## 命令行工具的制作
1. 先编写js文件实现功能
2. 创建package.json文件
3. 在pacakge.json文件中加 bin 属性
4. bin属性是个对象，对象中的属性名 最终要使用的命令名称
5. 属性值，就是使用命令的时候调用的文件的路径
6. 在js文件最顶上加上  #! node  告诉操作系统，需要使用node来执行这个文件
7. 将这个包上传到npm
8. 使用全局安装的方式安装这个包
9. 在命令行中就可以使用之前bin中添加的命令了！

## es6
1. 变量声明语法
​```js
let 变量名;
//let声明变量不可以重复声明
//let声明的变量有块级作用域
const 变量 = 值；
//const声明变量不可以重复声明
//const声明的变量有块级作用域
//只能在声明的时候赋值，不能二次赋值！
​```
2. 对象成员的简写
​```js
let name = "";
let age = 19;

let obj = {
    name,
    age,
    方法名(){

    }
}
​```

3. 解构赋值
​```js
let obj = {
    name: "",
    age: 18
}

let {name, age} = obj;
let {name: name, age: age} = obj;

let arr = [1, 2, 3, 4];
let [num1, num2, num3, num4] = arr;

let arr = [1, 2, 3, 4];
let [num1, , ,num4] = arr;

let arr = [1, 2, 3, 4];
let [num1, ...num4] = arr;
​```

4. 对象的扩展语法
​```js
let obj = {
    name: "",
    money: 9999
}

let person = {...obj, gender: 'male'}
​```

5. 模板字符串
​```js
let name = "";
let age = 18;

let str = `我叫${name}, 我今年${age}岁`
​```

6. class关键字
​```js
class Person{
    constructor(name, age){
        this.name = name;
        this.age = age;
    }
    sayHi(){
        console.log('Hi')
    }
    static sayHello(){
        console.log('Hello')
    }
}
​```

7. class继承
​```js
class Person{
    constructor(name, age){
        this.name = name;
        this.age = age;
    }
    sayHi(){
        console.log('Hi')
    }
    static sayHello(){
        console.log('Hello')
    }
}

class Student extends Person{
    constructor(){
        super();
        this.stuNo = 9527;
    }
    study(){

    }
}

​```

8. 箭头函数
​```js
// 函数表达式的另一种写法
let test = function(){

}

let test = () => {

}

// 1. 当只有一个参数的时候，参数的小括号可以省略
// 2. 当函数体只有一句代码的时候，函数体大括号可以省略
// 3.  当函数体只有一句代码并且这句代码是return语句的时候，函数体大括号可以省略，return关键字也可以省略
​```

9. 箭头函数没有this 也没有 arguments

在箭头函数中使用this的时候，会按照变量的查找规则，沿着作用域链向上查找。

箭头函数中没有this的这个特性，一般被用来解决 `var that = this`的问题


在箭头函数中使用arguments的时候，会按照变量的查找规则，沿着作用域链向上查找。

10. rest参数
​```js
function test(...a){
    console.log(a)
    // a就是剩余参数，他是一个真数组！！！
}

test(1, 2, 3, 4)
​```

## babel
1. 安装
​```
npm i babel-cli -g
​```
2. 使用

2.1 创建配置文件  .babelrc
配置文件中，需要制定转码规则 presets
如果需要进行方法的兼容性处理 则需要配置 plugins

转码规则和插件都需要通过npm来下载！
​```json
{
    "presets": [
        ["env", {
            "targets": {
                "chrome": 40
            }
        }]
    ],
    "plugins": [
        "transform-runtime"
    ]
}
​```

2.2 使用babel命令进行转码
​```
babel 要转码的文件 -o 输出文件
​```
```