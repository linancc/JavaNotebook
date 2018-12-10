[Oracle安装](https://www.cnblogs.com/dmego/p/6353641.html)

用户配置

```
安装ORACLE时，若没有为下列用户重设密码，则其默认密码如下：

用户名 / 密码             登录身份                              说明

sys/change_on_install    SYSDBA 或 SYSOPER        不能以 NORMAL 登录，可作为默认的系统管理员

system/manager           SYSDBA 或 NORMAL         不能以 SYSOPER 登录，可作为默认的系统管理员

sysman/oem_temp          sysman                   为 oms 的用户名

scott/tiger              NORMAL                   普通用户

aqadm /aqadm             SYSDBA 或 NORMAL          高级队列管理员

Dbsnmp/dbsnmp            SYSDBA 或 NORMAL          复制管理员
```

[Oracle服务](https://blog.csdn.net/u010028869/article/details/50069119)