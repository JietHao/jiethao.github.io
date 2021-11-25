## Git命令

### 1、设置
```
git config --global user.name 'xxx'
git config --glolbal user.mail 'xxx@xxx.com'

git config --global core.quotepath false // 识别中文
````

### 0、常用命令汇总
```
git config --global user.name 'xxx'
git config --glolbal user.mail 'xxx@xxx.com'
git config --global core.quotepath false // 识别中文

git clone url // 下载远端仓库到本地
git push // 推送到远端仓库
git pull // 同步远端仓库到本地

git init // 初始化本地仓库
git add xxx // 加入文件xxx本地仓库
git rm xxx // 从本地仓库移除文件xxx
git commit xxx -m 'yyy' // 提交文件xxx的修改到本地仓库
git commit -m 'yyy' // 提交当前已经add但未commit的所有文件到仓库
git commit -a -m 'yyy' // 提交当前目录下所有修改文件到仓库
git checkout xxx // 还原xxx文件的本地修改
git checkout . // 还原当前目录下的修改
```

### 1、创建分支 
``` 
git branch new_branch //创建新分支 
git branch -d xxx // 删除分支 
```

### 2、切换分支 
``` 
git checkout develop //切换分支到develop 
git checkout -b new_branch //创建并切换到新分支 
git checkout -p other_branch // 当前分支和其他分支进行比较 
``` 

### 3、查看分支 
``` 
git branch //查看本地分支 
git branch -r // 查看远程分支 
git branch -a // 本地和远程分支 
git branch -vv //本地分支和远程分支关联关系 
``` 

### 4、分支推到远程 
``` 
git push --set-upstream origin feature/zhuchb/test //将当前分支推送到远端 
git push origin --delete [branchname] // 删除远程分支
``` 

### 5、切换远程分支 
``` 
git branch --set-upstream-to=<远程主机名>/<远程分支名> <本地分支名> 
``` 

### 6、修改远程HEAD到某分支 
``` 
git remote set-head origin develop //修改远程分支HEAD指向develop 
``` 

### 7、分支合并 
``` 
git checkout master // 切回到需要合并的源分支 
git merge new_branch // 将目的分支合并到源分支 
```

### 8、子模块
```
git submodule init // 初始化子模块
git submodule update // 更新子模块
git submodule update --init //初始化并更新子模块
```

## 9. 暂存
```
git stash list 查看暂存记录
git stash show 查看具体暂存的改动
git stash 当前改动全部暂存
git stash clear 清空全部暂存
```

## 10. 查看log
```
git log 查看所有历史记录
git log -n 查看前几条
git log --stat 显示更改文件和增改行数等简要统计
git log --since=2.days 指定日期
git log --author=xxx 指定作者（程序的修改人）
git log --grep=xxx 指定关键字
git log --committer=xxx 指定提交者（代码的提交人）
```

## 11. 提交
```
git commit -m 'xxx'  只能提交已经git add的文件
git commit -a -m 'xxx' 无需git add，直接提交
git commit --amend 修补提交，可以覆盖上次commit，场景：修改注释，漏提交，多次修改提交同一内容
git show <commit-hash-id>  查看某次提交的修改内容
git reset HEAD^ 等同使用默认参数--mixed，HEAD^指上一个版本(等同HEAD~1)，上n次提交，则写成：HEAD~n
git reset --soft HEAD^  撤销commit,不撤销git add，不删除工作空间改动代码
git reset --hard HEAD^  撤销commit,撤销git add，删除工作空间改动代码
git reset --mixed HEAD^  撤销commit，撤销git add，不删除工作工作空间改动代码
```

## 12. 对比
```
git diff
```

## 13. 切换仓库
```
方法一：
本地分支修改步骤：
1、查看本地代码的远程仓库地址
git remote -v
2、如果不是在新的gitlab上，找到新的gitlab上的此项目的git地址，拷贝一下
3、删除旧的gogs仓库地址
git remote rm origin
4、添加新的gitlab仓库地址，把刚才2拷贝的地址粘贴一下
git remote add origin "刚才拷贝的地址"
5、查看一下是否修改成功
git remote -v
6、okk了

旧仓库地址： https://tygit.touch4.me
新仓库地址： https://tygit.tuyoo.com/weiqu/server

方法二：
1、进入本地项目下先查看本地远程仓库是否更新，未更新找到新的gitlab上的此项目的git地址，拷贝一下
git remote -v
2、设置
git remote set-url origin "刚才复制的url"
3、okk了~

旧仓库地址： https://tygit.touch4.me
新仓库地址： https://tygit.tuyoo.com/weiqu/server

示例：git remote set-url origin https://tygit.tuyoo.com/freetime/tuyoo6.git

```

## 14. orgin信息
```
git remote show origin 查看origin信息
git remote prune origin 删除本地有远程仓库不存在的
```