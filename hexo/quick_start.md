# Quick Start

在上一节中，我们详细地讲述了 Hexo 的安装方法。在本节中，我们将介绍如何初步搭建自己的博客。

## 创建博客目录

首先先去到你想将博客文件保存到的路径中，打开终端，在终端执行以下命令，Hexo 会在该路径新建所需要的文件。
```
hexo init <folder>  // 初始化文件夹
cd <folder>  // 进入到文件夹中
npm install  // 安装必要的依赖
```
新建完成后，该文件夹的目录如下：
```
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
```

## 常用命令

### init

```
hexo init <folder>
```
新建一个网站。如果没有设置 folder ，Hexo 默认在目前的文件夹建立网站。

### clean

```
hexo clean
```
清除缓存文件 (`db.json`) 和已生成的静态文件 (`public`)。
在某些情况（尤其是更换主题后），如果发现您对站点的更改无论如何也不生效，您可能需要运行该命令。

### generate

```
hexo generate
```
生成静态文件。

### server

```
hexo server
```
启动服务器。在该命令运行后，我们可以访问 `http://localhost:4000/` 地址查看我们博客网站的内容。

对于前三个命令，我们一般是联合使用的。在每次对博客内容进行修改后，我们都会依次运行以上三个命令。有点类似于程序中的 bug 调试。

### deploy

```
hexo deploy
```
将预先生成的静态文件部署到 GitHub 或者其他网站上。
在我们确定博客的内容无误后，我们使用该命令将博客内容部署到 GitHub 或者其他平台上，以便对公众可见。

其他的命令请参考 [官方文档](https://hexo.io/zh-cn/docs/commands)。