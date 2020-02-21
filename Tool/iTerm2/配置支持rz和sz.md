
[参考](https://segmentfault.com/a/1190000012166969)

## 1. 安装lrzsz
```
brew install lrzsz  
```

## 2. 创建脚本文件
1. 进入/usr/local/bin目录
2. 新建两个脚本文件
   ```
   vi iterm2-recv-zmodem.sh
   vi iterm2-send-zmodem.sh
   ```
3. iterm2-recv-zmodem.shw文件内容
   ```
    #!/bin/bash
    # Author: Matt Mastracci (matthew@mastracci.com)
    # AppleScript from http://stackoverflow.com/questions/4309087/cancel-button-on-osascript-in-a-bash-script
    # licensed under cc-wiki with attribution required 
    # Remainder of script public domain
    
    osascript -e 'tell application "iTerm2" to version' > /dev/null 2>&1 && NAME=iTerm2 || NAME=iTerm
    if [[ $NAME = "iTerm" ]]; then
        FILE=`osascript -e 'tell application "iTerm" to activate' -e 'tell application "iTerm" to set thefile to choose folder with prompt "Choose a folder to place received files in"' -e "do shell script (\"echo \"&(quoted form of POSIX path of thefile as Unicode text)&\"\")"`
    else
        FILE=`osascript -e 'tell application "iTerm2" to activate' -e 'tell application "iTerm2" to set thefile to choose folder with prompt "Choose a folder to place received files in"' -e "do shell script (\"echo \"&(quoted form of POSIX path of thefile as Unicode text)&\"\")"`
    fi
    
    if [[ $FILE = "" ]]; then
        echo Cancelled.
        # Send ZModem cancel
        echo -e \\x18\\x18\\x18\\x18\\x18
        sleep 1
        echo
        echo \# Cancelled transfer
    else
        cd "$FILE"
        /usr/local/bin/rz -E -e -b
        sleep 1
        echo
        echo
        echo \# Sent \-\> $FILE
    fi
   ```

4. iterm2-send-zmodem.sh文件内容
```
#!/bin/bash
# Author: Matt Mastracci (matthew@mastracci.com)
# AppleScript from http://stackoverflow.com/questions/4309087/cancel-button-on-osascript-in-a-bash-script
# licensed under cc-wiki with attribution required 
# Remainder of script public domain

osascript -e 'tell application "iTerm2" to version' > /dev/null 2>&1 && NAME=iTerm2 || NAME=iTerm
if [[ $NAME = "iTerm" ]]; then
    FILE=`osascript -e 'tell application "iTerm" to activate' -e 'tell application "iTerm" to set thefile to choose file with prompt "Choose a file to send"' -e "do shell script (\"echo \"&(quoted form of POSIX path of thefile as Unicode text)&\"\")"`
else
    FILE=`osascript -e 'tell application "iTerm2" to activate' -e 'tell application "iTerm2" to set thefile to choose file with prompt "Choose a file to send"' -e "do shell script (\"echo \"&(quoted form of POSIX path of thefile as Unicode text)&\"\")"`
fi
if [[ $FILE = "" ]]; then
    echo Cancelled.
    # Send ZModem cancel
    echo -e \\x18\\x18\\x18\\x18\\x18
    sleep 1
    echo
    echo \# Cancelled transfer
else
    /usr/local/bin/sz "$FILE" -e -b
    sleep 1
    echo
    echo \# Received $FILE
fi 
```

5. 设置执行权限
```
chmod 777 iterm2-*
```

6. 配置iTerm2
Profiles -> Advance
```
Regular expression: rz waiting to receive.\*\*B0100
Action: Run Silent Coprocess
Parameters: /usr/local/bin/iterm2-send-zmodem.sh

Regular expression: \*\*B00000000000000
Action: Run Silent Coprocess
Parameters: /usr/local/bin/iterm2-recv-zmodem.sh
```