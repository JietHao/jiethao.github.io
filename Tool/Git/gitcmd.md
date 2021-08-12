# git命令

## 初始化
1. 设置
   git config --global user.name 'xxx'
   git config --glolbal user.mail 'xxx@xxx.com'

2. 初始化仓库
   git init


## 操作
1. clone远程仓库工程代码到本地
   git clone  xxxx

2. 查看工程代码状态
   git status 
   git status -s   // 查看简要信息


3. 加入本地仓库
   git add xxx

4. 从本地仓库移除
   git rm xxx


5. 提交到本地
   git commit -m ''
   git commit xxx -m ''

6. 推送到远程仓库
   git push


7. 更新远程仓库代码到本地
   git pull


8. 查看日志
   git log



9. 子模块
   git submodule init
   git sumodule update