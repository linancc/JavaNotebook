常用命令
```
命令之间有空格  短命令-  长命令--
man 
echo 将字符串输出到屏幕
ctrl + l清屏  clear  reset
wget 下载 
systemctl status sshd
w  开启终端
last 
history
sosreport
head -n 10 某一文件的前十行
tail -n 10 后十行
diff 比较不同
ps -aux ｜ grep xxx 是查看某个进程或者服务是否存在
service 服务名 status 查看单个服务的运行状态： 
service –status -all 查看所有服务的运行状态： 
```

系统命令

```
uname -a 系统信息
who 系统用户
date 系统时间  date "+%H:%M:%S"
uptime 系统负载
free -h 系统内存
ps 进程  参数  aux  所有/用户信息/系统
pidof 查看进程pid号码
kill 结束进程  -9强制
killall 
reboot 重启
poweroff 关机  shutdown
```

文件操作

```
cp 复制 -r复制目录
mv 剪切/重命名
rm 删除 -f强制 -r删除目录
cd 切换目录
ls 列出目录
pwd 显示当前工作目录
cat 看短小的文件
more 看大文件
tar czvf  压缩
tar xzvf  解压
mkdir 新建目录
mkdir -p a/b/c  逐级创建目录
```

编辑网卡

```
ifconfig 1.网卡名称 2.ip地址 3.mac地址 4.收到/发送流量大小
vim /etc/sysconfig/network-scripts/ifcfg-ens32  编辑网卡
systemctl restart network 重启服务
nmtui 编辑网卡信息
nm-connection-editor
```

安装软件

```
which mysql可执行程序在哪
whereis
rpm -qa | grep sql搜索sql
rpm -ivh *.rpm安装软件
rpm -e --nodeps强制卸载
```

yum

```
自动搜索最快镜像插件：yum install yum-fastestmirror
```

用户身份与文件权限

```
useradd tom 添加用户
id tom 
groupadd grop1 添加用户组
usermod 修改用户属性
passwd 用于修改用户密码、过期时间、认证信息等
userdel 删除用户 -r	同时删除用户及用户家目录
```

防火墙

```
firewall-cmd --zone=public --add-port=443/tcp --permanent  添加端口
firewall-cmd --reload  重启生效
```

[lnmp下mysql怎么设置远程连接访问](https://my.oschina.net/u/585378/blog/110478)

```mysql
mysql - u root - p
#输入mysql的root用户的密码
mysql > use mysql ;
mysql > update user set host = '%' where user = 'root' ;
mysql > flush privileges ;
mysql > exit ;
```