# 使用说明


## MacOS下破解方式
> link: https://www.jianshu.com/p/596b4463eacd

### 下载安装BCompare
1. 地址：https://www.scootersoftware.com/download.php

### 创建BCompare文件
1. 进入Mac应用程序目录下，找到刚刚安装好的Beyond Compare，路径如下/Applications/Beyond Compare.app/Contents/MacOS。
2. 修改启动程序文件BCompare为BCompare.real。
3. 在当前目录下新建一个文件BCompare，文件内容如下：
   ```sh
   #!/bin/bash
   rm "/Users/$(whoami)/Library/Application Support/Beyond Compare/registry.dat"
   "`dirname "$0"`"/BCompare.real $@
   ```
4. 保存BCompare文件。
5. 修改文件的权限：
   ```
   chmod a+x /Applications/Beyond\ Compare.app/Contents/MacOS/BCompare
   ```
6. 以上步骤完成后，再次打开Beyond Compare就可以正常使用了，enjoy it。


## Windows破解方式
1. 查看当前用户

C:\Users\TU>whoami/user

用户信息
----------------

用户名             SID
================== =============================================
windows-7aincbm\tu S-1-5-21-319973256-2931121972-3601398790-1000


C:\Users\TU>

2. 从注册表删除该用户下的CacheId

reg delete “HKEY_USERS<SID>\Software\Scooter Software\Beyond Compare 4” /v CacheId /f

reg delete “HKEY_USERS\S-1-5-21-1742707355-3167172020-1997565728-1001\Software\Scooter Software\Beyond Compare 4” /v CacheId /f

reg delete “HKEY_USERS\S-1-5-21-319973256-2931121972-3601398790-1000\SOFTWARE\Scooter Software\Beyond Compare 5” /v CacheId /f


打开注册表
Win+R后输入regedit

注意事项：
1. 如果不好使，卸载重新安装
2. 重新安装后，先删除注册表信息再启动