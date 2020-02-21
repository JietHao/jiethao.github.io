   curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py  
   python get-pip.py
   
   pip install --user  # /User/xxx/.local/
   
   pip install --target=/Library/
   

conda-env

conda install xxx
conda install --use-local /path/xxx.tar.gz


anaconda search -t conda bootstrap_admin
Run 'anaconda show <USER/PACKAGE>' to get more details:
Packages:
     Name                      |  Version | Package Types   | Platforms
     ------------------------- |   ------ | --------------- | ---------------
     auto/bootstrap_admin      |    0.3.0 | conda           | linux-64, linux-32
                                          : https://github.com/douglasmiranda/django-admin-bootstrap
Found 1 package

conda install -c https://conda.anaconda.org/auto/bootstrap_admin bootstrap-admin

解决方法 ：

anaconda search -t conda 要安装的包
选择符合条件的安装包路径

conda install -c https://conda.anaconda.org/列表中对应的Name 要安装的包
如果还是没有对应的安装包用：

pip install 要安装的包
————————————————
版权声明：本文为CSDN博主「醉雨轩Y」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/miao0967020148/article/details/85230430