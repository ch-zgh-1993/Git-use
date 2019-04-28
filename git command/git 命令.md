/*
* @Author: Zhang Guohua
* @Date:   2018-11-12 19:57:51
* @Last Modified by:   zgh
* @Last Modified time: 2018-11-12 20:08:39
* @Description: create by zgh
* @GitHub: Savour Humor
*/
# git操作

## 安装
    ```
    sudo apt-get install git-core
    ```
## 全局配置
1. 获取配置
    ```
        git config --list
    ```
1. 配置用户名邮箱
    ```
        git config --global user.name 
        git config --global user.email
    ```
2. 初始化操作
    ```
        git init // 进入项目目录
        git status // 显示哪些将被提交，哪些将被忽略,查看分支信息
        git add // 添加提交文件
        
        
    ```
3. 配置github ssh
    ```
    ssh -T git@github.com // 测试连接到github
    ssh-keygen -t rsa -C "your email" // 创建本地SSH key
    // 在github 上添加，再尝试连接
    ```
4. 

## Remote 仓库
    ```
    git remote // 查看远程仓库
    git remote -v // 查看远程仓库的地址
    
    git remote add origin https/git地址 // origin为本地仓库名,代表远程主机 连接远程git 项目 url
    git remote add [-t <branch>] [-m <master>] [-f] [--[no-]tags] [--mirror=<fetch|push>] <name> <url> 
    
    git remote rename <old> <new> // 重命名本地名,会修改远程分支名
    
    git remote remove <name> // 移除远程仓库
    
    git remote set-head <name> (-a | --auto | -d | --delete | <branch>)
    git remote set-branches [--add] <name> <branch>…
    git remote get-url [--push] [--all] <name>
    git remote set-url [--push] <name> <newurl> [<oldurl>]
    git remote set-url --add [--push] <name> <newurl>
    git remote set-url --delete [--push] <name> <url>
    git remote [-v | --verbose] show [-n] <name>…
    git remote prune [-n | --dry-run] <name>…
    git remote [-v | --verbose] update [-p | --prune] [(<group> | <remote>)…]
    
    ```


## 项目操作
1. fetch
    ```  fetch
        git fetch origin master // 下载远程代码，origin本地仓库名，master为本地分支名
        git diff origin/master // 比较本地和远程代码
       
    ```
    上面代码的含义：
    1. fetch 从远程获取最新版本到本地，不自动merge。
    2. 比较本地的差别
    3. 在进行合并
    更安全，主动决定是否merge
    
    拉取他有你没有的代码。
    
***

2. pull
    ```
    git pull 本地仓库名 远程分支 // orgin master
    ```
    在push之前进行pull操作的意义在于，当你们两个人的代码改动冲突较大时，必须选择保留其他人代码。git的push不带merge操作。
    pull操作同步到本地并自带merge
3. commit
    ```
    git commit -m 'test commit' // 提交 注释说明
    ```

4. clone
    ```
    git clone url 目标文件夹 // 克隆别人和自己的项目 
    
    git clone [--template=<template_directory>]
      [-l] [-s] [--no-hardlinks] [-q] [-n] [--bare] [--mirror]
      [-o <name>] [-b <name>] [-u <upload-pack>] [--reference <repository>]
      [--dissociate] [--separate-git-dir <git dir>]
      [--depth <depth>] [--[no-]single-branch] [--no-tags]
      [--recurse-submodules[=<pathspec>]] [--[no-]shallow-submodules]
      [--jobs <n>] [--] <repository> [<directory>]
    ```
6. show 
    查看自己的提交

7. push
    ```
    git push origin master  // 将本地分支代码推送到远程主机的master分支
    git push -u origin master // 在初次提交使用 -u 会将本地分支与远程master分支关联起来，简化后续操作。
    ```
8.  merge
    ```
     git merge origin/master // 将远程的master分支merge 到本地，若无冲突，则merge顺利。
    ```
9. checkout
使用版本库中的文件替换本地工作区的文件，一件还原至版本库中的代码。
    ```
    git checkout - a.text 
    ```
## 版本操作
    ```
    git reset --hard HEAD^ // 返回上一个版本 HEAD表示当前版本，上个版本是HEAD^,上上一个版本是HEAD^^ 第几个版本可以写 HEAD~n
    git reset --hard 99 // 返回版本号为99的版本
    git log --pertty=online 文件名 // 查看当前文件提交的记录
    git watchanged 文件名   // 查看文件提交的详情，人，时间，记录
    
    <!--对比版本-->
    git diff commit-id1 commit-id2 --stat // 比较版本差异
    ```
    
## Branch 分支操作
    ```
    git branch // 查看分支 当前分支前面会有*标识
    git branch -v // 查看分支最后一次提交
    git branch dev // 创建分支
    
    git checkout dev // 切换分支
    git checkout -b <local_branch_name> remote/<remote_branch_name>
    
    git merge dev // 合并分支到当前分支
    
    
    <!-- 命令选项 -->
    git branch --merged // 查看哪些分支已经合并到当前分支
    git branch -d dev // 合并过的列表中的分支，可以用 此命令删除
    git branch --no-merged // 查看哪些分支还没有合并，这些分支使用上述命令不可删除
    git branch -D dev // 可以使用 -D 强制删除
    
    git branch --set-upstream-to=origin/<remote_branch_name> <local_branch_name> // 设置追踪分支，设置后，可以使用简化操作。
    git branch -u origin/<remote_branch_name> <local_branch_name> // 同上
    
    <!--对比分支-->
    git diff b1 b2 --stat // 比较两个分支的文件差异
    
    ```
    
## 提交历史日志操作
```
git log filename // 查看远程仓库提交历史 -p 显示每次提交修改的情况 -2 显示最近两次提交的历史 Q退出日志

git show 提交id filename // 查看某次提交时文件变化

git reflog // 记录命令历史

```

## Git Add
```
git add filename|. //增加到提交列表
git add -all|-A     //增加所有改动到提交列表，包括删除文件
git add --ignore-removal <pathspec> // 增加但忽略移除文件
git add --all <pathspec> // 将让你删除文件


```
## Git rmove
```
git rm -r --cached . // 删除本地缓存，更新文件追踪状态
git rm // 移除提交文件
git rm a.md // 当删除一些版本库中的文件，需要提交时，先要将文件rm,再进行提交。
```


 
    


