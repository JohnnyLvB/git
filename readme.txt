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
git branch -D <branch> ---->  强行删除某个分支（当某个分支还没有和其他分支合并，此时不能直接删除，若要强行删除，使用此命令）

git stash             ----->  把当前工作区暂时“储藏”起来
git stash list        ----->  查看被暂存的工作区
git stash apply       ----->  恢复被暂存的工作区（但是stash里的内容不会被删除，使用 git stash drop 来删除）
git stash pop         ----->  恢复被暂存的工作区并删除

git remote            ----->  查看远程库的信息
git remote -v         ----->  查看远程库的详细信息
git push origin master----->  将本地提交推送到远程master分支
git push origin dev   ----->  将本地提交推送到远程dev分支
git checkout -b dev origin/dev  创建一个本地dev分支并与远程origin仓库下的dev分支关联

git tag <tagname>     ----->  用于新建一个标签，也可以指定一个commitid（git tag <tagname> 78d1ed656ffe）
git tag               ----->  查看所有标签
git tag -a <tagname> -m "blablabla..."  创建带有说明的标签
git show <tagname>    ----->  查看某标签下的信息描述
eg: git tag V1.0

git push origin <tagname>  ----->  可以推送一个本地标签
git push origin --tags     ----->  可以推送全部未推送过的本地标签
git tag -d <tagname>  ----->  可以删除一个本地标签
git push origin :refs/tags/<tagname>  ----->  可以删除一个远程标签



理解工作区 和 暂存区
通过 git add file 将file提交到的是暂存区
再通过 git commit -m 'desc' 则将file从暂存区提交到分支


多人协作的工作模式通常是这样：
1、首先，可以试图用git push origin <branch-name>推送自己的修改；
2、如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；
3、如果合并有冲突，则解决冲突，并在本地提交；
4、没有冲突或者解决掉冲突后，再用git push origin <branch-name>推送就能成功！

如果git pull提示no tracking information，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream-to <branch-name> origin/<branch-name>。这就是多人协作的工作模式，一旦熟悉了，就非常简单。


小结
查看远程库信息，使用git remote -v；
本地新建的分支如果不推送到远程，对其他人就是不可见的；
从本地推送分支，使用git push origin branch-name，如果推送失败，先用git pull抓取远程的新提交；
在本地创建和远程分支对应的分支，使用git checkout -b branch-name origin/branch-name，本地和远程分支的名称最好一致；
建立本地分支和远程分支的关联，使用git branch --set-upstream branch-name origin/branch-name；
从远程抓取分支，使用git pull，如果有冲突，要先处理冲突。




远程仓库使用
1、关联一个远程库 git remote add origin git@server-name:path/repo-name.git
2、第一次推送master分支 git push -u origin master
3、后续推送 git push origin master


通常，合并分支时，如果可能，Git会用Fast forward模式，但这种模式下，删除分支后，会丢掉分支信息。
如果要强制禁用Fast forward模式，Git就会在merge时生成一个新的commit，这样，从分支历史上就可以看出分支信息。
git merge --no-ff -m "desc" <branch>
