# Git

## 学习指南

### 推荐资料

* [图书][Git权威指南](http://product.dangdang.com/21108669.html)
* [图书][Git版本控制管理](http://product.dangdang.com/23657840.html)
* [图书][精通Git](http://product.dangdang.com/25166975.html) GitHub联合创始人倾心之作，没有版本控制概念的读者也可轻松入门，涵盖Git常见工作场景，有效帮助程序员提升软技能。
* [网站][gitignore][A collection of .gitignore templates](https://github.com/github/gitignore)
* 很多IDE提供gitignore插件，比如VS Code的[gitignore插件](https://marketplace.visualstudio.com/items?itemName=codezombiech.gitignore)
* [推荐][网站][Git入门图文教程(1.5W字40图)🔥🔥--深入浅出、图文并茂](https://www.cnblogs.com/anding/p/16987769.html)

* [工具][Mercurial](https://www.mercurial-scm.org) 源码控制管理工具。(Mercurial is a free, distributed source control management tool.)
* [工具][SourceTree](https://www.sourcetreeapp.com/) 版本控制管理工具。(The friendly GUI for Mercurial and Git on your Mac.

### 常用命令

* git
* git --version
* git help
  * git help status
* git add
  * git add .
* git commit
  * git commit -m 'message'
  * git commit --amend -m "New commit message"
* git push
  * git push --set-upstream origin dev
    * 推送本地分支到远程
* git pull
* git fetch
* git config
  * git config user.name
  * git config --global user.name "rm57"
  * git config –global user.email rollin.r.ma@newegg.com
  * git config –l
* git init
* git status
* git rm
  * git rm –cached readme.txt
* git log
  * git log --pretty=format:"%h %s" –graph
* git tag
  * git tag recommend-watch.1.0.0.20170214D1
  * git tag -d recommend-watch.1.0.0.20170214D1
  * git tag –l
  * git push origin 0.0.1
    * 推送本地tag到远程仓库
* git push
  * git push origin recommend-watch.1.0.0.20170214D1
  * git push --force
    * 强制覆盖
* git diff
  * git diff hello.java
  * git diff 0a70dd 6fc267
* git branch
  * git branch
    * git branch --list
    * 查看本地当前分支
  * git branch dev
    * 创建本地分支dev
    * 后续操作：
      * git checkout dev
        * 切换到分支dev
      * git push --set-upstream origin dev
        * 推送分支dev到远程
  * git branch -d dev
    * 删除分支
  * git branch -r
    * 显示远程分支
  * git push origin -d dev
    * 删除远程分支
    * git push origin :dev
      * 删除远程分支的另一种方法
  * git remote update origin --prune
    * 更新远程分支信息到本地
  * git branch -a
    * 显示本地和远程所有分支信息
* git show-branch
* git stash
  * git stash list
  * git stash pop
* git clone
* git remote –v
  * git remote set-url origin *
* git rebase
* git checkout
  * git checkout .
    * 本地所有修改的。没有的提交的，都返回到原来的状态。
  * git checkout master
    * 切换到master分支
* git reset
  * git reset --hard HEAD~1
* git merge
  * git merge feature-user
    * 合并feature-user到当前分支
* git reflog
* git show
* git bisect
* git grep
* git cherry-pick

### Q&A

* merge 和 rebase 的区别
  * [合并分支中rebase和merge的区别](https://juejin.cn/post/7123826435357147166)
    * 这篇文章是个典型应用（观察每个Commit Graph体验效果）
      * 初始化仓库
        * git init
        * git status
        * touch 1.txt
        * git add .
        * git commit -m 'add 1.txt'
      * 用户开发新功能
        * git branch feature1
        * git checkout feature1
        * touch f1.txt
        * git add .
        * git commit -m 'add f1.txt'
        * touch f2.txt
        * git add .
        * git commit -m 'add f2.txt'
      * 模拟其他用户合并记录到master
        * git checkout master
        * touch 2.txt
        * git add .
        * git commit -m 'add 2.txt'
      * 用户使用rebase功能，合并master记录，并保持记录结构清晰
        * git checkout feature1
        * git rebase master
        * ls -l
    * 私有分支可使用rebase，公有的不要用。
  * [一文搞懂 git rebase](https://juejin.cn/post/7038093620628422669)
  * [git rebase和git merge有什么区别？](https://joyohub.com/2020/04/06/git-rebase/)
  * [Git Rebase vs Git Merge: Which is Better?](https://www.edureka.co/blog/git-rebase-vs-merge)

    | Merge                                                                                           | Rebase                                                                                             |
    | :---------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------- |
    | Git merge is a command that allows you to merge branches from Git.                              | Git rebase is a command that allows developers to integrate changes from one branch to another.    |
    | In Git Merge logs will be showing the complete history of the merging of commits.               | Logs are linear in Git rebase as the commits are rebased                                           |
    | All the commits on the feature branch will be combined as a single commit in the master branch. | All the commits will be rebased and the same number of commits will be added to the master branch. |
    | Git Merge is used when the target branch is shared branch                                       | Git Rebase should be used when the target branch is private branch                                 |
