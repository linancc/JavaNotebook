[阿里Maven镜像](http://maven.aliyun.com/mvn/view)

[Maven Repository](https://mvnrepository.com/)

[官方仓库](https://search.maven.org/)

一般情况下在c:\Users\xx.m2\这个目录下面没有settings.xml文件，我们可以新建一个，settings.xml文件下的内容是

```xml
<?xml version="1.0" encoding="UTF-8"?>

<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                          https://maven.apache.org/xsd/settings-1.0.0.xsd">

      <mirrors>
        <mirror>  
            <id>alimaven</id>  
            <name>aliyun maven</name>  
            <url>https://maven.aliyun.com/repository/public</url>  
            <mirrorOf>central</mirrorOf>          
        </mirror>  
      </mirrors>
</settings>
```

一键构建

```
mvn tomcat:run 即使未安装tomcat也能运行maven项目
```

Maven的好处

```
依赖管理 就是对jar包的统一管理 可以节省空间
一键构建
可以跨平台
应用于大型项目 可以提高开发效率

用户管理  订单管理  支付管理
Maven分模块开发
互联网项目 按业务分
传统项目 按层分 dao service web
```

Maven仓库

```
三种仓库：
    本地仓库：自己维护
    远程仓库：公司维护
    中央仓库：maven团队维护  大概两个亿（2015年）
```

settings.xml文件

```
可以修改本地仓库位置
修改镜像源
```

Maven的目录结构

```
src
	--main           	主目录
		--java			都是java代码
		--resources		配置文件 .properties .xml
		--webapp		web工程的主目录
			--WEB-INF
				--web-xml
    --test				测试目录
    	--java			java代码
    	--resources		junit测试所用到的配置文件，如果没有默认从main里找
pom.xml 	 			整个项目的核心文件
```

Maven常用命令

```
clean  清理编译的文件（target文件夹）
compile 编译了主目录的文件
test 编译test目录文件
package 打包
install 把项目发布到本地仓库  会先执行compile test package
site 项目说明

tomcat：run  一键启动
```

Maven生命周期

```
clean 生命周期  clean
default 生命周期 compile test package install
site 生命周期 site 
```

