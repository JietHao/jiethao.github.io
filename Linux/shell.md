# shell命令

## alias 别名
1. 查看所有别名 alias
2. 设置别名  alias ll='ls -l --color=auto'
3. 取消别名  unalias ll
4. 永久设置别名（重启不失效）可在/etc/profile或自己的~/.bashrc


## vi 编辑
1. gg 跳到 首行
2. G 跳到 尾行
3. :set nu  显示行号
4. 行号gg 跳到指定行
5. 行首: Home or shift+6
6. 行尾： End  or shift+4


## find 查找
- 查找名删除
```
find . -name .DS_* |xargs rm -rf
```


## history 查看历史
1. 查看所有 history
2. 查看最近N条  history N   如：history 10
3. 清除所有  history -c
4. 清除指定记录  history -d xx  如：history -d 21
   * 批量删除
   ```
   j=0;for i in `history |grep xxxx|awk '{print $1}'`;do let j=j+1; let i=i-j+1; echo $i $j ;history -d $i;done
   ```
5. ctrl + r 查询历史
