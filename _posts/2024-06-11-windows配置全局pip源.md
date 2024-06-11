### pip国内镜像源

```
阿里云
https://mirrors.aliyun.com/pypi/simple/

中科大
https://pypi.mirrors.ustc.edu.cn/simple/

清华
https://pypi.tuna.tsinghua.edu.cn/simple/

豆瓣
https://pypi.douban.com/simple/
```


### Windows

```
pip config list -v
```

当前用户的pip配置文件为C:\Users\${username}\pip\pip.ini

我们把当前用户下的pip源更换为国内源

进入C:\Users\${username}\下

新建文件夹pip

新建pip.ini

内容如下（更换为阿里云的源，根据需要自行更改）

```
[global]
index-url=https://mirrors.aliyun.com/pypi/simple/
[install]
trusted-host=mirrors.aliyun.com
```

再次运行pip config list -v, 提示更换源成功。



