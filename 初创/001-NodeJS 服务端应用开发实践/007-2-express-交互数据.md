# 交互数据

[toc]

## HTTP 客户端接口测试

- 在编写服务端的时候 , 如果需要测试接口 , 但是服务端还没有完成
- 可以使用*postman* 或者 *Insomina*等接口测试服务软件进行

- *Insomina* 下载 , 网站: [insomina.rest](https://insomnia.rest)

### 基本使用

- 在`PROJECT`中创建自己的项目
- 在`ALL File`中的`Collections`中添加自己的测试请求
- 定义名字以及请求方法
- 在右侧顶部配置请求的地址
- 点击`send`按钮可以在右侧显示服务器响应的数据

### 环境配置

- 在 `base environment`旁边的设置按钮中可以添加`sub environment`
- 接收 JSON 格式的数据 ,通常用来配置一些在多个接口中都会重复的东西

```json
/* 
开发环境的配置
*/

{
 "xb2": "http://localhost:3000"
}
/* 
生产环境的配置
*/
{
 "xb2": "https://xb2-node.api.watplus.com"
}
```

- 这样就可以在设置接口的时候 , 将已经配置的地址使用对应的变量代替 `http://localhost:3000/posts`就可以写为`_.xb2/posts`
- 在切换环境的时候 , 变量存储的值也会随之变化

## 应用资源接口

```js
app.get()
app.post()
app.put();app.patch()
app.delete()
```

### 创建内容的接口

```js
/* 
创建内容
*/
app.post("/posts", (request, response) => {
 // 结构请求头内的content
 const { content } = request.body;

 // 设置相应状态码
 response.status(201);
 // 响应回去
 response.send({
  "message": `请求成功: ${content}`
 })
})
```

- 可以通过 insomnia 测试
  - 创建一个新的post 请求 , 设置 body 属性
  - 进行请求 , 在 Preview 中查看响应

> **request.body()为空的解决方案**
>
> 是因为缺少`body-parser`中间件 , 通过`npm install body-parser` 安装 , 在主程序中添加下面的代码
>
> ```python
>   var bodyParser = require('body-parser')
>   app.use(bodyParser.urlencoded({ extended: false }))
>   app.use(bodyParser.json())
> ```

## 头部数据

- 请求和响应的时候除了可以携带请求主体还可以有头部数据
- 可以用于携带一些用户信息之类的

### 服务端获取客户端的请求头

- insomnia 中点击`hreaders`可以设置请求头用于测试
- express 获取请求头中的数据

```js
app.post("/posts", (request, response) => {
 // 结构请求头内的content
 const { content } = request.body;
 // 获取请求头中的测试信息
 const header = request.headers["test-header"]
 // 设置相应状态码
 response.status(201);
 // 响应回去
 response.send({
  "message": `请求成功: ${content}`,
  "header": {
   "test-header": header,
  }
 })
})
```

### 响应的头

- 通过`response.set()`设置

```js

```
