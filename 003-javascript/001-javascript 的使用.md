
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
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```

- 代码执行的时候依旧会阻塞页面的加载
- 代码执行的时候并不会等待
