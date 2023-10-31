### 安装依赖
yum -y groupinstall "Development tools"
yum install -y ncurses-devel gdbm-devel xz-devel sqlite-devel tk-devel uuid-devel readline-devel bzip2-devel libffi-devel
yum install -y openssl-devel openssl11 openssl11-devel


### 下载
mkdir -p /doc/temp && cd /doc/temp
wget https://www.python.org/ftp/python/3.10.4/Python-3.10.4.tgz


### 编译
export CFLAGS=$(pkg-config --cflags openssl11)
export LDFLAGS=$(pkg-config --libs openssl11)


tar xvzf Python-3.10.4.tgz
cd Python-3.10.4
./configure --enable-optimizations && make altinstall


### 验证
/usr/local/bin/python3.10 --version
/usr/local/bin/pip3.10 --version


### 配置
ln -sf /usr/local/bin/python3.10 /usr/bin/python3
ln -sf /usr/local/bin/pip3.10  /usr/bin/pip3


### 配置pip源
mkdir -p ~/.pip
touch ~/.pip/pip.conf

vim ~/.pip/pip.conf

[global]
index-url=https://pypi.tuna.tsinghua.edu.cn/simple/
extra-index-url=
        http://pypi.douban.com/simple/
        http://mirrors.aliyun.com/pypi/simple/
#proxy = [user:passwd@]proxy.server:port
[install]
trusted-host=
        pypi.tuna.tsinghua.edu.cn
        pypi.douban.com
        mirrors.aliyun.com
ssl_verify: false

pip3 install --upgrade pip




