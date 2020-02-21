# svn 常用命令


@svn:externals[https://www.cnblogs.com/freeliver54/archive/2012/09/05/2671564.html]
@svn:ignore[https://www.cnblogs.com/isykw/p/7298607.html]


### svn属性命令

* 显示当前svn目录下设置的所有属性
  -  `svn proplist`
   
* 获取某个设置的属性
  - `svn propget PROPNAME`

* 设置某个属性
  - 直接设置：`svn propset PROPNAME PROPVALUE .`
  - 通过文件设置：`svn propset PROPNAME -F FILE .`
 
* 编辑某个属性
  - `svn propedit PROPNAME . --editor-cmd vim` 
  
* 删除某个设置的属性
  - `svn propdel PROPNAME`
  
* svn:ignore  忽略目录或文件，不维护到svn
* svn:externals 外部引入


### svn对比命令

* svn diff config37 -r HEAD |grep Index


### svn合并命令
1. svn merge url -r ver1:ver2 . [--dry-run]
```
svn merge url . -r 100:200 .  // 合并范围内的version，不包含100，包含200
svn merge url . -c 100,105,110 .   // 合并指定的版本，100=(99,100]
svn merge url . -r 100:HEAD --dry-run
```

2. 解决
```
svn update --ignore-externals
```