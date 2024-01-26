```
$ git pull

ssh: connect to host github.com port 22: Connection refused

fatal: Could not read from remote repository.


Please make sure you have the correct access rights

and the repository exists.

```

### 排查思路

ssh: connect to host github.com port 22: Connection refused这个错误提示的是连接github.com的22端口被拒绝了。

原本以为github.com挂了，但是浏览器访问github.com一切正常。

网上搜索这个报错，发现很多人遇到这个问题，大概有2个原因和对应解决方案：

#### 1、使用GitHub的443端口

22端口可能被防火墙屏蔽了，可以尝试连接GitHub的443端口。

```

$ vim ~/.ssh/config
```
# Add section below to it
Host github.com
  Hostname ssh.github.com
  Port 443
```
$ ssh -T git@github.com
Hi xxxxx! You've successfully authenticated, but GitHub does not
provide shell access.

```

这个解决方案的思路是：给~/.ssh/config文件里添加如下内容，这样ssh连接GitHub的时候就会使用443端口。

```
Host github.com
  Hostname ssh.github.com
  Port 443

```

如果~/.ssh目录下没有config文件，新建一个即可。

修改完~/.ssh/config文件后，使用ssh -T git@github.com来测试和GitHub的网络通信是否正常，如果提示`Hi xxxxx! You've successfully authenticated, but GitHub does not

provide shell access.` 就表示一切正常了。

但是，这个方案在我这里行不通，修改后还是提示ssh: connect to host github.com port 443: Connection refused。

这个方案有效的前提是：执行命令ssh -T -p 443 git@ssh.github.com后不再提示connection refused，所以要尝试这个方案的小伙伴先执行这条命令测试下。


#### 2、使用https协议，不要使用ssh协议

在你的GitHub的本地repo目录，执行如下命令：

```
$ git config --local -e

```

然后把里面的url配置项从git格式

```
url = git@github.com:username/repo.git

```

修改为https格式

```
url = https://github.com/username/repo.git

```

这个其实修改的是repo根目录下的.git/config文件。

[参考地址](https://segmentfault.com/a/1190000041909858)
