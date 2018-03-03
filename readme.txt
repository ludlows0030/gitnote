mkdir  xx//创建文件夹
cd xx//进入该文件夹
pwd //用于显示当前目录
git init//将当前目录变成Git可以管理的仓库
git add xx//将文件添加到仓库
git commit -m "xxxx"//将文件提交到仓库,xxx为本次提交的说明（备注，方便日后阅读）

Q：什么Git添加文件需要add，commit一共两步呢？
A：因为commit可以一次提交很多文件，所以你可以多次add不同的文件
z.b.：
	$ git add file1.txt
	$ git add file2.txt file3.txt
	$ git commit -m "add 3 files."
	//add多个文件，一次性commit
	
git statue//查看当前仓库状态
git diff xxx//查看文件修改内容
git log//查看提交日志(回退后在回退版本之后进行的操作无法查看） --pretty=oneline参数将结果输出为一行
git reset --hard HEAD^//回退到上一个版本
git reset --hard xxx//回退到指定版本
git relog//查看操作的每一次命令

//工作区和缓存区
	工作区Working Directory:电脑里可以看到的目录（.git的父目录）
	版本库Repository:工作区的一个隐藏目录.git。
	版本库里有 stage（暂存区）、master（第一个分支）、head（指针）
	git add//实质是将文件修改添加到暂存区
	git commit//实质上就是把暂存区的所有内容提交到当前分支
	
git checkout -- file//丢弃工作区的修改，分为两种情况：
	一种是file自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
	一种是file已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

git reset HEAD file//丢弃添加到缓存区的修改
git rm//用于删除一个文件，如误删可以用git checkout --file恢复
git remote add origin git@github.com:username/Respository//将本地仓库和Github关联
git push -u origin master//第一次推送并关联当前master
git push origin master//往后本地作了提交，通过此命令推送到Github
git clone git@github.com:username/Respositoryname//将远程仓库克隆到本地
git checkout -b xxx//创建并切换到xxx分支 
	相当于执行
		$git branch xxx
		$git checkout xxx
git branch//列出所有分支，当前分支前面标一个*
git checkout master//切换回master分支
git merge xxx//将xxx分支的工作合并到master上
git branch -d xxx//删除xxx分支

合并存在冲突时，解决冲突后再进行提交，合并完成
git log --graph//查看分支合并图
git stash//储藏当前工作分支
git stash list//被stash的分支
git stash apply//回复分支但不删除stash内容
git stash drop//删除stash内容
git stash pop//回复并删除stash内容
