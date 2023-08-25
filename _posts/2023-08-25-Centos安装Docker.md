## 清理残留
```
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```

# 一、yum 安装

## Install using the rpm repository
```
sudo yum install -y yum-utils

sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

## Install Docker Engine
```
sudo yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## Start Docker
```
sudo systemctl start docker
```

# 二、rpm 安装

## 下载安装包 [安装地址](https://download.docker.com/linux/centos/)

## 安装
```
sudo yum install /path/to/package.rpm
```

## 启动
```
sudo systemctl start docker
```
