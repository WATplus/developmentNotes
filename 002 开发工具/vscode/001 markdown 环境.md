# Vscode 中的 Markdown 环境

## 语法层插件

- Markdown All in One
  - 快捷键自
  - 动生成并更新目录
  - 自动格式化表格
  - LaTeX 数学公式支持
- mardownlint
  - 语法检测
- Markdown Preview Mermaid Support
  - mermaid 的支持

## 编辑扩展插件

- MdTableEditor
  - 提升表格编辑体验
- Auto Markdown TOC By AX1
  - 实现章节自动编号
- Draw.io
  - 绘图工具 , 新建`.drawio` 文件打开即可
- Markdown Notebook
  - 实现所见即所得

## 自动粘贴图片

VSCode 在 2023.05 发布了 1.79 版本，提供了一项名为 Automatic copy of external files 的新功能,可以自动粘贴内容到 markdown 中.

除了图片，新功能还支持音频和视频，会生成 <audio> 和 <vidoe> 的 Markdown 片段。为了简单起见，本文只讲图片。

### 自定义存放目录

由 `markdown.copyFiles.destination` 配置控制图片文件的存放目录。

```json
    "markdown.copyFiles.destination": {
        "/docs/api/**/*": "${documentWorkspaceFolder}/docs/images/"
    }
```

该配置是一个对象，key 使用 Glob 语法，表示匹配的 Markdown 文档；value 则表示所匹配的这些 Markdown 文档，它们的图片文件存放目录，可以使用一些简单的变量。

- `${documentFileName}` — Markdown 文档的完整文件名，比如 `README.md`
- `${documentBaseName}` — Markdown 文档的基本文件名，比如 `README`
- `${documentExtName}` — Markdown 文档的拓展名，比如 `md`
- `${documentDirName}` — Markdown 文档的上级目录名词，比如示例的 `api`
- `${documentWorkspaceFolder}` —  Markdown 文档工作区路径，比如示例的 `/Users/me/myProject`。如果 Markdown 文档不是工作区的一部分，则该值与 `${documentDirName}` 相同
- `${fileName}` — 被拖拽或粘贴的图片文件名，比如 `image.png`

常见的图片存放目录有这两种：

1. 与当前 Markdown 文档同级并新建目录
2. 工作区固定目录统一管理图片

#### 1. Markdown 同级目录（假设为 images）

VSCode 配置：

```json
json
复制代码    "markdown.copyFiles.destination": {
        "**/*": "images/"
    }
```

项目结构

```css
css
复制代码--docs
----api
------images
--------image.png
------README.md
```

markdown 插入内容

```markdown
markdown
复制代码![Alt text](images/image.png)
```

#### 2. 工作区固定目录（假设为 `工作区目录/assets`）

VSCode 配置：

```json
json
复制代码    "markdown.copyFiles.destination": {
        "**/*": "${documentWorkspaceFolder}/assets/"
    }
```

项目结构

```css
css
复制代码--docs
----api
------README.md
--assets
----image.png
```

markdown 插入内容

```markdown
markdown
复制代码![Alt text](../../assets/image.png)
```

## 功能关闭

此项功能默认开启，如果觉得干扰，也可以配置 copyIntoWorkspace 字段进行关闭

```json
json
复制代码// 拖拽行为
"markdown.editor.drop.copyIntoWorkspace": "never"
// 粘贴行为
"markdown.editor.filePaste.copyIntoWorkspace": "never"
```

