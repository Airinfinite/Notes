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

## Git 工作流程及基本概念

### 工作流程

Git 的一般工作流程如下：
1. 将远程仓库克隆到本地
2. 从克隆的本地仓库中检出一条分支到工作区，对分支进行修改
3. 在我们对分支修改完成后，先将其添加到本地缓存区
4. 添加到本地缓存区后，我们可以提交修改后的分支到本地仓库
5. 最后，我们可以将本地仓库推送到远程仓库
![](quick_guide_asset/Xnip2022-06-08_07-53-37.jpg)

### 基本概念

* Remote 是远程仓库，常用的有 GitHub、Gitee 等。
* `clone`：将远程仓库克隆到本地仓库。
* Repository 是本地仓库，也就是版本库，工作区的 `.git` 文件夹。在这里存放着我们代码的各个历史版本。
* `checkout`：从本地仓库中检出一个分支然后进行修改。
* `workspace`：工作区，也就是我们能直接看得见的文件夹。
* `add`：在提交代码前，现将代码添加到暂存区。
* Index 一般存放在 `.git` 目录下的 index 文件（.git/index）中，所以我们把暂存区有时也叫作索引。
* `commit`：将我们添加到暂存区的代码提交到本地仓库。
* `push`：将本地仓库推送到远程仓库。

## 创建仓库

在这里，我们将介绍如何创建 Git 仓库。主要有以下两种方式：
1. 在本地创建 Git 仓库
2. 将远程仓库克隆到本地

### 在本地创建 Git 仓库 —— git init

Git 使用 `git init` 命令来初始化一个 Git 仓库，Git 的很多命令都需要在 Git 的仓库中运行，所以 `git init` 是使用 Git 的第一个命令。
在执行完成 `git init` 命令后，会在当前文件夹 生成一个 .git 目录，也就是本地仓库。

#### 使用方法

使用当前目录作为 Git 仓库，我们只需使它初始化。
```
git init
```
该命令执行完后会在当前目录生成一个 .git 目录。
或者我们可以指定特定目录作为 Git 仓库。
```
git init [newrepo]
```
初始化后，会在 newrepo 目录下会出现一个名为 .git 的目录，所有 Git 需要的数据和资源都存放在这个目录中。
如果当前目录下有几个文件想要纳入版本控制，需要先用 `git add` 命令告诉 Git 开始对这些文件进行跟踪，然后提交：
```
$ git add *.c
$ git add README
$ git commit -m '版本说明'
```
以上命令将目录下以 .c 结尾及 README 文件提交到仓库中。

### 将远程仓库克隆到本地 —— git clone

我们使用 `git clone` 从远程 Git 仓库中拷贝项目。克隆仓库的命令格式为：
```
git clone [repo]
```
如果我们需要克隆到指定的目录，可以使用以下命令格式：
```
git clone [repo] [directory]
```
参数说明：
1. repo：远程 Git 仓库
2. directory：本地目录

比如，要克隆 Ruby 语言的 Git 代码仓库 Grit，可以用下面的命令：
```
git clone git://github.com/schacon/grit.git
```
执行该命令后，会在当前目录下创建一个名为 grit 的目录，其中包含一个 .git 的目录，用于保存下载下来的所有版本记录。
如果要自己定义要新建的项目目录名称，可以在上面的命令末尾指定新的名字：
```
git clone git://github.com/schacon/grit.git mygrit
```

## 基本操作

Git 的工作就是创建和保存你项目的快照及与之后的快照进行对比。本章将对有关创建与提交你的项目快照的命令作介绍。
Git 常用的是以下 6 个命令：`git clone`、`git push`、`git add`、`git commit`、`git checkout`、`git pull`，接下来我们将一一介绍。
![](quick_guide_asset/2022-06-08-10-01-01.png)

### 创建仓库命令

#### git init

`git init` 命令用于在目录中创建新的 Git 仓库。
在目录中执行 `git init` 就可以创建一个 Git 仓库了。
例如，我们在当前目录下创建一个名为 note 的项目：
```git
mkdir note
cd note/
git init
# Initialized empty Git repository in ~/Desktop/note/.git/
```
现在你可以看到在你的项目中生成了 .git 这个子目录，这就是你的 Git 仓库了，所有有关你的此项目的快照数据都存放在这里。

#### git clone

`git clone` 拷贝一个 Git 仓库到本地，让自己能够查看该项目，或者进行修改。拷贝项目命令格式如下：
```
git clone [URL]
```
URL 是我们要拷贝的 GitHub 上的项目。

默认情况下，Git 会按照你提供的 URL 所指向的项目的名称创建你的本地项目目录。通常就是该 URL 最后一个 / 之后的项目名称。如果你想要一个不一样的名字，你可以在该命令后加上你想要的名称。
```
git clone [URL] [reopname]
```
reponame 就是你想要自定义的名字。

### 提交与修改

#### git add

`git add` 命令可将该文件添加到暂存区。

添加一个或多个文件到暂存区：
```
git add [file1] [file2] ...
```
添加指定目录到暂存区，包括子目录：
```
git add [dir]
```
添加当前目录下的所有文件到暂存区：
```
git add .
```

#### git commit

`git commit` 命令将暂存区内容添加到本地仓库中。
提交暂存区到本地仓库中:
```
git commit -m [message]
```
message 可以是一些备注信息。
提交暂存区的指定文件到仓库区：
```
git commit [file1] [file2] ... -m [message]
```

### 远程操作

#### git push

`git push` 命令将本地的分支版本上传到远程并合并。命令格式如下：
```
git push <远程主机名> <本地分支名>:<远程分支名>
```
如果本地分支名与远程分支名相同，则可以省略冒号：
```
git push <远程主机名> <本地分支名>
```

##### 实例

以下命令将本地的 master 分支推送到 origin 主机的 master 分支。
```
git push origin master
```
相等于：
```
git push origin master:master
```

#### git pull

`git pull` 命令用于从远程获取代码并合并本地的版本。
`git pull` 其实就是 `git fetch` 和 `git merge FETCH_HEAD` 的简写。命令格式如下：
```
git pull <远程主机名> <远程分支名>:<本地分支名>
```

##### 实例

将远程主机 origin 的 master 分支拉取过来，与本地的 brantest 分支合并。
```
git pull origin master:brantest
```
如果远程分支是与当前分支合并，则冒号后面的部分可以省略。
```
git pull origin master
```
