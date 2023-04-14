## Git的使用

####  1. git配置
    获取本机ssh key：
        ssh-keygen -t -C "<yourEmail@example.com>"
    配置全局name和email：
        git config --global user.name "<yourName>"
        git config --global user.email "<yourEmail@example.com>"
#### 2. clone项目到本地
    git clone <http://yourGitAddress.git>
#### 3. 查看工作区状态  git status
    查看文件变动    git diff file_name
#### 4. git add
    将某个文件或文件夹添加到暂存区：
        git add <file_name.txt>/<path>
    将当前目录所有修改添加到暂存区(不包括忽略文件)：
        git add .
    将<path>内的所有已跟踪文件的修改添加到暂存区（省略path表示当前目录）：
        git add -u [<path>]
    将<path>内的所有已跟踪文件的修改和未跟踪文件添加到暂存区（省略path表示当前目录）：
        git add -A [<path>]
    查看<path>中已修改但未提交的文件，并通过子命令进行控制（省略path表示当前目录）：
        git add -i [<path>]
#### 5. git commit
    提交所有改动并编写日志：
        git commit -m "<改动日志说明>"
#### 6. git pull
    下拉指定主机的指定分支，并与本地的指定分支合并：
        git pull <origin> <远程master>:<本地master>
    下拉指定主机的指定分支，并与本地的当前分支合并：
        git pull <origin> <master>
#### 7. git push
    推送本地指定分支到指定远程主机的指定分支上：
        git push <origin> <本地master>:<远程master>
    推送本地指定分支到远程同名分支上,如果远程没有同名分支，则会新建同名分支：
        git push <origin> <本地master>
    推送空的分支到远程指定分支，相当于删除远程分支：
        git push <origin> :<远程master>
    推送当前分支到指定主机的指定分支：
        git push <origin> HEAD:<远程master>
    推送当前分支到指定主机的同名分支：
        git push <origin> HEAD
    推送本地分支到远程同名分支上，并建立追踪关系（建立追踪关系后可直接使用git push推送）：
        git push -u <origin> <master>
    推送本地所有分支到指定主机上：
        git push --all <origin>
#### 8. git branch
    查看分支列表：
        git branch [--list]
    查看本地和远程所有分支：
        git branch -a
    新建分支:
        git branch <next>
    删除远程分支：
        git push <origin> --delete <next>
    删除分支（当前分支不能在被删除的分支上）：
        git branch -D <next>
#### 9. git merge
    合并某个分支到当前分支下，并自动进行新的提交：
        git merge <next>
    合并某个分支到当前分支下，不进行新的提交：
        git merge --no-commit <next>
    合并master分支和next分支到当前分支顶部：
        git merge <master> <next>
#### 10. git checkout
    切换到<master>分支的head版本：
        git checkout <master>
    取出当前分支的tag_name版本：
        git checkout <tag_name>
    放弃指定分支对file_name的修改：
        git checkout <master> <file_name.txt>
    在当前分支上创建新分支并将工作区设置为该分支上：
        git checkout -b <next>
#### 11. git reset
    回退文件，将文件从暂存区回退到工作区:
        git reset [HEAD] <file_name.txt>
    向前回退多个版本:
        git reset HEAD~n
    回退到指定某个版本：
        git reset <commit_id>
    将版本库软回退n个版本，所谓软回退表示将本地版本库的头指针全部重置到指定版本，且将这次提交之后的所有变更都移动到暂存区：
        git reset --soft HEAD~n
    将版本库回退n个版本，将本地版本库的头指针全部重置到指定版本，且会重置暂存区，即这次提交之后的所有变更都移动到未暂存阶段:
        git reset [--mixed] HEAD~n
    将版本库回退n个版本，但是不仅仅是将本地版本库的头指针全部重置到指定版本，也会重置暂存区，并且会将工作区代码也回退到这个版本:
        git reset --hard HEAD~n
#### 12. git rm
    删除git仓库管理系统以及本地中的某个文件：
        git rm <file_name.txt>
    删除git仓库管理系统以及本地中的某个文件夹：
        git rm -r <path>
    删除git仓库管理系统中的文件，但是保留本地文件：
        git rm --cached <file_name.txt>
#### 13. git mv
    移动某个文件到指定文件夹下：
        git mv <file> <path>
    重命名某个文件：
        git mv <file_name> <new_file_name>
#### 14. git rebase
    把当前分支衍合到指定分支上：
        git rebase <master>
    如果有冲突需要先解决冲突，解决完冲突之后执行:
        git rebase --continue
    放弃本次衍合操作：
        git rebase --abort
    直接使用master分支取代此分支
        git rebase --skip

####  15. 如果你还没有克隆现有仓库，并欲将你的仓库连接到某个远程服务器，你可以使用如下命令添加：
	git remote add origin <server>
<!--stackedit_data:
eyJoaXN0b3J5IjpbNTU0NDEyNzEzXX0=
-->