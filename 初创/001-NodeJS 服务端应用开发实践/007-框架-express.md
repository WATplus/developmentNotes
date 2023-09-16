# 应用框架(express)

[toc]

## 安装 express

```zsh
npm install express@4.17.1 # 安装指定版本的包
```

## 创建 web 服务器

```js
/* 
main.js
*/

const express = require('express');
const app = express();
const port = 3000;

app.listen(port, () => {
 console.log("^_^ 服务已启动");
})
```

## 应用接口 API

- 可以通过接口使用服务端的功能
- 服务端的接口都会有地址 , 客户端可以访问**对应的地址调用对应的功能**
- 接口是客户端的概念 ,这个"接口"在服务端称之为**路由**(Routor/Route)
- 都需要**被特定的 HTTP 方法使用**'
- **接口处理器** 一个函数 , 服务端可以在接收到请求的同时接受地址 , 根据地址分辨执行哪一个接口 , 执行具体的处理器

### 定义一个接口

```js
/* 
main.js
*/
// 定义一个通过 HTTP 的 get方式访问时的接口
app.get("/", (request, response) => {
 response.send("你好");
})
```

> `/` 是借口的地址
>
> `.get()`是指通过 get 方式请求的
>
> `.send()` 设置了响应信息

### 数据响应

```js

const data = [{..},{..},{..}] // 定义了数据

app.get("/posts", (request, response) => {
 response.send(data)
})
```

> express 会自动的判断相应的类型并自动加上响应头文件
>
> 所以这里即使没有通过 stringify 转换 , 响应的也是 JSON 格式的文件
>
> 响应头也包含 'Content-Type:application/json; charset=utf-8'

### 带参数的接口

- 地址中可以设置参数
- 参数使用`:`开头
- 可以有多个  , `/` 分隔就行
- 参数存储在`request`中的`params`字段中 , 可以直接通过解构获得

```js
/* 
main.js
*/

// 带参数的接口
app.get("/posts/:postsId", (request, response) => {
 // 获取参数
 const { postsId } = request.params;

 // 过滤出 id 对应的项
 const posts = data.filter(item => item.id == postsId);

 // 响应
 response.send(posts);
})
```

> 例如访问`posts/1`时 1 就会作为 postsId 参数被传入
