### 撤销修改

```
git checkout -- readme.txt
```

作用：把readme.txt文件在工作区的修改全部撤销，这里有两种情况：

一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；

一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

总之，就是让这个文件回到最近一次git commit或git add时的状态

用命令`git reset HEAD <file>`可以把暂存区的修改撤销掉（unstage），重新放回工作区

### 删除某次提交

```
git rebase -i [commitID]
git push origin [branch] -f
```

这里的commitID表示该commit之后的所有提交都会被删除。执行git rebase后，在界面中将pick命令改为drop即可删除提交

### 修改某次提交

与上面类似，只是将pick命令改为edit，然后对文件做修改，再执行以下命令

```
git add [modified files]
git commit --amend(在弹出的编辑框中直接输出q退出即可)
git rebase --continue
```

### 回滚

```
git revert [commitID]
git push origin master

或
git reset --hard [commitID]
git push origin master
```

revert和reset的区别:

revert是放弃指定提交的修改，但是会生成一次新的提交，需要填写提交注释，以前的历史记录都在，而reset是指将HEAD指针指到指定提交，历史记录中不会出现放弃的提交记录。



git 查看diff并保存: 

```
git diff 上次commit的id 你commit的id 文件路径 > 要保存的文件名
```

fileName相关的commit记录

```
git log filename
```

显示每次提交的diff

```
git log -p filename
```

版本回退

```
git reset --hard 版本号
```

git push到远程指定分支

```
git push origin [branch]
```

