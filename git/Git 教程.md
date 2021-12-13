# Git 教程

![Git 教程](https://www.runoob.com/wp-content/uploads/2015/02/f7246b600c338744a9591cd7530fd9f9d62aa0f8.png)

Git 是一个开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。

Git 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件。

Git 与常用的版本控制工具 CVS, Subversion 等不同，它采用了分布式版本库的方式，不必服务器端软件支持。

------

## Git 与 SVN 区别

Git 不仅仅是个版本控制系统，它也是个内容管理系统(CMS)，工作管理系统等。

如果你是一个具有使用 SVN 背景的人，你需要做一定的思想转换，来适应 Git 提供的一些概念和特征。

Git 与 SVN 区别点：

- **1、Git 是分布式的，SVN 不是**：这是 Git 和其它非分布式的版本控制系统，例如 SVN，CVS 等，最核心的区别。

- **2、Git 把内容按元数据方式存储，而 SVN 是按文件：**所有的资源控制系统都是把文件的元信息隐藏在一个类似 .svn、.cvs 等的文件夹里。

- **3、Git 分支和 SVN 的分支不同：**分支在 SVN 中一点都不特别，其实它就是版本库中的另外一个目录。

- **4、Git 没有一个全局的版本号，而 SVN 有：**目前为止这是跟 SVN 相比 Git 缺少的最大的一个特征。

- **5、Git 的内容完整性要优于 SVN：**Git 的内容存储使用的是 SHA-1 哈希算法。这能确保代码内容的完整性，确保在遇到磁盘故障和网络问题时降低对版本库的破坏。

  

![Git 安装配置

在使用Git前我们需要先安装 Git。Git 目前支持 Linux/Unix、Solaris、Mac和 Windows 平台上运行。

Git 各平台安装包下载地址为：http://git-scm.com/downloads

------

## Linux 平台上安装

Git 的工作需要调用 curl，zlib，openssl，expat，libiconv 等库的代码，所以需要先安装这些依赖工具。

在有 yum 的系统上（比如 Fedora）或者有 apt-get 的系统上（比如 Debian 体系），可以用下面的命令安装：

各 Linux 系统可以使用其安装包管理工具（apt-get、yum 等）进行安装：

### Debian/Ubuntu

Debian/Ubuntu Git 安装命令为：

```
$ apt-get install libcurl4-gnutls-dev libexpat1-dev gettext \
  libz-dev libssl-dev

$ apt-get install git

$ git --version
git version 1.8.1.2
```

### Centos/RedHat

如果你使用的系统是 Centos/RedHat 安装命令为：

```
$ yum install curl-devel expat-devel gettext-devel \
  openssl-devel zlib-devel

$ yum -y install git-core

$ git --version
git version 1.7.1
```

### 源码安装

我们也可以在官网下载源码包来安装，最新源码包下载地址：https://git-scm.com/download

安装指定系统的依赖包：

```
########## Centos/RedHat ##########
$ yum install curl-devel expat-devel gettext-devel \
  openssl-devel zlib-devel

########## Debian/Ubuntu ##########
$ apt-get install libcurl4-gnutls-dev libexpat1-dev gettext \
  libz-dev libssl-dev
```

解压安装下载的源码包：

```
$ tar -zxf git-1.7.2.2.tar.gz
$ cd git-1.7.2.2
$ make prefix=/usr/local all
$ sudo make prefix=/usr/local install
```

------

## Windows 平台上安装

在 Windows 平台上安装 Git 同样轻松，有个叫做 msysGit 的项目提供了安装包，可以到 GitHub 的页面上下载 exe 安装文件并运行：

安装包下载地址：https://gitforwindows.org/

官网慢，可以用国内的镜像：https://npm.taobao.org/mirrors/git-for-windows/。

![img](https://www.runoob.com/wp-content/uploads/2015/02/20140127131250906)

完成安装之后，就可以使用命令行的 git 工具（已经自带了 ssh 客户端）了，另外还有一个图形界面的 Git 项目管理工具。

在开始菜单里找到"Git"->"Git Bash"，会弹出 Git 命令窗口，你可以在该窗口进行 Git 操作。

------

## Mac 平台上安装

在 Mac 平台上安装 Git 最容易的当属使用图形化的 Git 安装工具，下载地址为：

http://sourceforge.net/projects/git-osx-installer/

安装界面如下所示：



![18333fig0107-tn](https://www.runoob.com/wp-content/uploads/2015/02/18333fig0107-tn.png)

------

## Git 配置

Git 提供了一个叫做 git config 的工具，专门用来配置或读取相应的工作环境变量。

这些环境变量，决定了 Git 在各个环节的具体工作方式和行为。这些变量可以存放在以下三个不同的地方：

- `/etc/gitconfig` 文件：系统中对所有用户都普遍适用的配置。若使用 `git config` 时用 `--system` 选项，读写的就是这个文件。
- `~/.gitconfig` 文件：用户目录下的配置文件只适用于该用户。若使用 `git config` 时用 `--global` 选项，读写的就是这个文件。
- 当前项目的 Git 目录中的配置文件（也就是工作目录中的 `.git/config` 文件）：这里的配置仅仅针对当前项目有效。每一个级别的配置都会覆盖上层的相同配置，所以 `.git/config` 里的配置会覆盖 `/etc/gitconfig` 中的同名变量。

在 Windows 系统上，Git 会找寻用户主目录下的 .gitconfig 文件。主目录即 $HOME 变量指定的目录，一般都是 C:\Documents and Settings\$USER。

此外，Git 还会尝试找寻 /etc/gitconfig 文件，只不过看当初 Git 装在什么目录，就以此作为根目录来定位。

### 用户信息

配置个人的用户名称和电子邮件地址：

```
$ git config --global user.name "runoob"
$ git config --global user.email test@runoob.com
```

如果用了 **--global** 选项，那么更改的配置文件就是位于你用户主目录下的那个，以后你所有的项目都会默认使用这里配置的用户信息。

如果要在某个特定的项目中使用其他名字或者电邮，只要去掉 --global 选项重新配置即可，新的设定保存在当前项目的 .git/config 文件里。

### 文本编辑器

设置Git默认使用的文本编辑器, 一般可能会是 Vi 或者 Vim。如果你有其他偏好，比如 Emacs 的话，可以重新设置：:

```
$ git config --global core.editor emacs
```

### 差异分析工具

还有一个比较常用的是，在解决合并冲突时使用哪种差异分析工具。比如要改用 vimdiff 的话：

```
$ git config --global merge.tool vimdiff
```

Git 可以理解 kdiff3，tkdiff，meld，xxdiff，emerge，vimdiff，gvimdiff，ecmerge，和 opendiff 等合并工具的输出信息。

当然，你也可以指定使用自己开发的工具，具体怎么做可以参阅第七章。

### 查看配置信息

要检查已有的配置信息，可以使用 git config --list 命令：

```
$ git config --list
http.postbuffer=2M
user.name=runoob
user.email=test@runoob.com
```

有时候会看到重复的变量名，那就说明它们来自不同的配置文件（比如 /etc/gitconfig 和 ~/.gitconfig），不过最终 Git 实际采用的是最后一个。

这些配置我们也可以在 **~/.gitconfig** 或 **/etc/gitconfig** 看到，如下所示：

```
vim ~/.gitconfig 
```

显示内容如下所示：

```
[http]
    postBuffer = 2M
[user]
    name = runoob
    email = test@runoob.com
```

也可以直接查阅某个环境变量的设定，只要把特定的名字跟在后面即可，像这样：

```
$ git config user.name
runoob
```

](https://www.runoob.com/wp-content/uploads/2015/02/0D32F290-80B0-4EA4-9836-CA58E22569B3.jpg)

# Git 工作流程

本章节我们将为大家介绍 Git 的工作流程。

一般工作流程如下：

- 克隆 Git 资源作为工作目录。
- 在克隆的资源上添加或修改文件。
- 如果其他人修改了，你可以更新资源。
- 在提交前查看修改。
- 提交修改。
- 在修改完成后，如果发现错误，可以撤回提交并再次修改并提交。

下图展示了 Git 的工作流程：

![img](https://www.runoob.com/wp-content/uploads/2015/02/git-process.png)

# Git 工作区、暂存区和版本库

------

## 基本概念

我们先来理解下 Git 工作区、暂存区和版本库概念：

- **工作区：**就是你在电脑里能看到的目录。
- **暂存区：**英文叫 stage 或 index。一般存放在 **.git** 目录下的 index 文件（.git/index）中，所以我们把暂存区有时也叫作索引（index）。
- **版本库：**工作区有一个隐藏目录 **.git**，这个不算工作区，而是 Git 的版本库。

下面这个图展示了工作区、版本库中的暂存区和版本库之间的关系：

![img](https://www.runoob.com/wp-content/uploads/2015/02/1352126739_7909.jpg)

- 图中左侧为工作区，右侧为版本库。在版本库中标记为 "index" 的区域是暂存区（stage/index），标记为 "master" 的是 master 分支所代表的目录树。
- 图中我们可以看出此时 "HEAD" 实际是指向 master 分支的一个"游标"。所以图示的命令中出现 HEAD 的地方可以用 master 来替换。
- 图中的 objects 标识的区域为 Git 的对象库，实际位于 ".git/objects" 目录下，里面包含了创建的各种对象及内容。
- 当对工作区修改（或新增）的文件执行 **git add** 命令时，暂存区的目录树被更新，同时工作区修改（或新增）的文件内容被写入到对象库中的一个新的对象中，而该对象的ID被记录在暂存区的文件索引中。
- 当执行提交操作（git commit）时，暂存区的目录树写到版本库（对象库）中，master 分支会做相应的更新。即 master 指向的目录树就是提交时暂存区的目录树。
- 当执行 **git reset HEAD** 命令时，暂存区的目录树会被重写，被 master 分支指向的目录树所替换，但是工作区不受影响。
- 当执行 **git rm --cached <file>** 命令时，会直接从暂存区删除文件，工作区则不做出改变。
- 当执行 **git checkout .** 或者 **git checkout -- <file>** 命令时，会用暂存区全部或指定的文件替换工作区的文件。这个操作很危险，会清除工作区中未添加到暂存区中的改动。
- 当执行 **git checkout HEAD .** 或者 **git checkout HEAD <file>** 命令时，会用 HEAD 指向的 master 分支中的全部或者部分文件替换暂存区和以及工作区中的文件。这个命令也是极具危险性的，因为不但会清除工作区中未提交的改动，也会清除暂存区中未提交的改动。



# Git 创建仓库

本章节我们将为大家介绍如何创建一个 Git 仓库。

你可以使用一个已经存在的目录作为Git仓库。

------

## git init

Git 使用 **git init** 命令来初始化一个 Git 仓库，Git 的很多命令都需要在 Git 的仓库中运行，所以 **git init** 是使用 Git 的第一个命令。

在执行完成 **git init** 命令后，Git 仓库会生成一个 .git 目录，该目录包含了资源的所有元数据，其他的项目目录保持不变。

### 使用方法

使用当前目录作为Git仓库，我们只需使它初始化。

```
git init
```

该命令执行完后会在当前目录生成一个 .git 目录。

使用我们指定目录作为Git仓库。

```
git init newrepo
```

初始化后，会在 newrepo 目录下会出现一个名为 .git 的目录，所有 Git 需要的数据和资源都存放在这个目录中。

如果当前目录下有几个文件想要纳入版本控制，需要先用 git add 命令告诉 Git 开始对这些文件进行跟踪，然后提交：

```
$ git add *.c
$ git add README
$ git commit -m '初始化项目版本'
```

以上命令将目录下以 .c 结尾及 README 文件提交到仓库中。

> **注：** 在 Linux 系统中，commit 信息使用单引号 **'**，Windows 系统，commit 信息使用双引号 **"**。
>
> 所以在 git bash 中 **git commit -m '提交说明'** 这样是可以的，在 Windows 命令行中就要使用双引号 **git commit -m "提交说明"**。

------

## git clone

我们使用 **git clone** 从现有 Git 仓库中拷贝项目（类似 **svn checkout**）。

克隆仓库的命令格式为：

```
git clone <repo>
```

如果我们需要克隆到指定的目录，可以使用以下命令格式：

```
git clone <repo> <directory>
```

**参数说明：**

- **repo:**Git 仓库。
- **directory:**本地目录。

比如，要克隆 Ruby 语言的 Git 代码仓库 Grit，可以用下面的命令：

```
$ git clone git://github.com/schacon/grit.git
```

执行该命令后，会在当前目录下创建一个名为grit的目录，其中包含一个 .git 的目录，用于保存下载下来的所有版本记录。

如果要自己定义要新建的项目目录名称，可以在上面的命令末尾指定新的名字：



```
$ git clone git://github.com/schacon/grit.git mygrit
```

## 配置

git 的设置使用 **git config** 命令。

显示当前的 git 配置信息：

```
$ git config --list
credential.helper=osxkeychain
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
core.ignorecase=true
core.precomposeunicode=true
```

编辑 git 配置文件:

```
$ git config -e    # 针对当前仓库 
```

或者：

```
$ git config -e --global   # 针对系统上所有仓库
```

设置提交代码时的用户信息：

```
$ git config --global user.name "runoob"
$ git config --global user.email test@runoob.com
```

如果去掉 **--global** 参数只对当前仓库有效。



# Git 基本操作

Git 的工作就是创建和保存你项目的快照及与之后的快照进行对比。

本章将对有关创建与提交你的项目快照的命令作介绍。

Git 常用的是以下 6 个命令：**git clone**、**git push**、**git add** 、**git commit**、**git checkout**、**git pull**，后面我们会详细介绍。

![img](https://www.runoob.com/wp-content/uploads/2015/02/git-command.jpg)

**说明：**

- workspace：工作区
- staging area：暂存区/缓存区
- local repository：版本库或本地仓库
- remote repository：远程仓库

一个简单的操作步骤：

```
$ git init    
$ git add .    
$ git commit  
```

- git init - 初始化仓库。
- git add . - 添加文件到暂存区。
- git commit - 将暂存区内容添加到仓库中。

### 创建仓库命令

下表列出了 git 创建仓库的命令：

| 命令        | 说明                                   |
| :---------- | :------------------------------------- |
| `git init`  | 初始化仓库                             |
| `git clone` | 拷贝一份远程仓库，也就是下载一个项目。 |

------

## 提交与修改

Git 的工作就是创建和保存你的项目的快照及与之后的快照进行对比。

下表列出了有关创建与提交你的项目的快照的命令：

| 命令         | 说明                                     |
| :----------- | :--------------------------------------- |
| `git add`    | 添加文件到仓库                           |
| `git status` | 查看仓库当前的状态，显示有变更的文件。   |
| `git diff`   | 比较文件的不同，即暂存区和工作区的差异。 |
| `git commit` | 提交暂存区到本地仓库。                   |
| `git reset`  | 回退版本。                               |
| `git rm`     | 删除工作区文件。                         |
| `git mv`     | 移动或重命名工作区文件。                 |

### 提交日志

| 命令               | 说明                                 |
| :----------------- | :----------------------------------- |
| `git log`          | 查看历史提交记录                     |
| `git blame <file>` | 以列表形式查看指定文件的历史修改记录 |

### 远程操作

| 命令         | 说明               |
| :----------- | :----------------- |
| `git remote` | 远程仓库操作       |
| `git fetch`  | 从远程获取代码库   |
| `git pull`   | 下载远程代码并合并 |
| `git push`   | 上传远程代码并合并 |





# Git 分支管理

几乎每一种版本控制系统都以某种形式支持分支。使用分支意味着你可以从开发主线上分离开来，然后在不影响主线的同时继续工作。

有人把 Git 的分支模型称为**必杀技特性**，而正是因为它，将 **Git** 从版本控制系统家族里区分出来。

创建分支命令：

```
git branch (branchname)
```

切换分支命令:

```
git checkout (branchname)
```

当你切换分支的时候，Git 会用该分支的最后提交的快照替换你的工作目录的内容， 所以多个分支不需要多个目录。

合并分支命令:

```
git merge 
```

你可以多次合并到统一分支， 也可以选择在合并之后直接删除被并入的分支。

开始前我们先创建一个测试目录：

```
$ mkdir gitdemo
$ cd gitdemo/
$ git init
Initialized empty Git repository...
$ touch README
$ git add README
$ git commit -m '第一次版本提交'
[master (root-commit) 3b58100] 第一次版本提交
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README
```

------

## Git 分支管理

### 列出分支

列出分支基本命令：

```
git branch
```

没有参数时，**git branch** 会列出你在本地的分支。

```
$ git branch
* master
```

此例的意思就是，我们有一个叫做 **master** 的分支，并且该分支是当前分支。

当你执行 **git init** 的时候，默认情况下 Git 就会为你创建 **master** 分支。

如果我们要手动创建一个分支。执行 **git branch (branchname)** 即可。

```
$ git branch testing
$ git branch
* master
  testing
```

现在我们可以看到，有了一个新分支 **testing**。

当你以此方式在上次提交更新之后创建了新分支，如果后来又有更新提交， 然后又切换到了 **testing** 分支，Git 将还原你的工作目录到你创建分支时候的样子。

接下来我们将演示如何切换分支，我们用 git checkout (branch) 切换到我们要修改的分支。

```
$ ls
README
$ echo 'runoob.com' > test.txt
$ git add .
$ git commit -m 'add test.txt'
[master 3e92c19] add test.txt
 1 file changed, 1 insertion(+)
 create mode 100644 test.txt
$ ls
README        test.txt
$ git checkout testing
Switched to branch 'testing'
$ ls
README
```

当我们切换到 **testing** 分支的时候，我们添加的新文件 test.txt 被移除了。切换回 **master** 分支的时候，它们有重新出现了。

```
$ git checkout master
Switched to branch 'master'
$ ls
README        test.txt
```

我们也可以使用 git checkout -b (branchname) 命令来创建新分支并立即切换到该分支下，从而在该分支中操作。

```
$ git checkout -b newtest
Switched to a new branch 'newtest'
$ git rm test.txt 
rm 'test.txt'
$ ls
README
$ touch runoob.php
$ git add .
$ git commit -am 'removed test.txt、add runoob.php'
[newtest c1501a2] removed test.txt、add runoob.php
 2 files changed, 1 deletion(-)
 create mode 100644 runoob.php
 delete mode 100644 test.txt
$ ls
README        runoob.php
$ git checkout master
Switched to branch 'master'
$ ls
README        test.txt
```

如你所见，我们创建了一个分支，在该分支的上移除了一些文件 test.txt，并添加了 runoob.php 文件，然后切换回我们的主分支，删除的 test.txt 文件又回来了，且新增加的 runoob.php 不存在主分支中。

使用分支将工作切分开来，从而让我们能够在不同开发环境中做事，并来回切换。

### 删除分支

删除分支命令：

```
git branch -d (branchname)
```

例如我们要删除 testing 分支：

```
$ git branch
* master
  testing
$ git branch -d testing
Deleted branch testing (was 85fc7e7).
$ git branch
* master
```

### 分支合并

一旦某分支有了独立内容，你终究会希望将它合并回到你的主分支。 你可以使用以下命令将任何分支合并到当前分支中去：

```
git merge
$ git branch
* master
  newtest
$ ls
README        test.txt
$ git merge newtest
Updating 3e92c19..c1501a2
Fast-forward
 runoob.php | 0
 test.txt   | 1 -
 2 files changed, 1 deletion(-)
 create mode 100644 runoob.php
 delete mode 100644 test.txt
$ ls
README        runoob.php
```

以上实例中我们将 newtest 分支合并到主分支去，test.txt 文件被删除。

合并完后就可以删除分支:

```
$ git branch -d newtest
Deleted branch newtest (was c1501a2).
```

删除后， 就只剩下 master 分支了：

```
$ git branch
* master
```

### 合并冲突

合并并不仅仅是简单的文件添加、移除的操作，Git 也会合并修改。

```
$ git branch
* master
$ cat runoob.php
```

首先，我们创建一个叫做 change_site 的分支，切换过去，我们将 runoob.php 内容改为:

```
<?php
echo 'runoob';
?>
```

创建 change_site 分支：

```
$ git checkout -b change_site
Switched to a new branch 'change_site'
$ vim runoob.php
$ head -3 runoob.php
<?php
echo 'runoob';
?>
$ git commit -am 'changed the runoob.php'
[change_site 7774248] changed the runoob.php
 1 file changed, 3 insertions(+)
 
```

将修改的内容提交到 change_site 分支中。 现在，假如切换回 master 分支我们可以看内容恢复到我们修改前的(空文件，没有代码)，我们再次修改 runoob.php 文件。

```
$ git checkout master
Switched to branch 'master'
$ cat runoob.php
$ vim runoob.php    # 修改内容如下
$ cat runoob.php
<?php
echo 1;
?>
$ git diff
diff --git a/runoob.php b/runoob.php
index e69de29..ac60739 100644
--- a/runoob.php
+++ b/runoob.php
@@ -0,0 +1,3 @@
+<?php
+echo 1;
+?>
$ git commit -am '修改代码'
[master c68142b] 修改代码
 1 file changed, 3 insertions(+)
```

现在这些改变已经记录到我的 "master" 分支了。接下来我们将 "change_site" 分支合并过来。

```
$ git merge change_site
Auto-merging runoob.php
CONFLICT (content): Merge conflict in runoob.php
Automatic merge failed; fix conflicts and then commit the result.

$ cat runoob.php     # 打开文件，看到冲突内容
<?php
<<<<<<< HEAD
echo 1;
=======
echo 'runoob';
>>>>>>> change_site
?>
```

我们将前一个分支合并到 master 分支，一个合并冲突就出现了，接下来我们需要手动去修改它。

```
$ vim runoob.php 
$ cat runoob.php
<?php
echo 1;
echo 'runoob';
?>
$ git diff
diff --cc runoob.php
index ac60739,b63d7d7..0000000
--- a/runoob.php
+++ b/runoob.php
@@@ -1,3 -1,3 +1,4 @@@
  <?php
 +echo 1;
+ echo 'runoob';
  ?>
```

在 Git 中，我们可以用 git add 要告诉 Git 文件冲突已经解决

```
$ git status -s
UU runoob.php
$ git add runoob.php
$ git status -s
M  runoob.php
$ git commit
[master 88afe0e] Merge branch 'change_site'
```





# Git 查看提交历史

Git提交历史通常经常两个命令：

- **git log** - 查看历史提交记录。
- **git blame <file>** - 以列表形式查看指定文件的历史修改记录。
- ### 混帐日志

- 在使用 Git 提交了若干更新，又或者克隆了某个项目之后，想回顾下提交历史，我们可以使用**git log**命令查看。

- 针对我们前一阶段的操作，使用**git log**命令提交历史提交记录如下：

- ```
  $ git 日志
  提交 d5e9fc2c811e0ca2b2d28506ef7dc14171a207d9 (HEAD -> master)
  合并：c68142b 7774248
  作者：runoob <test@runoob.com>
  日期：2019 年 5 月 3 日星期五 15:55:58 +0800
  
      合并分支“change_site”
  
  提交 c68142b562c260c3071754623b08e2657b4c6d5b
  作者：runoob <test@runoob.com>
  日期：2019 年 5 月 3 日星期五 15:52:12 +0800
  
      修改代码
  
  提交 777424832e714cf65d3be79b50a4717aea51ab69 (change_site)
  作者：runoob <test@runoob.com>
  日期：2019 年 5 月 3 日星期五 15:49:26 +0800
  
      改变了runoob.php
  
  提交 c1501a244676ff55e7cccac1ecac0e18cbf6cb00
  作者：runoob <test@runoob.com>
  日期：2019 年 5 月 3 日星期五 15:35:32 +0800
  ```

- 我们可以用 --oneline 选项来查看历史记录的简单版本。

- ```
  $ git log --oneline
  $ git log --oneline
  d5e9fc2 (HEAD -> master) 合并分支“change_site”
  c68142b 修改代码
  7774248 (change_site) 更改了 runoob.php
  c1501a2删除了test.txt、添加runoob.php
  3e92c19 添加test.txt
  3b58100 第一次版本提交
  ```

- 这告诉我们，这个项目的开发历史。

- 我们还可以用--graph，查看历史中什么时候出现了分支、合并以下。为相同的命令，选项开启了拓扑选项：

- ```
  * d5e9fc2 (HEAD -> master) 合并分支“change_site”
  |\  
  | * 7774248 (change_site) 更改了 runoob.php
  * | c68142b 修改代码
  |/  
  * c1501a2 删除了 test.txt、添加了 runoob.php
  * 3e92c19 添加 test.txt
  * 3b58100 第一次版本提交
  ```

- 现在我们可以更清楚地看到什么时候工作分叉、又何时归并。

- 你也可以用**--reverse**参数来逆向显示所有日志。

- ```
  $ git log --reverse --oneline
  3b58100 第一次版本提交
  3e92c19 添加test.txt
  c1501a2删除了test.txt、添加runoob.php
  7774248 (change_site) 更改了 runoob.php
  c68142b 修改代码
  d5e9fc2 (HEAD -> master) 合并分支“change_site”
  ```

- 如果想要查找指定用户的提交日志可以使用命令：git log --author，例如，比方说我们要找 Git 源码中 Linus 提交的部分：

- ```
  $ git log --author=Linus --oneline -5
  81b50f3 将“builtin-*”移动到“builtin/”子目录中
  3bb7256 使“索引包”成为内置
  377d027 使“git pack-redundant”成为内置
  b532581 使“git unpack-file”成为内置
  112dd51 使“mktag”成为内置
  ```

- 如果你要指定日期，可以执行几个选项：--since 和 --before，但是你也可以用--until 和--after。

- 例如，如果我还前查看 Git 项目中三周且在四月十八日之后的所有提交，我可以执行（我用了 --no-merges 选项以隐藏合并提交）：

- ```
  $ git log --oneline --before={3.weeks.ago} --after={2010-04-18} --no-merges
  5469e2d Git 1.7.1-rc2
  d43427d 文档/远程助手：修复拼写错误并改进语言
  272a36b 修正：第二个参数可以是任意字符串
  b6c8d2d 文档/远程助手：添加调用部分
  5ce4f4e 文档/网址：重写以适应传输::地址
  00b84e9 文档/远程助手：重写描述
  03aa87e 文档：描述 -z 影响 git diff 的其他情况
  77bc694 rebase-interactive：未重写提交时的静音警告
  636db2c t3301：添加测试以使用 --format="%N"
  ```

- 更多 git log 命令可查看：http://git-scm.com/docs/git-log

- ### 怪罪

- 如果要查看指定文件的修改记录可以使用gitblame命令，格式如下：

- ```
  git 责备 <文件>
  ```

- gitblame命令以表格形式显示修改记录，如下实例：

- ```
  $ git 责备自述文件 
  ^d2097aa (tianqixin 2020-08-25 14:59:25 +0800 1) # Runoob Git 测试
  db9315b0 (runoob 2020-08-25 16:00:23 +0800 2) #菜鸟教程 
  ```





# Git 标签

如果你达到一个重要的阶段，并希望永远记住那个特别的提交快照，你可以使用 git tag 给它打上标签。

比如说，我们想为我们的 runoob 项目发布一个"1.0"版本。 我们可以用 git tag -a v1.0 命令给最新一次提交打上（HEAD）"v1.0"的标签。

-a 选项意为"创建一个带注解的标签"。 不用 -a 选项也可以执行的，但它不会记录这标签是啥时候打的，谁打的，也不会让你添加个标签的注解。 我推荐一直创建带注解的标签。

```
$ git tag -a v1.0 
```

当你执行 git tag -a 命令时，Git 会打开你的编辑器，让你写一句标签注解，就像你给提交写注解一样。

现在，注意当我们执行 git log --decorate 时，我们可以看到我们的标签了：

```
*   d5e9fc2 (HEAD -> master) Merge branch 'change_site'
|\  
| * 7774248 (change_site) changed the runoob.php
* | c68142b 修改代码
|/  
* c1501a2 removed test.txt、add runoob.php
* 3e92c19 add test.txt
* 3b58100 第一次版本提交
```

如果我们忘了给某个提交打标签，又将它发布了，我们可以给它追加标签。

例如，假设我们发布了提交 85fc7e7(上面实例最后一行)，但是那时候忘了给它打标签。 我们现在也可以：

```
$ git tag -a v0.9 85fc7e7
$ git log --oneline --decorate --graph
*   d5e9fc2 (HEAD -> master) Merge branch 'change_site'
|\  
| * 7774248 (change_site) changed the runoob.php
* | c68142b 修改代码
|/  
* c1501a2 removed test.txt、add runoob.php
* 3e92c19 add test.txt
* 3b58100 (tag: v0.9) 第一次版本提交
```

如果我们要查看所有标签可以使用以下命令：

```
$ git tag
v0.9
v1.0
```

指定标签信息命令：

```
git tag -a <tagname> -m "runoob.com标签"
```

PGP签名标签命令：

```
git tag -s <tagname> -m "runoob.com标签"
```





# Git远程仓库(Github)

Git 不是像 SVN 那样的服务中心。

如果我们现在使用到的 Git 命令在本地执行，你想通过 Git 分享你的代码或者与其他开发人员合作。

本例使用了 Github 作为远程仓库，你可以先阅读我们的[Github 简明教程。](https://www.runoob.com/w3cnote/git-guide.html)

![img](https://www.runoob.com/wp-content/uploads/2015/03/Git-push-command.jpeg)

------

## 添加远程库

要添加一个新的远程仓库，可以指定一个简单的名字，以便将来引用，命令如下格式：

```
git remote add [shortname] [url]
```

本例以 Github 为例作为远程仓库，如果你 Github 可以在官网https://github.com/注册。



因为你本地的Git仓库和GitHub仓库之间的传输是通过SSH共享的，所以我们需要验证信息：

使用以下命令生成SSH Key：

```
$ ssh-keygen -t rsa -C "youremail@example.com"
```

不用的**your_email@youremail.com**改为你在Github上注册的邮箱，之后会要求确认路径和输入密码，我们这默认使用的一路回车就行。

成功的话会在**~/**下生成**.ssh**，打开，打开**id_rsa.pub**，复制里面的**key**。

```
$ ssh-keygen -t rsa -C "429240967@qq.com"-密钥生成-吨RSA - ç “429240967@qq.com”
生成公钥/私钥 rsa 密钥对。生成公共/私人rsa 密钥对。 
输入保存密钥的文件（/Users/tianqixin/.ssh/id_rsa）： 输入文件中要保存键（/用户/ tianqixin /。SSH / id_rsa ）： 
输入密码（无密码为空）：#直接回车输入密码（空为无密码）：#直接回车     
再次输入相同的密码：#直接回车再次输入相同的密码：#直接回车                   
您的身份信息已保存在/Users/tianqixin/.ssh/id_rsa。您的身份信息已保存在/用户/天启信/。ssh / id_rsa 。 
您的公钥已保存在/Users/tianqixin/.ssh/id_rsa.pub。你的公共密钥已经保存在/用户/ tianqixin /。ssh / id_rsa 。酒吧。  
关键指纹是：该密钥指纹是：
SHA256:MDKVidPTDXIQoJwoqUmI4LBAsg5XByBlrOEzkxrwARI 429240967@qq.com: MDKVidPTDXIQoJwoqUmI4LBAsg5XByBlrOEzkxrwARI 429240967@qq 。电脑 
钥匙的 randomart 图像是：在关键的randomart形象是：
+---[RSA 3072]----+
|E*+.+=**oo |
|%Oo+oo=o。. |
|%**.oo |
|哦。哦|
|+o+ S |
|。|
| |
| |
| |
+----[SHA256]-----+
```

回到github上，进入Account => Settings（账户配置）。

![img](https://www.runoob.com/wp-content/uploads/2015/03/48840BF0-992F-4CCC-A388-15CB74819D88.jpg)

美食选择**SSH和GPG密钥**，然后点击**新建SSH密钥**按钮，标题标题，可以随意填写，粘贴在你电脑上生成的密钥。

![img](https://www.runoob.com/wp-content/uploads/2015/03/B0589847-A498-4415-8700-252BDE1B20C0.jpg)

![img](https://www.runoob.com/wp-content/uploads/2015/03/106AD534-A38A-47F3-88A3-B7BE3F2FEEF1.jpg)

添加成功后界面如下所示



![img](https://www.runoob.com/wp-content/uploads/2015/03/EC8F8872-091A-4CAB-90F2-616F34F350A9.jpg)

为了验证是否成功，输入以下命令：

```
$ ssh -T git@github.com-牛逼的git @ github上。电脑
无法确定主机“github.com (52.74.223.119)”的真实性。所述主机的真实性“github.com（52.74.223.119）”可“T来建立。
RSA 密钥指纹是 SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8。
您确定要继续连接吗（是/否/[指纹]）？是#输入是
警告：将“github.com,52.74.223.119”（RSA）永久添加到已知主机列表中。github 。com ，52.74 。223.119 ' (RSA) 到已知主机列表。
你好田七欣！您已成功通过身份验证，但 GitHub 不提供 shell 访问。#成功信息成功已经验证，但GitHub上并没有提供shell访问。#成功信息 
```

下面的命令说明我们已经成功连上Github。

登录后点击“新建仓库”如下图所示：

![img](https://www.runoob.com/wp-content/uploads/2015/03/github1.jpg)

之后在Repository name 入runoob-git-test(远程仓库名)，其他保持默认设置，点击“Create repository”按钮，就成功地创建了一个新的Git仓库：

![img](https://www.runoob.com/wp-content/uploads/2015/03/299CF000-7B6E-4BEC-B8C2-D9AEB053307B.jpg)

创建成功后，显示如下信息：

![img](https://www.runoob.com/wp-content/uploads/2015/03/1BCB4379-1A25-4C77-BB82-92B3E7185435.jpg)

以上信息告诉我们可以从这个仓库克隆出新的仓库，也可以把仓库里的内容送到GitHub。

现在，我们根据 GitHub 的提示，在本地的仓库下运行命令：

```
$ mkdir runoob-git-test #创建测试目录- git - test                      #创建测试目录
$ cd runoob-git-test/ # 进入测试目录- git - test / #进入测试目录                       
$ echo "#菜鸟教程 Git 测试" >> README.md #创建 README.md 文件并写入内容"#菜鸟教程 Git 测试" >>自述文件。md      #创建README.md 文件并写入内容 
$ ls # 查看目录下的文件# 查看目录下的文件
自述文件
$ git init # 初始化# 初始化
$ git add README.md #添加文件. md                          #添加文件
$ git commit -m "添加README.md文件" #提交并附备注信息- m "添加 README.md 文件" # 提交并提交备注信息        
[master (root-commit) 0205aab] 添加 README.md 文件[ master ( root - commit ) 0205aab ]添加自述文件。md文件  
 1 个文件已更改，1 个插入 (+)1 个文件已更改，1 个插入(+) 
 创建模式 100644 README.md100644自述文件。医学博士

#提交到Github#提交到Github
$ git remote add origin git@github.com:tianqixin/runoob-git-test.git. com : tianqixin / runoob - git - test . 混帐
$ git push -u origin master-你的起源大师
```

以下命令请根据你在Github成功创建的新仓库的地方复制，而不是根据我提供的命令，因为我们的Github用户名不一样，仓库名也不一样。

接下来我们返回 Github 创建的仓库，就可以看到文件已上传到 Github 上：

![img](https://www.runoob.com/wp-content/uploads/2015/03/53CA927D-F36F-4A00-AFB2-5EAED05B535E.jpg)

------

## 查看当前的远程库

要查看当前配置有哪些远程仓库，可以用命令：

```
git远程
```

### 实例

```
$ git 远程
起源
$ git 远程 -v- v
origin git@github.com:tianqixin/runoob-git-test.git (fetch). com : tianqixin / runoob - git - test . git (获取)
origin git@github.com:tianqixin/runoob-git-test.git（推送）. com : tianqixin / runoob - git - test . git (推)
```

执行时加上 -v 参数，你还可以看到每个其他的具体链接地址。

------

## 提取远程仓库

Git 有两个命令处理删除远程仓库的更新。

1、从远程仓库下载新分支与数据：

```
混帐
```

该执行后需要执行 git merge 远程分支到你所在的命令分支。

2、从远端提取数据并样本合并到当前：

```
合并
```

该命令就是在执行**git fetch**之后紧接着执行**merge**远程分支到你所属的任意分支。

![img](https://www.runoob.com/wp-content/uploads/2015/03/main-qimg-00a6b5a8ec82400657444504c4d4d1a7.png)

假你配置好了一个远程仓库，并且你想要**提取**更新的数据，你可以先执行**git fetch [别名]** 告诉Git 去获取它有你没有的数据，然后你可以执行**git merge [别名]/[branch] ]**以将服务器上的任何更新（如果有人此时发送到服务器）合并到你的当前分支。

接下来我们在 Github 上点击“README.md”并在线修改它：

![img](https://www.runoob.com/wp-content/uploads/2015/03/C5A6670F-202D-4F2C-8A63-07CEA37BB67A.jpg)

然后我们在本地更新修改。

```
$ git 获取来源
远程：计数对象：3，完成。：计数对象：3 ，完成。   
远程：压缩对象：100% (2/2)，完成。：压缩对象：100 % （2 / 2 ），完成。    
远程：总计 3 (delta 0)，重用 0 (delta 0)，pack-reused 0:总计3 ( delta 0 ),重用0 ( delta 0 ),打包-重用0    
拆包对象：100% (3/3)，完成。拆包对象：100 % ( 3 / 3 )，完成。   
来自github.com：tianqixin/runoob-git-test来自github 。com : tianqixin / runoob - git - test
   0205aab..febd8ed master -> origin/master0205aab .. febd8ed master      -> origin / master
```

以上信息“0205aab..febd8ed master -> origin/master”说明master分支已被更新，我们可以使用以下命令将更新同步到本地：

```
$ git merge origin/master/大师
更新 0205aab..febd8ed更新0205aab .. febd8ed 
快进快速-向前
 README.md | 1 +. 医学博士| 1 +  
 1 个文件已更改，1 个插入 (+)1 个文件已更改，1 个插入(+) 
```

查看README.md文件内容：

```
$ cat README.md . 医学博士
# 菜鸟教程 Git 测试# 菜鸟教程 Git 测试
##第一次修改内容##第一次修改内容
```

------

## 发送到远程仓库

发送你的新分支与数据到某个终点命令：

```
git push [别名] [分支]
[别名] [分支] 
```

以上将命令分支的[分支]将你的分支接入[别名]远程仓库上的[分支]，实例如下。

```
$ touch runoob-test.txt #添加文件-测试。txt       #添加文件
$ git add runoob-test.txt -测试。文本
$ git commit -m "添加到远程"-米“添加到远程”
master 69e702d]添加到远程69e702d ]添加到远程 
 1 个文件更改，0 次插入（+），0 次删除（-）1 个文件已更改，0 次插入(+)，0 次删除(-)  
 创建模式 100644 runoob-test.txt100644 runoob -测试。文本

$ git push origin master # 推送到 Github# 提交到 Github
```

重回到我们的 Github 仓库，可以看到文件已经提交上来了：

![img](https://www.runoob.com/wp-content/uploads/2015/03/79A84530-7DC0-4D25-9F83-8776433A4C32.jpg)

------

## 删除远程仓库

删除远程仓库你可以使用命令：

```
git remote rm [别名][别名]
```

### 实例

```
$ git 远程 -v- v
origin git@github.com:tianqixin/runoob-git-test.git (fetch). com : tianqixin / runoob - git - test . git (获取)
origin git@github.com:tianqixin/runoob-git-test.git（推送）. com : tianqixin / runoob - git - test . git (推)

#添加仓库origin2#添加仓库origin2
$ git remote add origin2 git@github.com:tianqixin/runoob-git-test.git. com : tianqixin / runoob - git - test . 混帐

$ git 远程 -v- v
origin git@github.com:tianqixin/runoob-git-test.git (fetch). com : tianqixin / runoob - git - test . git (获取)
origin git@github.com:tianqixin/runoob-git-test.git（推送）. com : tianqixin / runoob - git - test . git (推)
origin2 git@github.com:tianqixin/runoob-git-test.git（获取）. com : tianqixin / runoob - git - test . git (获取)
origin2 git@github.com:tianqixin/runoob-git-test.git（推送）. com : tianqixin / runoob - git - test . git (推)

#删除仓库 origin2#删除仓库 origin2
$ git remote rm origin2
$ git 远程 -v- v
origin git@github.com:tianqixin/runoob-git-test.git (fetch). com : tianqixin / runoob - git - test . git (获取)
origin git@github.com:tianqixin/runoob-git-test.git（推送）. com : tianqixin / runoob - git - test . git (推)
```





# Git Gitee

大家都知道国内访问 Github 速度比较慢，很影响我们的使用。

如果你希望体验到 Git 飞一般的速度，可以使用国内的 Git 托管服务——[Gitee（gitee.com）](https://gitee.com/?utm_source=remote_blog_cnjc)。

Gitee 提供免费的 Git 仓库，还集成了代码质量检测、项目演示等功能。对于团队协作开发，Gitee 还提供了项目管理、代码托管、文档管理的服务，5 人以下小团队免费。

接下来我们学习一下如何使用 Gitee。

由于我们的本地 Git 仓库和 Gitee 仓库之间的传输是通过SSH加密的，所以我们需要配置验证信息。

**1、我们先在 [Gitee](https://gitee.com/?utm_source=remote_blog_cnjc) 上注册账号并登录后，然后上传自己的 SSH 公钥。**

我们在 Git Github 章节已经生成了自己的 SSH 公钥，所以我们只需要将用户主目录下的 ~/.ssh/id_rsa.pub 文件的内容粘贴 Gitee 上。

选择右上角用户头像 -> 设置，然后选择 "SSH公钥"，填写一个便于识别的标题，然后把用户主目录下的 .ssh/id_rsa.pub 文件的内容粘贴进去：

![img](https://www.runoob.com/wp-content/uploads/2020/03/gitee1.png)

![img](https://www.runoob.com/wp-content/uploads/2020/03/gitee2.png)

成功添加后如下图所示：

![img](https://www.runoob.com/wp-content/uploads/2020/03/gitee3.png)

接下来我们创建一个项目。

点击右上角的 **+** 号，新建仓库：

![img](https://www.runoob.com/wp-content/uploads/2020/03/gitee4.png)

然后添加仓库信息：

![img](https://www.runoob.com/wp-content/uploads/2020/03/gitee5.png)

创建成功后看到如下信息：

![img](https://www.runoob.com/wp-content/uploads/2020/03/gitee6.png)

接下来我们看下连接信息：

![img](https://www.runoob.com/wp-content/uploads/2020/03/gitee7.png)

项目名称最好与本地库保持一致。

然后，我们在本地库上使用命令 **git remote add** 把它和 Gitee 的远程库关联：

```
git remote add origin git@gitee.com:imnoob/runoob-test.git
```

之后，就可以正常地用 git push 和 git pull 推送了！

如果在使用命令 git remote add 时报错：

```
git remote add origin git@gitee.com:imnoob/runoob-test.git
fatal: remote origin already exists.
```

这说明本地库已经关联了一个名叫 origin 的远程库，此时，可以先用 **git remote -v** 查看远程库信息：

```
git remote -v
origin    git@github.com:tianqixin/runoob.git (fetch)
origin    git@github.com:tianqixin/runoob.git (push)
```

可以看到，本地库已经关联了 origin 的远程库，并且，该远程库指向 GitHub。

我们可以删除已有的 GitHub 远程库：

```
git remote rm origin
```

再关联 Gitee 的远程库（注意路径中需要填写正确的用户名）：

```
git remote add origin git@gitee.com:imnoob/runoob-test.git
```

此时，我们再查看远程库信息：

```
git remote -v
origin    git@gitee.com:imnoob/runoob-test.git (fetch)
origin    git@gitee.com:imnoob/runoob-test.git (push)
```

现在可以看到，origin 已经被关联到 Gitee 的远程库了。

通过 git push 命令就可以把本地库推送到 Gitee 上。

有的小伙伴又要问了，一个本地库能不能既关联 GitHub，又关联 Gitee 呢？

答案是肯定的，因为 git 本身是分布式版本控制系统，可以同步到另外一个远程库，当然也可以同步到另外两个远程库。

使用多个远程库时，我们要注意，git 给远程库起的默认名称是 origin，如果有多个远程库，我们需要用不同的名称来标识不同的远程库。

仍然以 runoob-test 本地库为例，我们先删除已关联的名为 origin 的远程库：

```
git remote rm origin
```

然后，先关联 GitHub 的远程库：

```
git remote add github git@github.com:tianqixin/runoob-git-test.git
```

注意，远程库的名称叫 github，不叫 origin 了。

接着，再关联 Gitee 的远程库：

```
git remote add gitee git@gitee.com:imnoob/runoob-test.git
```

同样注意，远程库的名称叫 gitee，不叫 origin。

现在，我们用 git remote -v 查看远程库信息，可以看到两个远程库：

```
git remote -v
gitee    git@gitee.com:imnoob/runoob-test.git (fetch)
gitee    git@gitee.com:imnoob/runoob-test.git (push)
github    git@github.com:tianqixin/runoob.git (fetch)
github    git@github.com:tianqixin/runoob.git (push)
```

如果要推送到 GitHub，使用命令：

```
git push github master
```

如果要推送到 Gitee，使用命令：

```
git push gitee master
```

这样一来，我们的本地库就可以同时与多个远程库互相同步：

![img](https://www.runoob.com/wp-content/uploads/2020/03/gitee8.png)





# Git 服务器搭建

上一章节中我们远程仓库使用了 Github，Github 公开的项目是免费的，2019 年开始 Github 私有存储库也可以无限制使用。

这当然我们也可以自己搭建一台 Git 服务器作为私有仓库使用。

接下来我们将以 Centos 为例搭建 Git 服务器。

### 1、安装Git

```
$ yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel perl-devel
$ yum install git
```

接下来我们 创建一个git用户组和用户，用来运行git服务：

```
$ groupadd git
$ useradd git -g git
```

### 2、创建证书登录

收集所有需要登录的用户的公钥，公钥位于id_rsa.pub文件中，把我们的公钥导入到/home/git/.ssh/authorized_keys文件里，一行一个。

如果没有该文件创建它：

```
$ cd /home/git/
$ mkdir .ssh
$ chmod 755 .ssh
$ touch .ssh/authorized_keys
$ chmod 644 .ssh/authorized_keys
```



### 3、初始化Git仓库

首先我们选定一个目录作为Git仓库，假定是/home/gitrepo/runoob.git，在/home/gitrepo目录下输入命令：

```
$ cd /home
$ mkdir gitrepo
$ chown git:git gitrepo/
$ cd gitrepo

$ git init --bare runoob.git
Initialized empty Git repository in /home/gitrepo/runoob.git/
```

以上命令Git创建一个空仓库，服务器上的Git仓库通常都以.git结尾。然后，把仓库所属用户改为git：

```
$ chown -R git:git runoob.git
```

### 4、克隆仓库

```
$ git clone git@192.168.45.4:/home/gitrepo/runoob.git
Cloning into 'runoob'...
warning: You appear to have cloned an empty repository.
Checking connectivity... done.
```

192.168.45.4 为 Git 所在服务器 ip ，你需要将其修改为你自己的 Git 服务 ip。

这样我们的 Git 服务器安装就完成。