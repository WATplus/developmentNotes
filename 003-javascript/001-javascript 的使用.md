
# 使用 javascript

## 通过 `<script>` 标签使用 JavaScript 程序

```html
<body>
  <!-- 页面内容 -->
  <script>
    function hello(){
      alert("hi");
    }
  </script>
</body>
<body>
  <!-- 页面内容 -->
  <script src="hello.js"> </script>
</body>
```

## `<script>` 的常用属性

- `src` 执行外部的脚本文件
- `async` 代码的加载不会影响页面的加载 , 代码加载完毕之后也不会等待其他脚本文件, 会直接运行(运行过程中是阻塞页面加载的)
- `defer` 代码加载不会影响页面的加载 , 页面加载完毕后再开始按照顺序执行代码
- `type` 用来代替`language`属性的 , 一般填写`text/javascript` 即可

## 异步代码

```html
<body>
 <script src="相对较大的文件.js"></script>
 <script src="相对较小的文件.js"></script>
  <!-- 页面内容 -->
</body>
```

- async属性添加之后代码的执行顺序如下

```mermaid
sequenceDiagram

participant 文档开始加载
participant 较小脚本加载完毕
participant 较小脚本执行完毕
participant 较大脚本加载完毕
participant 较大脚本执行完毕
participant 文档加载结束

文档开始加载 ->> 较小脚本加载完毕 : 较小脚本加载
较小脚本加载完毕 --> 较小脚本执行完毕 : 较小代码执行

文档开始加载 ->> 较大脚本加载完毕 : 较大脚本加载
较大脚本加载完毕 --> 较大脚本执行完毕 : 较大脚本执行

文档开始加载 ->> 较小脚本加载完毕 : 页面 DOM 加载
较小脚本执行完毕 ->> 较大脚本加载完毕 : 页面 DOM 加载
较大脚本执行完毕 ->> 文档加载结束 : 页面 DOM 加载
```

- 代码执行的时候依旧**会阻塞页面的加载**
- 代码执行的时候并不会等待其他脚本加载完成
- 所以使用`async` 属性的脚本尽量不做任何`DOM` 处理 ,不要与其他的脚本有联系

## 延时脚本

- 给`<script>` 标签添加`defer`属性可以使所有的脚本加载不阻塞页面的加载 ,
- 脚本加载完毕之后不会立即执行 , 会等到页面加载完毕之后, 按照出现的顺序执行

```html
<body>
 <script src="相对较大的文件.js"></script>
 <script src="相对较小的文件.js"></script>
  <!-- 页面内容 -->
</body>
```

```mermaid
sequenceDiagram

代码开始加载 ->> 较小代码加载完毕 : 较小代码加载
代码开始加载 ->> 较大代码加载完毕 : 较大代码加载
代码开始加载 ->> 页面加载完毕 :  DOM 加载
页面加载完毕 -->> 第一个出现的代码执行完毕 : 较大代码执行
第一个出现的代码执行完毕 -->> 第二个出现的代码执行 : 较小代码执行

```

> 不过不是所有的浏览器都能够正确的处理 `defer`  , 遇到问题时可以将`defer`的`<script>` 标签也放在`<body>`的最后

## 禁用 script 后显示的内容

- `<noscript> </noscript>` 标签对内可以包含除了`<script>` 之外的所有标签
- 默认不会显示 , 如果当前浏览器的 javascript 被禁用 , 就会显示出来

```html
<html>
  <head>
    <title>Document</title>
  </head>
  <body>
    <p>常规显示的内容</p>
    <noscript>
      <strong>请解除 javascript 禁用后继续使用</strong>
    </noscript>
  </body>
</html>
```

> 但是如果 javascript 脚本已经执行完毕 , 再禁用页面的 javascript 脚本 , `<noscript>` 也不会显示
