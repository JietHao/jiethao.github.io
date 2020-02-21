# 连接mongo
```
> sh mongo.sh
> mongo --port 20000 -u haojie -p 'password' --authenticationDatabase=idlethree
> use idlethree;
```

## 显示所有库（需要权限）
```
> show dbs  
```

## 切库
```
> use idlethree;
```

## 显示所有collections（需要权限）
```
> show collections;
```

## 查询新服玩家新增情况
```
db.the_server.find({"_id": 1}
```


## 导出表数据
```
> mongoexport --port 20000 -u haojie -p 'password' --authenticationDatabase=idlethree -d idlethree -c legion_matching -o legionmatching_wx_1225_1.json
> sz legionmatching_wx_1225_1.json
```

