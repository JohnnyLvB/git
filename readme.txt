Git is a distributed version control system.
Git is free software.
This is third times update

git init              ----->  初始化git仓库
git add <file>        ----->  添加文件
git commit -m 'desc'  ----->  添加描述说明
git status            ----->  查看当前仓库的状态
git diff              ----->  查看具体修改了什么内容
git log               ----->  (以便确定要回退到哪个版本)查看历史记录，显示从最近到最远的提交日志，其中对应有commit id
git reflog            ----->  (以便确定要回到未来的哪个版本)查看历史修改的版本对应的id和description
git checkout -- file  ----->  将文件在工作区的修改全部撤销（两种情况：1、文件还没有添加到暂存区 2、文件已经添加到暂存区，又做了修改）

理解工作区 和 暂存区
通过 git add file 将file提交到的是暂存区
再通过 git commit -m 'desc' 则将file从暂存区提交到分支

test1

error line