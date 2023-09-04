# 002 基本标签-HTML 结构

## 文档声明

- `**<!DOCTYPE html>**`**是文档类型的声明 **
   - 并不是一个标签  
- **需要写在整个 HTML文档的第一行 **
   - 用来告诉告诉计算机这个页面要按照 HTML5 页面进行渲染
## 
## <html> 元素

- 作为整个网页的**根元素** , 包裹所有元素
- 通常会书写一个`**lang=""**`**的属性**,来标明这个网页的**语言**
   - `lang="en"`英文网页
   - `lang = "zh"` 中文网页
      - `**lang="-zh-CN"**`**中国大陆的中文**
      - `zh-hant` 繁体中文
      - `zh-hans`简体中文
### 
### <head> 元素

- 通常用来包裹页面的配置元信息 , 常见的子标签有:
   - `meta`
   - `title`
- **配置网页字符集**
   - `<meta charset = "UTF-8">`
- **网页标题**
   - `<title>caption</title>`
### 
### body 元素

- 存放用户在也页面上真正看得见的元素
- 常见元素 : [003 基础标签-常见基本元素](https://www.yuque.com/babailiqiuzhuyueye/vss305/obgk25kdvo3o9724)
