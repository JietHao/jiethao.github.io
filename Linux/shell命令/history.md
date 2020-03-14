# history 查看历史
1. 查看所有 history
2. 查看最近N条  history N   如：history 10
3. 清除所有  history -c
4. 清除指定记录  history -d xx  如：history -d 21
   * 批量删除
   ```
   j=0;for i in `history |grep sudo|awk '{print $1}'`;do let j=j+1; let i=i-j+1; echo $i $j ;history -d $i;done
   ```
5. ctrl + r 查询历史
