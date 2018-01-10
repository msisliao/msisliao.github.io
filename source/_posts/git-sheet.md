---
title: git常用命令清单
date: 2016-02-15 17:46:19
categories:
  - web前端技术
tags: [git]
---


##  生成ssh

- **第一步输入用户名密码**

  $ git config --global user.name "yourName"

  $ git config --global user.email "yourEmail"

- **第二步生成ssh 全部按回车键**
  $ ssh-keygen -t rsa -C “yourEmail”

- 最后把生成的公钥`id_rsa.pub`添加到github上

##  常用命令

<span style="color:#999;font-size:14px;">克隆远程项目</span>
 git clone [url]

<span style="color:#999;font-size:14px;">初始化本地仓库</span>
  git init

<!--more-->


<span style="color:#999;font-size:14px;">切换分支</span>
  git checkout master

 <span style="color:#999;font-size:14px;">添加指定目录到暂存区，包括子目录</span>
  git add [dir]

 <span style="color:#999;font-size:14px;">添加当前目录的所有文件到暂存区</span>
  git add .

<span style="color:#999;font-size:14px;">进行一次commit</span>
  git commit -m '提交说明'

<span style="color:#999;font-size:14px;">提交代码到分之上</span>
  git push origin master

<span style="color:#999;font-size:14px;">相当于从远程获取最新的版本并merge(合并）到本地的master分支，相当于git fetch和git merge</span>
  git pull origin master

<span style="color:#999;font-size:14px;">创建一个分支，名字为branch-name</span>
  git branch branch-name

## 隆重的分割线

 <span style="color:#999;font-size:14px;">删除工作区文件，并且将这次删除放入暂存区</span>
  git rm [file1] [file2] ...

 <span style="color:#999;font-size:14px;">停止追踪指定文件，但该文件会保留在工作区</span>
  git rm --cached [file]

 <span style="color:#999;font-size:14px;">改名文件，并且将这个改名放入暂存区</span>
  git mv [file-original] [file-renamed]

<span style="color:#999;font-size:14px;">删除分支名</span>
   git branch -d branch-name

<span style="color:#999;font-size:14px;">删除远程的test分支</span>
   git branch -d -r origin/test

<span style="color:#999;font-size:14px;">提交本地的test分支做为远程的master分支</span>
   git push origin test:master

<span style="color:#999;font-size:14px;">合并分支</span>
   git merge origin/master

<span style="color:#999;font-size:14px;">显示所有的分支，包括本地和远程的分支</span>
   git branch -a

<span style="color:#999;font-size:14px;">修改本地分支的名字  ，ori-branch为原来的分支名，dist-branch要修改后的分支名</span>
   git branch -m ori-branch dist-branch

<span style="color:#999;font-size:14px;">从远程的master分支下载最新的版本到本地，但是不会自动merge(合并）</span>
   git fetch  origin master

<span style="color:#999;font-size:14px;">把远程的master分支下载到本地的remote-branch分支，这个remote-branch 分支会被自动创建，不存在的时候</span>
   git fetch origin master:remote-branch

<span style="color:#999;font-size:14px;">比较现在所处的分，跟remote-branch分支有什么差别</span>
   git diff remote-branch

<span style="color:#999;font-size:14px;">把remote-branch分支合并到现在的分支上面，如果没有冲突，会自动完成合并。当出现冲突的时候，需要手动修改conflict ,再提交commit</span>
   git merge --no-ff remote-branch

<span style="color:#999;font-size:14px;">比较本地的master分支和origin/master分支的差别</span>
   git log -p master ../origin/master

<span style="color:#999;font-size:14px;">基于base_branch_name分支一个名为new_branch的分支</span>
   git checkout -b new_branch base_branch_name

<span style="color:#999;font-size:14px;">基于master分支创建一个没有父节点的分支，名字为gh-pages</span>
   git checkout --orphan gh-pages

<span style="color:#999;font-size:14px;">添加远程仓库，另名为origin</span>
   git remote add origin git@github.com:username/project-name.git

<span style="color:#999;font-size:14px;">删除远程分支的另名，origin,如果要重新添加，就要用git remote add url</span>
   git remote rm origin
