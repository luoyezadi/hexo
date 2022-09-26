
<div align="center">
<h1>Hexo 快速入门</h1>
</div>

## 简介

[Hexo] 是一款基于 `Node.js` 的静态博客框架，依赖少易于安装使用，同时拥有着众多插件和主题，支持 Git、云主机、对象存储等方式部署发布。

Hexo 使用 Markdown 语法进行编写，支持常见的 [Markdown](https://daringfireball.net/projects/markdown/) 语法。

## Hexo 官网和常见资料

> 官网：[https://hexo.io/](https://hexo.io/)
> 文档：[https://hexo.io/zh-cn/docs/](https://hexo.io/zh-cn/docs/)
> 主题：[https://hexo.io/themes/](https://hexo.io/themes/)
> 插件：[https://hexo.io/plugins/](https://hexo.io/plugins/)

## Hexo 常见命令

在日常使用中，Hexo 常见的动作有：创建文章、编写 Markdown 内容、调试、发布等。Hexo 发布了完整的文档。可以通过访问 [https://hexo.io/zh-cn/docs/commands](https://hexo.io/zh-cn/docs/commands) 进行了解。
以下为 Hexo 常用的命令介绍：

### 新建网站

新建一个网站。如果没有设置 folder ，Hexo 默认在目前的文件夹建立网站。

```bash
hexo init [folder]
```

### 新建文章
```bash
hexo new [layout] <title>
```
> 新建一篇文章。如果没有设置 layout 的话，默认使用 _config.yml 中的 default_layout 参数代替。如果标题包含空格的话，请使用引号括起来。

### 静态文件生成

```bash
hexo generate  # 简写：hexo g
```

> Hexo 引入了差分机制，如果 public 目录存在，那么 hexo g 只会重新生成改动的文件。
该命令可以简写为



### 发表草稿
```bash
hexo publish [layout] <filename>
```


### 启动本地服务

启动服务器。默认情况下，访问网址为： http://localhost:4000/。

```bash
hexo server  # 简写：hexo s
```

### 部署网站

```bash
hexo deploy  # 简写：hexo d
```


### 渲染文件

```bash
hexo render <file1> [file2] ...
```

### 迁移内容

```bash
hexo migrate <type>
```

### 清除缓存

清除缓存文件 (db.json) 和已生成的静态文件 (public)。

```bash
hexo clean
```

> 在某些情况（尤其是更换主题后），如果发现您对站点的更改无论如何也不生效，您可能需要运行该命令。

### 查看网站信息

通过 list 命令，可以很方便的查看站点下的各项内容如：文章、单页、分类、标签等。

```bash
hexo list <type>
```

> `<type>` 参数为枚举类型，具体的只可以是：`page`/`post`/`route`/`tag`/`category`


### 查看 Hexo 版本

```bash
hexo version  # 显示 Hexo 版本
```

### 模式选项
#### 安全模式

在安全模式下，不会载入插件和脚本。当您在安装新插件遭遇问题时，可以尝试以安全模式重新执行。

```bash
hexo --safe
```


#### 调试模式

在终端中显示调试信息并记录到 debug.log。当您碰到问题时，可以尝试用调试模式重新执行一次。

```bash
hexo --debug
```

#### 简洁模式

```bash
hexo --silent
```

#### 显示草稿

显示 source/_drafts 文件夹中的草稿文章。

```bash
hexo --draft
```


[Hexo]:https://hexo.io
