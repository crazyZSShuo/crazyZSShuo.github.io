删除mysql的数据文件

sudo rm /var/lib/mysql/ -R

删除mysql的配置文件

sudo rm /etc/mysql/ -R

（这两步非常重要，百度上很多文章都没有，如果是改完了密码还好，没改重装依然是系统自定账号密码）

自动卸载mysql（包括server和client）

sudo apt-get autoremove mysql* --purge

sudo apt-get remove apparmor

（有时候自动卸载并没有卸载完成，我的有一次就就卸载失败了，建议执行两次）

然后在终端中查看MySQL的依赖项：dpkg --list|grep mysql

（这一步即使没有显示也要进行下面的删除）

卸载： sudo apt-get remove dbconfig-mysql

卸载：sudo apt-get remove mysql-client

卸载：sudo apt-get remove mysql-client-5.7

卸载：sudo apt-get remove mysql-client-core-5.7

再次执行自动卸载：sudo apt-get autoremove mysql* --purge

查看MySQL的剩余依赖项：dpkg --list|grep mysql
（这一步即使没有显示也要进行下面的删除）
卸载：sudo apt-get remove php7.0-mysql
清除残留数据：dpkg -l|grep ^rc|awk ‘{print$2}’|sudo xargs dpkg -P
再次查看MySQL的剩余依赖项：dpkg --list|grep mysql
至此已经没有了MySQL的依赖项，彻底删除！
