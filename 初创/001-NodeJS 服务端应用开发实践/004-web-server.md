# web-server

[toc]

## web服务 的 HTTP 模块

```js
/* 
main.js
*/

// 导入 http 模块
const http = require('http');

const server = http.creatServer((request ,response) => {
    /**
     * 服务的回调函数
     * 
     * @param {object} request 会被计算机传入一个请求对象
     * @param {object} response 会传入一个相应对象
      */

    //  响应写入 Hello
     response.write("Hello , 响应");
    //  结束响应
     response.end();
})

server.listen(3000 , ()=>{
    /**
     * 启动 web 服务的时候调用的回调函数
     * 
     * @param {number} 外部的 listen 函数的第一个参数是端口号
     */

    console.log("^_^ 服务已启动")
})
```

> 通过 `node main.js` 可以开启这个 web 服务
>
> 浏览器访问`localhost:3000` 可以访问这个 web 服务
>
> 打开的页面上有响应内容: `"Hello , 响应"`

### reponse 参数的值

> 可以通过 response 参数获取请求信息

```js
/* 
main.js
*/

const http = require("http");

const server = http.createServer((request ,response)=> {
    // 在收到请求的时候, 输出 request
    console.log(request)
    // 输出 客户端信息
    console.log(request.headers['user-agent'])
    // Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/116.0.0.0 Safari/537.36 Edg/116.0.1938.81
    response.write("你好");
    response.end();
});

server.listen(3000 , ()=>{
    console.log("^_^ 服务已开启");
})
```

### response 响应 实例

> 响应一个 html

```js
/* 
main.js
*/
const http = require("http");

const server = http.createServer((request, response) => {

    // 需要通过响应头告诉计算机相应的 html , 浏览器才能正确的处理
    response.writeHead(200, {
        'Content-Type': 'text/html',
    })
    // 响应一个 html 代码
    response.write('<input type="button" value="点击">');
    response.end();
});

server.listen(3000, () => {
    console.log("^_^ 服务已开启");
})

```

## 请求地址改变相应实例

```js
const http = require("http");

const server = http.createServer((request, response) => {
    /**
     * TODO: 根据请求的地址 , 响应不同内容
     */
    switch (request.url) {
        case "/":
            response.write("Hello");
            break;
        case "/pasts":
            response.write("pasts");
            break;
        default:
            response.writeHead(404);
            response.write("404");
            break;
    }
    response.end();
});

server.listen(3000, () => {
    console.log("^_^ 服务已开启");
})
```

## JSON 格式数据

- 对象 JSON

```json
{
    "id" : 1,
    "title" : "关山月",
    "content" : "明月出天山 , 苍茫云海间"
}
```

- 列表 JSON

```json
[
    {
        "id" : 1,
        "title" : "关山月",
        "content" : "明月出天山 , 苍茫云海间"
    },
    {
        "id" : 2,
        "title" : "eee",
        "content" : "aaaa,bbbb"
    }
]
```

### 响应 JSON 数据

```js
/* 
main.js
*/
const http = require("http");

const server = http.createServer((request, response) => {
    const data = {
        id: 1,
        title: "关山月",
        content: "明月出天山 , 苍茫云海间"
    }

    const jsonData = JSON.stringify(data);

    2
    response.writeHead(200, {
        "Content-Type": "application/json; charset=utf-8"
    });
    response.write(jsonData)

    response.end();
});

server.listen(3000, () => {
    console.log("^_^ 服务已开启");
})

```
