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

`git branch dev master` 从主分支master创建dev分支

`git branch -m dev dev_2` 将dev重命名为dev_2

`git checkout dev/master` 切换到dev/master分支

### 初始化版本库

`mkdir git` 创建git文件夹

`git init` 进入文件夹后执行，初始化版本库

`git remote add origin git@github.com:yourname/learn.git` 关联远程库learn

### git命令速查表

`git add` 添加至暂存区

`git add–interactive` 交互式添加

`git apply` 应用补丁

`git am` 应用邮件格式补丁

`git annotate` 同义词，等同于 git blame

`git archive` 文件归档打包

`git bisect` 二分查找

`git blame` 文件逐行追溯

`git branch` 分支管理

`git cat-file` 版本库对象研究工具

`git checkout` 检出到工作区、切换或创建分支

`git cherry-pick` 提交拣选

`git citool` 图形化提交，相当于 git gui 命令

`git clean` 清除工作区未跟踪文件

`git clone` 克隆版本库

`git commit` 提交

`git config` 查询和修改配置

`git describe` 通过里程碑直观地显示提交ID

`git diff` 差异比较

`git difftool` 调用图形化差异比较工具

`git fetch` 获取远程版本库的提交

`git format-patch` 创建邮件格式的补丁文件。参见 git am 命令

`git grep` 文件内容搜索定位工具
 
`git gui` 基于Tcl/Tk的图形化工具，侧重提交等操作

`git help` 帮助

`git init` 版本库初始化

`git init-db*` 同义词，等同于 git init

`git log` 显示提交日志

`git merge` 分支合并

`git mergetool` 图形化冲突解决

`git mv` 重命名

`git pull` 拉回远程版本库的提交

`git push` 推送至远程版本库

`git rebase` 分支变基

`git rebase–interactive` 交互式分支变基

`git reflog` 分支等引用变更记录管理

`git remote` 远程版本库管理

`git repo-config*` 同义词，等同于 git config

`git reset` 重置改变分支“游标”指向

`git rev-parse` 将各种引用表示法转换为哈希值等

`git revert` 反转提交

`git rm` 删除文件

`git show` 各种类型的对象

`git stage*` 同义词，等同于 git add

`git stash` 保存和恢复进度

`git status` 显示工作区文件状态

`git tag` 里程碑管理

### 对象库操作相关命令