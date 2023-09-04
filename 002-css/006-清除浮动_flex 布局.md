# 内容回顾

## 一. 浮动float

### 1.2. 清除浮动

```css
伪元素:after
```

```css
.clear_fix::after{
    content:"";
    display:block;
    clear:both;

    /* 浏览器兼容 */
    visibility:hidden;
    height:0;
}
.clear_fix{
    *zoom:1: /*IE67兼容性*/
}
```

### 1.3. 多种布局对比

- 标准流
- 定位
- 浮动

## 二. flex布局

### 2.1. 认识flex布局

### 2.2. flex布局重要的概念

- flex container

   - flex 的容器
- flex item

   - flex 容器的直接子元素
- main axis/cross axios

   - 主轴/交叉轴
- main start/main end/cross start / cross end

   - 主轴的开始位置 . 主轴的结束位置
   - 交叉轴的开始位置 , 交叉轴的结束位置

### 2.3. flex container中的属性

- flex-direction:

   - 设置主轴方向
   - row
   - row-reverse
   - column
   - column-reverse
- flex-wrap

   - 控制换行
   - nowrap 不换行
   - wrap 换行
   - wrap-reverse 沿着 cross axis 反方向换行
- flex-flow

   - flex-wrap 和 flex-direction 的缩写属性

> [flex-flow 相关属性实现实现的 4 边布局](<codes/flex-flow 实现的布局方式/index.html>)


- justify-content

   - flex-start
   - flex-end
   - space-between

      - 优先往 main start 和 main end 放置 , 其他元素等分
   - **space-around**

      - **元素之间等分, 两端元素与边界的距离之和等于元素之间的距离**
   - space-evenly

      - 元素之间元素与边界之间都等分

> [justify-content 的实例:](<codes/justify 的实例/index.hsa'stml>)


- align-items

   - flex items 在 cross axis 中对齐的方式
   - normal  默认值 弹性盒子中默认 与 search 相同
   - stretch

      - 如果 flex item 在 cross axis 方向上的尺寸为 auto 的时候会自动拉伸至填充 flex container
   - flex-start

      - cross axis start 对齐
   - flex-end

      - cross axis end 对齐
   - center

      - 居中对齐
   - baseline

      - 基线对齐

> [align-items 实例:](<codes/align-items 实例/index.html>)


- align-content

   - 决定 cross axis 上的每一行内容之间的对齐方式
   - space-between
   - space-round
   - space-evenly
   - flex-start
   - flex-end
   - **在 flex container 不设置高度的时候 , flex items 的各行内容会仅仅排列 , 只有在有多余空间的时候才需要设置 align-content 属性**

> align-content 实例[Title](<codes/align-content 实例/index.html>)


### 2.4. flex item中的属性

- order

   - 传递一个数字
   - order属性更大的 flex item 排列的更靠近 main axis start
- align-self

   - 控制一个 flex item 在 cross axis 上的对齐状态
- flex-grow

   - 控制一个flex item 在 flex container 中再有剩余空间时自动变大这个空间的几分
- flex-shrink

   - 控制一个flex item 在 flex container 中空间不足时自动变缩小这个空间的几分
- flex-basis

   - 默认宽度 , 与 width 不同的是 , width 会把宽度写死
   - `flex-basis`容器中如果设置的值不能完整的显示某个单词 , 就会自动变大
- flex

   - `flex-grow flex-shrink flex-basis`的缩写属性
   - 一个值

      - 有单位 : `flex-basis`
      - 无单位 : `flex-grow`
   - 两个值

      - 有单位 : `flex-basis`/ `flex-grow`
      - 无单位 : `flex-grow`

### 2.5. flex布局中justify-content最后一行布局问题

- 通常`justify-content`会设置为类似`space-between`的值 , 最后一行往往对齐方式不是我们想要的
- 添加数个没有高度`span`元素(数量是列数-2) ,span 也会乱排序 , 但是由于元素无高度 , 看不见

> 实例:[Title](<codes/justify-content 最后一行的对齐问题/index.html>)

