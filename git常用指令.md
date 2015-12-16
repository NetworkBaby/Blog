# git常用指令

`git branch` 查看本地所有分支

`git status` 查看当前状态

`git commit` 提交

`git branch -a` 查看所有分支

`git branch -r` 查看远程所有分支

`git commit -am "init"` 提交并且加注释

`git remote add origin git@github.com:yourname/repository` 关联

`git push origin master` 将文件推送到服务器

`git remote show origin` 显示远程origin里的资源

`git push origin master:develop` 将本地库与远程库关联

`git checkout --track origin/dev` 切换远程dev分支

`git branch -D master develop` 删除本地库develop

`git checkout -b dev` 建立新分支dev并切换

`git merge origin/dev` 将远程分支dev与当前分支进行合并

`git checkout dev` 切换到本地dev分支

`git remote show` 查看远程库

`git add .` add新增和修改的，不包括删除的

`git add -u` add修改和删除的，不包括新增的

`git add -A` add所有新增、修改和删除的

`git rm file` 从git中删除指定文件

`git clone git://github.com/...` 从服务器clone代码库

`git config --list` 查看配置

`git ls-files` 查看已提交的文件

`git commit -v` 查看commit的差异

`git log` 查看commit日志

`git diff` 查看尚未暂存的更新

`git rm a.a` 移除文件（从暂存区和工作区中删除）

`git rm --cached a.a` 移除文件（只从暂存区中删除）

`git rm -f a.a` 强行移除修改后文件（从暂存区和工作区中删除）

`git diff --cached`或`git diff --staged` 查看尚未提交的更新

`git stash push` 将文件push到一个临时空间中

`git stash pop` 将文件从临时空间pop下来

`git pull` 本地与服务器同步

`git fetch` 相当于从远程获取最新版本到本地，不会自动merge
