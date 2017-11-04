---
title: git常用操作及总结
date: 2017-03-06 13:16:17
tags: git
categories: 前端开发
---
<img src="https://ww4.sinaimg.cn/large/006tNbRwly1fdd1zpad2mj30i80bz0t5.jpg" width="400px">
<!--more -->  
　　如果你已经安装了git的话，主要内容告诉你在使用Git完成各种工作中将使用的各种命令。如果你看完了主要内容，应该就能配置初始化一个仓库(repository)、开始或停止跟踪(track)文件和文件模式、如何迅速而简单地撤销错误操作、如何浏览你的项目的历史版本以及不同提交(commits)间的差异、如何向你的远程仓库推送(commit)、以及如何从你的远程仓库拉取(pull)文件。  
# <font color="red">一.获取git仓库</font>  
　　有两种取得Git项目仓库的方法。第一种是在现有项目或目录下导入所有文件到Git中；第二中是从一个服务器或者github克隆一个现有的Git仓库。
## 1.在你新建的文件夹来建一个新的仓库  
如果你打算使用Git来对现有的项目进行管理，你只需要进入该项目所在的文件夹并且输入  

```
cd learn                                   进入你新建文件夹中
git init                                    建立一个新的仓库

```
　　如果你在一个已经存在文件的文件夹里建立了一个新仓库，你应该开始跟踪这些文件并提交。 你可通过 git add 命令来实现对指定文件的跟踪，然后执行 git commit 提交：

```
$ git add .
$ git add work
$ git commit -m" new version"

```
一般，刚建立的文件夹，仓库都是新的。不需要上面的那些命令  
  
  
## 2.克隆你以前的仓库或者别人的仓库
　　如果你想获得一份已经存在的Git仓库的话，比如，你想为某个开源项目贡献自己的一份力，这时就要用到git clone命令。git克隆的是Git仓库服务器上的几乎所有数据。而不是仅仅赋值完成你的工作所需要文件。当你执行git clone命令的时候，默认配置下远程仓库中的每一个文件的每一个版本都将被拉去下来。可以用下面的命令

```
$ git clone http://github.com/jack/learn

```
这会在当前目录下创建一个名为“learn”的文件夹在你的电脑上，并在这个目录下初始化一个.git文件夹，从远程仓库拉取下所有数据到你的文件夹里，如果你想自定义本地仓库的名字，可以在后面 添加 你的名字
# <font color="red">二、记录每次更新到仓库</font>   
　　现在我们手上有了一个Git仓库，并从这个仓库取出了所有文件的工作拷贝。接下来，对这些文件做了修改，在完成了一个阶段的目标后，提交每次跟新到仓库。  
　　一般文件都处于未修改，已修改，或已放入暂存区。工作目录中除已跟踪文件以外的所有文件都属于未跟踪文件，它们即不存在于上次快照的记录中，也没有放入暂存区。初次克隆某个仓库的时候，工作目录中的所有文件都属于已跟踪文件，并处于未修改状态。  
　　编辑修改某些文件之后，由于上次提交后，你对它们做了修改，Git将它们标记为已修改文件。我们逐步将这些修改过的文件放入暂存区，再提交素有暂存了的修改
　　文件从本地 到暂存区 到远程仓库。
简称文件处于什么状态，可以用 git status 简写“git st",如果在克隆仓库后立即使用git st 会看到没有可以提交的，说明都没有被修改。

```
$ git status
on branch master
nothing to commit ,working directory clean

```
　　这些信息，告诉你当前目录没有出现任何处于未跟踪状态的新文件，否则Git会列出来，最后改命令还显示了当前所在分支，并告诉你这个分支同远程服务器上对应的分支没有偏离。现在分支名是"master",这是默认的分支名。我们在Git分支后会降到。
现在，让我们在项目下新建一个新的README文件，如果之前并不存在这个文件，使用 git status 命令你会看到新的未跟踪文件：

```
$ git status
on branch master
Untracked files:
	(use "git add <file>.." to  include in what will be  commited)
	README
nothing added to commit but untracked files present (use "git add" to track)

```
在状态报告中可以看到新建的README文件出现在Untracked files 下面。未跟踪的文件以为这Git在之前的快照中没有这些文件。  
## 1.添加新文件  
使用命令 git add 开始跟踪一个文件。所以，要跟踪README文件，运行

```
$ git add README

```
此时再运行git status 命令， 会看到README 文件已被跟踪，并成功并处于暂存状态：

```
$ git status
on branch master
changes to be commited:
 (use "git reset HEAD <file>..." to unstage)
 new file: README

```
　　只要在Change to be commited 这行下面的，就说明是已暂存状态，如果此时提交，那么该文件此时此刻的版本将被留存在历史历史记录中。  
## 2.暂存已修改文件
　　现在我们来修改一个已被跟踪的文件。如果你修改了一个名字为index.html的已被跟踪文件
然后运行 git status 命令，会看到以下内容：

```
$ git status
on branch master
change to be commited:
	(use "git reset HEAD <file>.." to unstage)
	new file: README
Changes not staged for commit:
	(use "git add <file>..." to upadte what will be  commited)
	(use "git checkout --<file>.." to discared changes in working directory)
	modified: index.html

```
　　文件index.html出现在Changes not staged for commit 这行下面，说明已跟踪文件的内容发生了变化，但还没有放到暂存区，需要git add 命令

```
$ git add index.html
$ git status
on branch master
Changes to be commited:
	(use "git reset HEAD <file>..” to unstage)
new file: README
modified: index.html

```
　　现在两个文件都已被暂存，下次提交时就会一并记录到仓库，假设此时你想要在 index.html 里再加条注释，重新编辑存盘后，准备提交。再git status 你会发现：

```
$ vim index.html
$ git st
on branch master
changes to be commited:
	(use "git reset HEAD <file>..." to unstage)
	new file: README
	modified: index.html
changes not staged for commit:
	(use "git add <file>..." to discard changes in working directory)
	(use "git checkout -- <file>..." to discard changes in working directory)
	modified: index.html

```
　　出现了两个 index.html，同时出现在暂存区和非暂存区。git只不过暂存了你运行git add 命令的版本，如果你现在提交。idnex.html的版本是你最后一次运行 git add 命令的那个版本。而不是你运行 git commit 时，在工作目录中的当前版本，所以你需要重新git add。  
## 3.查看已暂存和未暂存的修改
　　如果git status，输出不知道具体修改了什么，可以用git diff命令
假如再次修改README 文件后暂存，然后编辑index.html文件后先不暂存,查看尚未暂存的文件更新了哪些部分，不加参数，直接输入 git diff

```
$ git diff
diff --git a/index.html b/index.html
--- a/index.html
+++ b/index.html
@@ -65,7 +65,8 @@ branch directly, things can get messy.
 Please include a nice description of your changes when you submit your PR;
 if we have to read the whole diff to figure out why you're contributing
 in the first place, you're less likely to get feedback and have your change
-merged in.
+merged in. Also, split your changes into comprehensive chunks if your patch is
+longer than a dozen lines.

 If you are starting to work on a particular area, feel free to submit a PR
 that highlights your work in progress (and note in the PR title that it's

```
## 4.提交更新
现在的暂存区已经可以提交了，再此之前看看是否有没被提交的

```
$ git commit -a -m 'added new benchmarks'
[master 83e38c7] added new benchmarks
 1 file changed, 5 insertions(+), 0 deletions(-)

```
## 5.移除文件
　　要从git中移除某个文件，就必须要从已跟踪文件清单中移除（确切的说，是从暂存区中移除），然后提交，可以用 git rm 命令完成此项工作，并连带从工作目录中删除指定的文件，这样以后就不会出现在未跟文件清单中了。
如果只是本地文件夹里删除文件，运行git status 时就会看到

```
$ rm index.html
$ git status
on branch master
Your branch is up-to-date with 'origin/master'.
Changes not staged for commit:
	(use "git add/rm <file>..." to update what will be commited)
	(use "git checkout -- <file>..." to discard changes in working directory)
	
	deleted:	index.html

```
然后在运行git rm 记录此次移除文件的操作：

```
$git rm index.html
rm 'index.html'
$git st
on branch master
Changes to be commited:
	(use "git reset HEAD <file>..." to unstage)
	
		deleted:  	index.html

```
　　下一次提交时，该文件就不再纳入版本管理了，如果删除之前修改过而且已经放到暂存区，则必须要用强制删除选项-f  
如果只是想将它从git仓库里（即从暂存区域移除），但仍然希望保留在当前工作目录中，换句话说，你想让文件保留在磁盘中，但是不想被git 追踪，可以使用 --cached 选项

```
$ git rm --cached README

```
## 6.移动文件
要在git 中对文件改名，可以这么做：

```
$ git mv file_from file_to

```
你会明白关于重命名操作的说明

```
$ git mv README.md README
$ git status
on branch master
Changes to be commited:
	(use "git reset HEAD <file>..." to unstage)
	
	renamed: README.md -> README

```
其实，git mv 相当于运行了下面的三条命令

```
$ mv README.md README
$ git rm README.md
$ git add README

```
如此分开操作，也是重命名
# <font color="red">三、查看提交历史</font>
　　在提交了若干更新，有或者克隆了某个项目之后，你也许想回顾选下提交历史。可以用git log 命令
我从github 上clone 一个项目用于演示

```
git clone https://github.com/schacon/simple-progit

```
　　然后在此项目中运行git log, 应该会看到下面的输出：

```
$ git log
commit ca82a6dff817ec66f44342007202690a93763949
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    changed the version number

commit 085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Sat Mar 15 16:40:33 2008 -0700

    removed unnecessary test

commit a11bef06a3f659402fe7563abf99ad00de2209e6
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Sat Mar 15 10:31:28 2008 -0700

    first commit

```
　　git log 会按提交时间列出所有的更新，最新的在最上面。正如你所看到的，这个命令会列出每个SHA-1校检、作者的名字和电子邮件地址，提交时间和提交说明  
一个常用的选项是 -p 用来显示每次提交的内容差异，你也可以加上 -2 来仅显示最近两次提交

```
$ git log -p -2
commit ca82a6dff817ec66f44342007202690a93763949
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    changed the version number

diff --git a/Rakefile b/Rakefile
index a874b73..8f94139 100644
--- a/Rakefile
+++ b/Rakefile
@@ -5,7 +5,7 @@ require 'rake/gempackagetask'
 spec = Gem::Specification.new do |s|
     s.platform  =   Gem::Platform::RUBY
     s.name      =   "simplegit"
-    s.version   =   "0.1.0"
+    s.version   =   "0.1.1"
     s.author    =   "Scott Chacon"
     s.email     =   "schacon@gee-mail.com"
     s.summary   =   "A simple gem for using Git in Ruby code."

commit 085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Sat Mar 15 16:40:33 2008 -0700

    removed unnecessary test

diff --git a/lib/simplegit.rb b/lib/simplegit.rb
index a0a60ae..47c6340 100644
--- a/lib/simplegit.rb
+++ b/lib/simplegit.rb
@@ -18,8 +18,3 @@ class SimpleGit
     end

 end
-
-if $0 == __FILE__
-  git = SimpleGit.new
-  puts git.show
-end
\ No newline at end of file

```
# <font color="red">四、撤销操作</font>  
　　在任何一个阶段，你都有可能想要撤销某些操作，这里，我们将会学习几个撤销你所做的修改  
有时候我们提交完了才发现漏掉了几个文件没有被添加，或者提交信息写错了。此时，可以运行带有 --amend 选项的提交命令尝试重新提交

```
$ git commit --amend

```
　　这个命令会将暂存中的文件提交。
如果你提交后发现忘记了暂存某些需要的修改，可以像下面这样操作

```
$ git commit -m 'initial commit'
$ git add  forgotten-file
$ git commit --amend

```
# <font color="red">五、远程仓库的使用</font>
　　为了能在任意Git项目上协作，你需要知道如何管理自己的远程仓库。远程仓库是指托管在网络上的版本库，你可以有好几个远程仓库，有的可以读，有的可以读写，与他人协作涉及管理远程仓库以及根据需要推送或拉去数据。管理远程仓库包括了解如何添加远程仓库、移除无效的仓库，管理不同的远程分支并定义他们是否被跟踪等等。在本节中，我们将介绍一部分远程管理的技能。  
## 2.查看远程仓库
　　如果你想查看你已经配置的远程仓库服务器，可以运行git remote 命令。它会列出你指定的每一个远程服务器的简写。如果你已经克隆了自己的仓库，那么至少应该能看到 origin- 这是Git 给你克隆的仓库服务器的默认名字

```
$ git clone http://github.com/schacon/ticgit
Cloning into 'ticgit'...
remote: Reusing existing pack: 1857, done.
remote: Total 1857 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (1857/1857), 374.35 KiB | 268.00 KiB/s, done.
Resolving deltas: 100% (772/772), done.
Checking connectivity... done.
$ cd ticgit
$ git remote origin

```
　　你也可以制定选项-v,会显示需要读写远程仓库使用的Git保存的简写与其对应的URL

```
$ git remote -v 
origin https://github.com/schacon/ticgit(fetch)
origin https://github.com/schacon/ticgit(push)

```
　　如果你的远程仓库不止一个，该命令会将它们全部列出。例如，与几个协作者合作的，拥有多个远程仓库的仓库看起来像这样

```
$cd grit
$git remote -v
bakkdoor  https://github.com/bakkdoor/grit (fetch)
bakkdoor  https://github.com/bakkdoor/grit (push)
cho45     https://github.com/cho45/grit (fetch)
cho45     https://github.com/cho45/grit (push)
defunkt   https://github.com/defunkt/grit (fetch)
defunkt   https://github.com/defunkt/grit (push)
koke      git://github.com/koke/grit.git (fetch)
koke      git://github.com/koke/grit.git (push)
origin    git@github.com:mojombo/grit.git (fetch)
origin    git@github.com:mojombo/grit.git (push)

```
　　这样我们可以轻松拉取其中任何一个用户的贡献。此外，我们大概还会有某些远程仓库的推送权限。

## 3.添加远程仓库  
　　之前提到并展示了如何添加远程仓库的示例，运行 git remote add <shortname><url> 添加一个新的远程Git仓库，同时指定一个你可以轻松引用的简写

```
$ git remote origin 
$ git remote add pb https://github.com/paulboone/ticgit
$ git remote -v
origin https://github.com/schacon/ticgit(fetch)
origin https://github.com/schacon/ticgit(push)
pb https://github.com/paulboone/ticigit(fetch)
pb https://github.com./paulboone/ticigit(push)

```
　　现在你可以在命令行中使用字符串pb来代替整个URL。例如，如果你想拉取Paul的仓库中有但你没有的信息，可以运行 git fetch pb

```
$ git fetch pb
remote: Counting objects: 43, done.
remote: Compressing objects: 100% (36/36), done.
remote: Total 43 (delta 10), reused 31 (delta 5)
Unpacking objects: 100% (43/43), done.
From https://github.com/paulboone/ticgit
 * [new branch]      master     -> pb/master
 * [new branch]      ticgit     -> pb/ticgit

```
　　现在Paul的master分支可以在本地通过pb/master访问到- 你可以将它合并到自己的某个分支中，或者如果你想要查看它的话，可以检出一个指向该点的本地分支  
## 4.从远程仓库中抓取与拉取
就如刚才所见，从远程仓库中获得数据，可以执行：

```
$ git fetch [remote-name]

```
　　这个命令会访问远程仓库，从中拉取你没有的数据。执行完成后，你将会拥有那个远程仓库中所有分支的引用，可以随时 合并或查看。  
如果你使用clone命令克隆了一个仓库，命令会自动将其添加为远程仓库并默认以”origin"为简写。所以，git fetch orgin 会抓取克隆(或上一次抓取)后新推送的所有工作。当准备好时你必须手动将其合并入你的工作。
　　如果你有一个分支设置为跟踪一个远程分支，可以使用git pull命令来自动抓取然后合并远程分支到当前分支。这对你来说可能是一个更简单或更舒服的流程；默认情况下，git clone命令会自动设置本地 master分支
跟踪克隆的远程仓库的master分支(或不管是什么名字的默认分支)。运行git pull通常会从最初克隆的服务器上抓取数据并自动尝试合并到当前分支  
## 5.推送到远程仓库
　　当你想分享你的项目时，必须将其推送到上游。这个命令很简单 git push [remote-name][branch-name]。当你想要将master分支推送到origin 服务器时，那么运行这个命令就可以

```
$ git push origin master

```
　　只有当你克隆服务器的写入权限，并且之前没有人推送过时，这条命令才生效。当你和其他人在同一时间克隆，他们先推送到上游然后你在推送到上游，你的推送就会被拒绝，你必须先将他们的工作拉取下来并将其合并进你的工作后才能推送。  
## 6.查看远程仓库
　　如果想要查看某一个远程仓库的更多信息，可以使用git remote show[remote-name] 命令。如果想以一个特定的缩写名运行这个命令，例如origin，会得到像下面的信息：

```
$ git remote show origin
*remote origin
 Fetch URL: https://github.com/schacon/ticgit
 Push  URL: https://github.com/schacon/ticgit
 HEAD branch: master
 Remote branches:
   master                               tracked
   dev-branch                           tracked
 Local branch configured for 'git pull':
   master merges with remote master
 Local ref configured for 'git push':
   master pushes to master (up to date)

```
　　它同样会列出远程仓库URL与跟踪分支的信息。这些信息非常有用，它告诉你正处于master分支，并且如果运行git pull，就会抓取所有的远程应用，然后将远程master分支合并到本地master分支。它也会列出拉取到的所有远程应用。  
## 7.远程仓库的移除与重命名
　　如果想要重命名引用的名字可以运行git remote rename 去修改一个远程仓库的简写名。例如，想要将pb重命名为paul,可以用git remote renmae 这样做：

```
$git remote rename pb paul
$git remote origin paul

```
　　值得注意的是这同样也会修改你的远程分支名字。那些过去引用pb/master的现在回引用paul/master。
如果因为一些原因想要移除一个远程仓库-你已经从服务器上搬走了或不想使用某一个特定的镜像了，又或者某一个贡献者不再贡献了-可以使用git
remote rm:

```
$git remote rm paul
$git remote origin

```
# <font color="red">六、打标签</font>  
　　像其他版本控制系统(vcs)系统一样，Git可以给历史中的某一个提交打上标签，以示重要。比较有代表性的是人们会使用这个功能来标记发布结点。
## 1.列出标签  
在Git中列出已有的标签是，只需要输入git tag:

```
$git tag
v0.1
v1.3

```
　　这个命令以字母顺序列出标签，但是它们出现的顺序并不重要
你也可以使用特定的模式查找标签。例如，Git自身的源代码仓库包含标签的数量超过500个。如果只对1.8.5系列感兴趣，可以运行：

```
$git tag -1 'v.1.8.5'
v1.8.5
v1.8.5-rc0
v1.8.5-rc1
v1.8.5-rc2
v1.8.5-rc3
v1.8.5.1
v1.8.5.2
v1.8.5.3
v1.8.5.4
v1.8.5.5

```
## 2.创建标签  
git使用两种主要类型的标签：轻量标签(light)与附注标签  
## 3.附注标签
　　在Git中创建一个附注标签是很简单的。最简单的方式是当你运行tag命令时指定-a选项：

```  
$git tag -a v1.4 -m 'my version 1.4'
$git tag
v0.1
v1.3
v1.4

```
　　-m选项指定了一条将会存储在标签中的信息。如果没有为附注标签指定一条信息，Git会运行编辑器要求你输入信息
通过git show 命令可以看到标签信息与对应的提交信息

```
$git show v1.4
tag 1.4
Tagger: Ben Straub <ben@straub.cc>
Date:   Sat May 3 20:19:12 2014 -0700

my version 1.4

commit ca82a6dff817ec66f44342007202690a93763949
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    changed the version number

```
　　你会看到显示了标签者的信息、打标签的日期时间、附注信息，然后显示具体的提交信息  
　　另一种给提交打标签的方式是使用轻量标签。 轻量标签本质上是将提交校验和存储到一个文件中 - 没有保存任何其他信息。 创建轻量标签，不需要使用 -a、-s 或 -m 选项，只需要提供标签名字：


```
$git tag v1.4-1w
$git tag
v0.1
v1.3
v1.4
v1.4-1w
v1.5

```
# <font color="red">七、设置别名</font>
## 1.常用命令缩写
git status 改成 git st  　git checkout 改成 git co  
git commit 改成 git ci　　git branch 改成 git br  
可以输入以下命令

```
$git config --global alias.co checkout
$git config --global alias.br branch
$git config --global alias.ci commit
$git config --global alias.st status

```
以上差不多就是git常用的所有命令，后面还有 关于 git 分支






