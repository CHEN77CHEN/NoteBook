# 常用 Git 命令

## 初始化一个新的 Git 仓库

这个命令在当前目录创建一个新的 Git 仓库。它会在目录下生成一个.git 的子目录，包含 Git 仓库的所有必要文件

初始化一个新的 Git 仓库。在项目的根目录执行此命令，会创建一个隐藏的 `.git` 目录，用于存储 Git 仓库的配置和元数据

## git init

### 在指定目录下初始化一个新的 Git 仓库。将 `<directory>` 替换为你想要创建仓库的目录名称

git init `<directory>`

### 初始化一个裸仓库（Bare Repository）。裸仓库通常用于共享和远程仓库。在这个仓库中，没有工作目录，只保存版本历史信息

git init --bare `<directory>`

### 使用指定的模板目录初始化 Git 仓库。模板目录中包含了一些预设的配置和钩子脚本

git init --template=<template_directory>

### 将 `.git` 目录初始化到指定位置，而不是在当前目录下创建。可以使用这个选项在项目目录之外管理 `.git` 目录

git init --separate-git-dir=<git_directory>

### 在初始化时不显示额外的信息，以安静模式执行

git init --quiet

### 初始化一个裸仓库，并设置共享权限。`<permissions>` 为权限设置，例如 `group` 表示将仓库设置为组共享

git init --bare --shared=`<permissions>`

## git clone `<repository>`

### 克隆一个远程仓库到本地 使用这个命令可以复制远程仓库的所有文件到本地，创建一个相同的仓库副本

git clone `<repository>`

### 将 `<repository>` 处的远程仓库克隆到指定目录 `<directory>` 中。例如：`git clone https://github.com/example/repository.git my_project`

git clone `<repository> <directory>`

## git add `<file>`

将文件添加到暂存区
这个命令将指定的文件或目录的更改添加到 Git 的暂存区，准备提交到版本历史。

### 将指定文件添加到暂存区

git add `<file1> <file2>` ...

### 将所有更改添加到暂存区

git add -A # 或 git add --all

### 将当前目录及其子目录中的所有更改添加到暂存区

git add .

## 添加当前目录下所有新文件和修改的文件，但不包括被删除的文件

git add -u # 或 git add --update

## 添加交互式模式，允许用户选择要添加的文件

git add -i # 或 git add --interactive

## git commit -m "message"

提交暂存区的更改到仓库。
通过这个命令，你将暂存区的更改永久保存到 Git 仓库中，"message"是对本次提交的描述信息。

### 提交暂存区的所有更改，并添加提交信息

git commit -m "message"

### 使用编辑器编写详细的提交信息，这会打开默认编辑器

git commit

### 提交暂存区的所有更改，并将更改和提交信息放入一个新的提交中

git commit -am "Your commit message here"

### 修改最后一次提交的提交信息

git commit --amend

### 提交时包含指定文件，并添加提交信息

git commit `<file1> <file2>` ... -m "Your commit message here"

### 将暂存区的更改拆分成多个提交，交互式地选择要提交的文件

git commit --interactive

### 提交时允许修改之前的提交信息

git commit --reuse-message=HEAD

### 提交时不生成新的提交对象，只更新上一次提交的时间戳和提交信息

git commit --only --amend

## git status

查看工作区、暂存区和仓库的状态。
这个命令显示当前工作目录中文件的状态，包括已修改、已暂存和未跟踪的文件。

### 查看工作区和暂存区的状态

git status

### 查看更详细的状态信息，包括未跟踪的文件

git status -u # 或 git status --untracked-files

### 以简洁的格式显示状态，可用于脚本或其他自动化工作

git status --porcelain

### 查看已暂存的变更

git status --cached # 或 git status --staged

### 在列出的文件前面显示相对路径

git status --short

### 显示未被忽略的文件

git status --no-ignore

### 显示忽略的文件

git status --ignored

### 以更紧凑的格式显示分支信息

git status -b # 或 git status --branch

### 显示所有分支的信息，包括远程跟踪分支

git status -vv # 或 git status --verbose

## git log

查看提交日志。
通过这个命令可以查看项目的提交历史，包括提交者、提交时间和提交信息。

### 显示提交历史，包括提交的 SHA 值、作者、日期和提交信息

git log

### 以图形化的方式显示提交历史，更直观地展示分支和合并信息

git log --graph

### 限制显示的提交数目，例如只显示最近的 3 个提交

git log -n 3

### 显示每个提交的详细更改，包括文件路径和具体变更内容

git log -p # 或 git log --patch

### 显示每个提交的简略统计信息，包括插入和删除的行数

git log --stat

### 以一行的格式显示每个提交的简略信息

git log --oneline

### 查看某个文件的提交历史

git log `<file>`

### 显示某个作者的提交历史

git log --author=`<author>`

### 仅显示包含指定关键字的提交

git log --grep=`<keyword>`

### 仅显示指定时间范围内的提交历史

git log --since=`<date`> --until=`<date>`

### 以时间线的方式显示提交历史，每个提交一行

git log --pretty=format:"%h - %an, %ar : %s"

### 以某种自定义格式显示提交历史

git log --pretty=format:"%h - %an, %ad : %s"

## git branch

列出本地分支。
这个命令列出当前仓库中所有的本地分支，当前分支前会有一个星号。

### 列出本地所有分支

git branch

### 创建一个新的分支

git branch <branch_name>

### 切换到指定分支

git checkout <branch_name> # 或 git switch <branch_name>

### 创建并切换到新的分支

git checkout -b <new_branch> # 或 git switch -c <new_branch>

### 删除本地分支

git branch -d <branch_name>

### 强制删除本地分支

git branch -D <branch_name>

### 列出远程仓库的所有分支

git branch -r

### 列出所有本地和远程仓库的分支

git branch -a

### 查看每个分支的最后一次提交

git branch -v

### 查看每个分支的最后一次提交和提交信息

git branch -vv

### 合并指定分支到当前分支

git merge <branch_name>

### 使用 rebase 将当前分支的提交移动到指定分支的最后

git rebase <branch_name>

### 查看分支合并图

git log --graph --oneline --all

### 设置当前分支的追踪分支

git branch --set-upstream-to=`<remote>/<branch>` # 或 git branch -u `<remote>/<branch>`

### 查看所有已合并到当前分支的分支

git branch --merged

### 查看所有未合并到当前分支的分支

git branch --no-merged

### git checkout `<branch>`

切换到指定分支。
使用这个命令可以切换到指定的本地分支，工作目录会变成该分支的最新状态。
git merge `<branch>`
合并指定分支到当前分支。
这个命令用于将指定分支的更改合并到当前所在的分支，通常用于将一个特性分支的更改合并到主分支。
Branch-2.png

## git pull

从远程仓库拉取最新的更改。
这个命令等同于 git fetch followed by git merge，它从远程仓库获取最新的更改并自动合并到当前分支。

### 从远程仓库拉取并合并最新的更改到当前分支

git pull

### 从远程仓库拉取并重新播放（rebase）本地未推送的更改

git pull --rebase

### 从指定的远程仓库拉取并合并更改

git pull `<remote> <branch>`

### 从远程仓库拉取指定分支的更改，并合并到当前分支

git pull origin `<branch>`

### 从远程仓库拉取指定分支的更改，并重新播放（rebase）到当前分支

git pull --rebase origin `<branch>`

## git push

推送本地更改到远程仓库。
这个命令将本地的提交推送到远程仓库，使得远程仓库中也有了最新的更改。

### 推送本地分支的更改到远程仓库

git push

### 推送本地分支的更改到指定远程仓库

git push `<remote> <branch>`

### 推送本地分支的更改到远程仓库，并将分支关联到远程分支

git push -u `<remote> <branch>`

### 强制推送本地分支的更改到远程仓库（谨慎使用）

git push -f # 或 git push --force

### 推送本地分支的更改到远程仓库，并删除远程分支的相应分支

git push `<remote>` --delete `<branch>` # 或 git push `<remote>` :`<branch>`

### 推送所有本地分支的更改到远程仓库

git push --all

### 推送所有本地分支的更改到远程仓库，并删除远程仓库中不存在的本地分支

git push --all --prune

### 推送所有标签到远程仓库

git push --tags

### 推送指定标签到远程仓库

git push `<remote>` `<tag>`

## git remote -v

查看远程仓库的详细信息。
这个命令显示与当前本地仓库关联的远程仓库的详细信息，包括 URL。

## git diff

查看工作区与暂存区的差异。
这个命令显示工作区与暂存区之间的差异，即显示尚未暂存的更改。

## git reset `<file>`

撤销对文件的暂存。
这个命令用于取消对指定文件的暂存，将文件从暂存区恢复到工作区。

## git rm `<file>`

从版本库中删除文件。
这个命令用于从 Git 版本库中删除指定的文件，同时会将这个删除操作暂存。

## git tag <tag_name>

创建一个标签。
通过这个命令可以创建一个标签，通常用于标记某个重要的提交，方便回溯历史。

## git fetch

## git commit -m 'test' --no-verify

忽略 eslint 验证
