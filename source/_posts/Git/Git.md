---
title: Git基本命令点总结
categories: []
date: 2018-11-28 16:57:51
cover: https://linux.cn/data/attachment/album/201804/20/162427h1tuyumjtud0y1zz.jpg
tags: git命令集
keywords: 前端 
---

### 创建git本地仓库
>* 初始化仓库 git init
>* 添加文件到仓库 git add .
>* git commit -m "备注信息"
-------

### 查看远程提交日志
>* git log
-------

### 把文件退回到上一个版本
>* git reset --hard HEAD^
>* 2.回到最新版本
> * git reset --hard id号
>* 3.查看历史的id号
> * git reflog 
-------

### 查看工作区状态
>* git status
-------

### 撤销工作区的修改到最近一次上传
>* git checkout -- 文件名称
-------

### 远程建库并上传
>* git remote add origin git地址
>* git push -u origin 分支名
-------

### 远程库克隆
>* git clone git地址
-------

### 创建分支并切换分支
>* git checkout -b 分支名
>* 分解为
	创建分支：git branch 分支名
	切换分支：git checkout 分支名
>* 2.检查当前分支：
	git branch
>* 3.合并分支
	git merge 分支名
>* 4.删除分支
>* git branch -d 分支名
-------

### 解决冲突
>* 查看冲突文件  git status
>* 查看分支合并图 git log --graph
-------

### 临时储存分支
>* git stash
>* 1.恢复临时储存分支
1.1:查看储存的id 
git stash list
1.2:恢复储存分支（两种方法）
1.2.3方法一:
恢复：git stash apply id名 如stash@{0}
删除：git stash drop
1.2.3方法二：
>* 自动恢复删除：git stash pop
-------

### 查看远程库信息
>* git remote
>* 查看详细信息 
>* git remote -v
>* 注：如果没有推送权限，就看不到push的地址
-------

### 推送分支
>* git push origin 分支名
-------

### 多人协作中的问题
>* 1.git pull 失败 提示no tracking information
	原因：没有指定本地分支与远程分支连接 
	解决： git branch 【--set-upstream 本地分支 远程分支】