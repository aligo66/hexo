---
title: git分支
date: 2017-03-07 13:33:20
tags: git
categories: 前端开发
---

<img src="https://ww2.sinaimg.cn/large/006tNbRwly1fde7z56q72j30fm09mt8s.jpg" width="500px" style="border:none;">
<!--more -->
几乎所有的版本控制系统都以某种形式支持分支。使用分支的目的是你可以把你的工作从开发主线上奋力开来，以免影响主线。分支的主要内容是我从廖老师的git教程总结的。
## 1.创建分支与合并分支
在工作中，可能会遇到开发网站时，为了实现某个新的需求，创建一个分支，在这个分支上展开工作。正在此时，你同事遇到问题，需要修补，你需要马上切换到你的线上分支，为这个紧急任务新建一个分支，并在其中修复它，在通过测试后，切换回到线上分支，然后合并这个修补分支，最后将改动推送到线上分支，切换到你最初的分支上，继续工作。

```
￥git checkout -b iss53
Switched to a new branch "iss53"
等价于  $git branch iss53           创建一个分支
       $git checkout iss53         切换到iss53分支
```
你继续在#53问题上工作，并且做了一些提交，在此过程中，iss53分支在不断地推进，因为你已经检出到该分支(也就是说，你的HEAD指针指向了 iss53分支)  

 然后，用git branch 命令查看当前分支：

```
$git branch
*iss53
 master
```
git branch 命令会列出所有的分支，当前分支会标一个*号。
然后我们呢就可以在iss53上分支上正常提交，比如对readme.txt做个修改，然后提交：

```
$git add readme.txt
$git commit -m"branch test"
[isss53 fec145a] branch test
 1 file changed, 1 insetion(+)

```
现在，iss53分支的工作完成，我们就可以切换到master分支：

```
$git checkout master
Switched to branch 'master'

```
切换到master分支后，再查看到readme.txt 文件。发现刚才的内容不见了！因为那个提交实在dev上，而master分支在此刻的提交点并没有变，是因为我们没有合并。

```
$git merge iss53
Updating d17efd8 ..fec145a 
Fast-ward
 readme.txt |  1+
 1 file changed, 1 insertion(+)

```
git merge命令用于合并指定分支到当前分支。合并后，再查看readme.txt内容就可以看到，和iss53分支的最新提交是一样的。Fast-ward信息，是指这次合并模式是"快进模式"，也就是直接把master指向iss53的当前提交，所以合并速度非常快。
当然也不是每次合并都能fast-ward
合并完成后，就可以放心删除iss53分支：

```
$git branch -d iss53

```
删除后就只剩下master分支了

```
$git branch
*master

```
应为创建、合并和删除分支很快，一般都是使用分支完成任务后，先合并再删除分支。
## 2.解决分支冲突
有时会出现合并失败
比如创建了一个新的分支 feature分支，在新的分支上开发

```
$git checkout -b feature1
Switched to a new branch 'feature1'

```
在分支上修改了某些文件，在feature1分支上准备提交

```
$git add readme.txt
$git commit -m" AND simple"
[feature1 75a857c] AND simple
 1 file changed, 1 insertion(+), 1 deletion(-)

```
切换到master分支：

```
$git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 1 commit.

```
Git还会自动提示我们当前master分支比远程分支要超前一个提交。
在master分支上把readme.txt 文件的最后一行进行修改

```
$git  add readme.txt
$git commit -m "& simple"
[master 400b400] &simple
 1 file changed, 1 insertion(+), 1 deletion(-)

```
现在，master分支和feature1分支各自都有了新的提交，这样，Git无法执行"快速合并'，只能试图把各自修改合并起来，但是这种合并就会有冲突

```
$git merge feature1
Auto-merging readme.txt
CONFLICT (content): Merge conflict in readme.txt
Automatic merge failed; fix conflicts and then commit the result.

```
出现了失败，说明有冲突，必须手动解决冲突再提交，git status会告诉我们冲突的文件。
当Git无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成。用git log --graph命令可以看到分支合并图。
## 3.分支管理策略
通常，合并分支时，如果可能，Git会用Fast forward模式，但这种模式下，删除分支后，会丢到分支信息。  
如果要强制禁用Fast-ward模式，Git就会merge时生成一个新的commit,这样，从分支历史上就可以看出分支信息。使用 --no-ff 方式的merge

```
$git checkout -b dev
Switched to a new branch 'dev'

```
修改readme.txt文件，并提交一个新的commit
现在，我们切换到master:

```
$git checkout master
Switched to branch 'master'

```
准备合并dev分支，注意 --no-ff 参数，表示禁用Fast-forward：

```
$git merge --no-ff -m"merge with no-ff" dev
Merge made by the 'recursive' strategy.
 readme.txt |   1+
 1 file changed, 1 insertion(+)

```
因为本次合并要创建一个新的commit，所以加上 -m参数,描述提交的东西，快速何必，不会看到历史记录。

## 4.分支策略
在实际开发中，我们应该按照几个基本原则进行分支管理：

首先，master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；

那在哪干活呢？干活都在dev分支上，也就是说，dev分支是不稳定的，到某个时候，比如1.0版本发布时，再把dev分支合并到master上，在master分支发布1.0版本；

你和你的小伙伴们每个人都在dev分支上干活，每个人都有自己的分支，时不时地往dev分支上合并就可以了。

## 5.多人协作
当你从远程仓库克隆时，实际Git自动把本地的master分支和远程的master分支对应起来了,并且，github远程仓库的默认名称是 origin.  
查看远程仓库信息，用git remote

```
$git remote origin

```
或者用git remote -v

```
$git remote -v
origin	git@github.com:wanqing19954/learn.git (fetch)
origin	git@github.com:wanqing19954/learn.git (push)

```
上面显示了可以抓取和推送的origin的地址。如果没有推送权限，就看不到push的地址

**推送分支**  
推送分支，就是把该分支上的所有本地提交推送到远程仓库。推送时，要指定本地分支，Git就会把该分支推送到远程库对应的远程分支上：

```
$git push origin master

```
如果要推送其他分支，例如dev,就直接

```
$git push origin dev

```
但是，并不是一定要把分支往远程推送，那么哪些分支需要推送，哪些不需要呢？

