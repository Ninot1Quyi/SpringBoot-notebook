**提示：若看不到图片，请加速github，图床位于github上，可能会由于网络问题造成图片无法显示。加速工具可以选择[Watt Toolkit - 瓦特工具箱(Steam++官网) (steampp.net)](https://steampp.net/)，该工具加速失败问题解决方案[点此跳转]([Watt Toolkit加速github相关问题.md](https://github.com/Ninot1Quyi/SpringBoot-notebook/blob/main/Watt%20Toolkit%E5%8A%A0%E9%80%9Fgithub%E7%9B%B8%E5%85%B3%E9%97%AE%E9%A2%98.md))**

# 1.项目分析

1.项目功能:登录、注册、热销商品、用户管理(密码、个人信息、头像、收货地址）、 购物车（展示、增加、删除)、订单模块。
2.开发顺序:注册、登录、用户管理、购物车、商品、订单模块。

3.某一模块的开发：

● 持久层开发:依据前端页面的设置规划相关的SQL语句，以及进行配置
● 业务层开发:核心功能控制、业务操作以及异常的处理
● 控制层开发:接受请求、处理响应
● 前端开发:JS、Query、 AJAX这些技术来连接后台

# 2.项目环境

1.JDK：1.8版本及以上

2.开发的平台: idea专业版，[学生申请专业版IDEA的方法](HFUT学生申请专业版IDEA步骤.md)

3.maven：配置到idea，3.6.1,[一定要看的Macen配置过程](Maven使用和配置.md)

4.数据库：MariaDB、MySQL，5.1及以上

![image-20230316161949264](https://raw.githubusercontent.com/Ninot1Quyi/Typora-s-picture/master/img/image-20230316161949264.png)

# 3.搭建项目

1.项目名称：store，表示商城

2.结构：com.cy.store

```
java web
mybatis
mysql driver
```

![image-20230316162322558](https://raw.githubusercontent.com/Ninot1Quyi/Typora-s-picture/master/img/image-20230316162322558.png)

3.资源文件: resources文件夹下（static、templates）

4.单元测试：test.com.cy.store

5.在properties文件中配置数据库的连接源信息

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/store? useUnicode=true&characterEncoding=utf-8&serverTimezone=Asia/Shanghai
spring.datasource.username=sa
spring.datasource.password=qy.Ninot.52
#mybatis.mapper-locations=
#user.address.max-count=20
```

## **这里一定要注意使用的是MySQL，另外是视频中使用的navicat的版本是专业版，我就下载错了使用的是navicat-sqlserver，导致navicat一直找不到MySQL，心态炸裂**

专业版相关网站【https://www.jianshu.com/p/4bb2e2bfb449】

## **应该使用MySQL，教程中未使用SQL Server，以下配置过程可以跳过，<a href="#3.6">[点此跳过]</a>到下一步：**

~~SQL Server配置过程~~

<img src="https://raw.githubusercontent.com/Ninot1Quyi/Typora-s-picture/master/img/image-20230316171626240.png" alt="image-20230316171442447" style="zoom:50%;" />

<img src="https://raw.githubusercontent.com/Ninot1Quyi/Typora-s-picture/master/img/image-20230316171347699.png" alt="image-20230316171626240" style="zoom:50%;" />

<img src="https://raw.githubusercontent.com/Ninot1Quyi/Typora-s-picture/master/img/image-20230316171442447.png" alt="image-20230316171851191" style="zoom:50%;" />

<img src="https://raw.githubusercontent.com/Ninot1Quyi/Typora-s-picture/master/img/image-20230316171701104.png" alt="image-20230316171701104" style="zoom:50%;" />



<img src="https://raw.githubusercontent.com/Ninot1Quyi/Typora-s-picture/master/img/image-20230316180056330.png" alt="image-20230316171347699" style="zoom:50%;" />

**<span name = "3.6">Navicat连接数据库</span>**   

注意：这里不使用专业版Navicat可能找不到MySQL连接选项，如果未安装MySQL可以看<a href="#3.7A">[点此跳过]</a>

6.创建一个sotre数据库

```mysql
create database store character set utf-8;
```

7.测试连接

· 启动SpringBoot主类，是否有对应的Spring图形输出
· 在单元测试类中测试数据库的连接是否可以正常的加载

Q：测试出错，提示![image-20230316180056330](https://raw.githubusercontent.com/Ninot1Quyi/Typora-s-picture/master/img/image-20230316171851191.png)

A：其实在IDEA新建项目的时候选择了JAVA1.8，IDEA在生成项目后，在Maven中的配置依然会采用JAVA17，猜测的原因可能是IDEA的版本的太新了。

​	另外，其自动配置的MyBatis版本为3.0，而3.0以上的MyBatis版本只支持JAVA17。

​	关于application.properties的配置可以在该网站进行查询

[][mybatis-spring-boot-autoconfigure – Introduction](http://mybatis.org/spring-boot-starter/mybatis-spring-boot-autoconfigure/index.html)

修改后启动成功：

<img src="https://raw.githubusercontent.com/Ninot1Quyi/Typora-s-picture/master/img/image-20230316200739945.png" alt="image-20230316183120225" style="zoom:80%;" />

Q：数据库连接失败

A：教程中使用的是MySQL，数据库连接的配置语句使用的是MySQL的配置方式，

​	  解决办法，去换一个MySQL的数据库

​	**<span name = "3.7A">MySQL安装教程：</span>**   

​	我的安装方法，选择custom，然后一路next，在按照下面这个链接中的提示配置一下环境变量，缺点是MySQL安装在C盘，优点是省事儿。

[(210条消息) MySQL安装配置教程（超级详细、保姆级）_mysql安装教程_SoloVersion的博客-CSDN博客](https://blog.csdn.net/SoloVersion/article/details/123760428)

数据库连接成功！！！

![image-20230316200739945](https://raw.githubusercontent.com/Ninot1Quyi/Typora-s-picture/master/img/image-20230316183120225.png)

8. 访问项目的静态资源是否可以正常的加载。所有的静态资源复制到static目录下。

> 注意: idea对于JS代码的兼容性较差，编写了js代码但是有的时候不能够正常去加载。
>
> 1.idea缓存清理
>
> 2.clear-install
>
> 3.rebuild重新构建
>
> 4.重启idea和操作系统

成功启动网页：[http://localhost:8080/web/register.html]

![image-20230316202733321](https://raw.githubusercontent.com/Ninot1Quyi/Typora-s-picture/master/img/image-20230316202733321.png)
