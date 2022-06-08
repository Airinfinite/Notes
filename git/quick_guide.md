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
在 2021.08.13 之后，输入账号密码的方式来向 GitHub 仓库提交代码等行为不再被支持。我们必须使用 Personal access token 的方式来替代。因此我们需要生成一个 token 以便我们能将 GitHub 中的仓库克隆到本地。我们去到 Settings 中找到 Developer settings。点击 Generate new token。
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

到这里，我们就完成了 Git 的安装，并且已经会将自己 GitHub 中的仓库克隆到本地。下面，我们将简单介绍一下 Git 的工作流程，以便让我们能在使用 Git 上得心应手。

## Git 工作流程

Git 的一般工作流程如下：
1. 将远程仓库克隆到本地
2. 从克隆的本地仓库中检出一条分支到工作区，对分支进行修改
3. 在我们对分支修改完成后，先将其添加到本地缓存区
4. 添加到本地缓存区后，我们可以提交修改后的分支到本地仓库
5. 最后，我们可以将本地仓库推送到远程仓库
![](quick_guide_asset/Xnip2022-06-08_07-53-37.jpg)

## 基本概念

* Remote 是远程仓库，常用的有 GitHub、Gitee 等。
* `clone`：将远程仓库克隆到本地仓库。
* Repository 是本地仓库，也就是版本库，工作区的 `.git` 文件夹。在这里存放着我们代码的各个历史版本。
* `checkout`：从本地仓库中检出一个分支然后进行修改。
* `workspace`：工作区，也就是我们能直接看得见的文件夹。
* `add`：在提交代码前，现将代码添加到暂存区。
* Index 一般存放在 `.git` 目录下的 index 文件（.git/index）中，所以我们把暂存区有时也叫作索引。
* `commit`：将我们添加到暂存区的代码提交到本地仓库。
* `push`：将本地仓库推送到远程仓库。