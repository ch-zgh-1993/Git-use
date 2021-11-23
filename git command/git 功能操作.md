1. git 推分支到另一个仓库, 保留历史记录
```
* clone new.git 新项目git不能有内容
* git checkout -b new-program
* git remote set-url origin old.git
* git fetch
* git checkout -b new-branch
* git log
* git remote set-url origin new.git
* git push origin new-branch
```
