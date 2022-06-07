# Git 快速指南

## 安装并克隆第一个仓库

### 安装

在使用 Git 前，我们需要确保自己的电脑已经安装好 Git。
Git 官方下载地址为：http://git-scm.com/downloads
具体的安装步骤可参考 Git 详细指南。

在终端输入命令 `git` ，若出现如下提示则证明安装成功。
![](quick_guide_asset/Xnip2022-06-07_22-51-20.jpg)

### 克隆第一个仓库

首先我们需要去到我们的 GitHub 仓库，复制 URL。
![](quick_guide_asset/Xnip2022-06-07_22-55-36.jpg)
在 2021.08.13 之后，输入账号密码的方式来向 Github 仓库提交代码等行为不再被支持。我们必须使用 Personal access token 的方式来替代。因此我们需要生成一个 token 以便我们能将 GitHub 中的仓库克隆到本地。我们去到 Settings 中找到 Developer settings。点击 Generate new token。
![](quick_guide_asset/Xnip2022-06-07_22-59-08.jpg)
在 Note 这一栏输入这个 token 的用途。
![](quick_guide_asset/Xnip2022-06-07_23-02-48.jpg)
Expiration 是这个 token 的有效期，我们可以根据具体的需求设置。为了方便起见，我们直接勾选所有的 scope，然后点击 Generate token。
![](quick_guide_asset/Xnip2022-06-07_23-04-22.jpg)
生成好 token 后，我们必须第一时间将其复制保存，因为它只向我们展示一次，之后我们是不能再次查看的。

在我们有了仓库的 URL 和 token 后，我们需要将两者按以下规则拼接在一起。
```
https://oauth2:token@github.com/username/xxx.git
```
其实就是在 URL 中插入 `oauth2:token@` 。接着我们在终端运行一下命令：
```
git clone https://oauth2:token@github.com/username/xxx.git
```
如果一切顺利，我们就可以在你打开终端的目录中看到与你仓库同名的文件夹。
![](quick_guide_asset/Xnip2022-06-07_23-17-47.jpg)