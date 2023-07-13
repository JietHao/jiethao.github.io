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
