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
git reset --hard id   ----->  回退到历史的某个版本，commitid 可以通过上两条的方式查看 也可以通过这种方式回退，git reset --hard HEAD^ 不过过于麻烦
git checkout -- file  ----->  将文件在工作区的修改全部撤销（两种情况：1、文件还没有添加到暂存区 2、文件已经添加到暂存区，又做了修改）
git reset HEAD <file> ----->  可以把暂存区的修改撤销掉（unstage），重新放回工作区,然后再通过上一条命令可以将其撤销
git rm <file>         ----->  删除文件
git branch dev        ----->  创建分支
git checkout dev      ----->  切换到dev分支
git checkout -b dev   ----->  创建dev分支，并切换到dev分支（合并前两部操作）
git branch            ----->  查看当前分支（命令会列出所有分支，当前分支前面会标一个*号）
git merge <branch>    ----->  合并指定分支到当前分支
git branch -d <branch> ---->  删除某个分支



理解工作区 和 暂存区
通过 git add file 将file提交到的是暂存区
再通过 git commit -m 'desc' 则将file从暂存区提交到分支

远程仓库使用
1、关联一个远程库 git remote add origin git@server-name:path/repo-name.git
2、第一次推送master分支 git push -u origin master
3、后续推送 git push origin master
