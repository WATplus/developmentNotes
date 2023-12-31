# 内容回顾

## 一. 伪元素

### 1.1. ::first-line/first-letter(了解)

- 给首行文本/首字母文本设置属性

### 1.2. ::before/after

- 插入内容图片等
- 方格

   - content不能省略
   - width/height
   - display

## 二. 继承-层叠-元素类型

### 2.1. CSS属性继承

- 继承: 如果我们给某一个元素设置了某个CSS属性, 而该属性具有继承性, 那么该元素的所有子元素会默认继承该属性.
- 有哪些继承属性? 不需要记

   - 一般和文本/字体相关的很多属性都具备继承;
   - 多查文档

### 2.2. CSS属性层叠

- 一个CSS属性可以多次设置:

   - 判断一: 权重, 优先级;
   - 判断二: 先后顺序;
- 常见的选择器:

   - !important -> 10000
   - 内联 -> 1000
   - id -> 100
   - 类/伪类/属性 -> 10
   - 元素 -> 1
   - 统配 -> 0

### 2.3. 元素的类型

- div -> 块级元素
- span -> 行内级
- 有本质的区别 -> display: block
- span -> 块级
- div -> 行内级

display:

- block

   - 独占一行(父元素)
   - 可以设置宽度和高度
   - 默认高度是内容的高度
- inline-block

   - 和其他行内级元素在同一行显示
   - 可以设置宽度和高度
   - 默认宽高由内容决定
- inline

   - 和其他行内级元素在同一行显示
   - 不能设置宽度和高度
   - 宽高由内容决定

### 2.4. 元素的隐藏方法

- display: none

   - 不占用空间
- visibility: hidden

   - 占用空间
- rgba -> alpha
- opacity -> 设置透明度

   - 所有的子元素都会跟着一起设置

### 2.5. overflow

- visible 默认可见
- hidden 隐藏
- scroll 滚动条
- auto 自动控制滚动条

### 2.6. HTML嵌套的规范

- 块级/行内块级可以嵌套其他元素
- p元素不能嵌套div元素
- 行内级元素不能嵌套块级元素

## 三. 盒子模型

### 3.1. 认识盒子模型

- 照片墙
- HTML元素都是盒子
- 盒子模型组成属性:

   - content
   - padding
   - border
   - margin

### 3.2. content

- width/height
- width: auto
- min-width/max-width

### 3.3. padding

内边距:

- 四个方法
- padding

   - 4/3/2/1

### 3.4. border

边框

- width
- style
- color

```css
div {
  border: 10px solid red;
}
```

### 3.5. border-radius

圆角:

- 具体的值, 比如6px
- 百分比 -> border box(了解)

   - 50%
