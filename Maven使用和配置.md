# 1.Maven下载和导入IDEA

1.1下载

总下载网址

[Index of /dist/maven/maven-3 (apache.org)](https://archive.apache.org/dist/maven/maven-3/)

SpringBoot项目使用的maven下载地址

[Index of /dist/maven/maven-3/3.6.1/binaries (apache.org)](https://archive.apache.org/dist/maven/maven-3/3.6.1/binaries/)

选择![image-20230316181900548](https://raw.githubusercontent.com/Ninot1Quyi/Typora-s-picture/master/img/image-20230316181900548.png)

# 2.更换IDEA的Maven

更改前

![image-20230316182019591](https://raw.githubusercontent.com/Ninot1Quyi/Typora-s-picture/master/img/image-20230316182019591.png)

​	操作步骤，将“C:\Users\曲艺\.m2”下的两个文件夹直接复制到自己新建的repostiory中，然后将上述位置更改成新的地址。

​	新的settings.xml和repository地址如下图所示。

更改后

![image-20230316182004724](https://raw.githubusercontent.com/Ninot1Quyi/Typora-s-picture/master/img/image-20230316182004724.png)

# 3.更换国内镜像源

更换阿里源

打开settings.xml文件，加入如下内容，注意原来已经存在的<mirrors>不要覆盖掉了。

![image-20230316182628041](https://raw.githubusercontent.com/Ninot1Quyi/Typora-s-picture/master/img/image-20230316182628041.png)

```settings.xml
  <!-- 中央仓库在中国的镜像 -->
    <mirror>
        <id>alimaven</id>
        <name>aliyun maven</name>
        <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
        <mirrorOf>central</mirrorOf>
    </mirror>
```

# 4.更改IDEA中pom.xml的配置

​	我是用IDEA创建项目的时候存在这样的问题：在创建项目是已经选择好了JAVA的版本为1.8，但是在pom.xml文件中依然显示为JAVA17，另外其他相关的配置版本过高，也导致该项目无法使用。

​	可以参考该网站进行配置设置：

(http://mybatis.org/spring-boot-starter/mybatis-spring-boot-autoconfigure/index.html)

​	最终在“SpringBoot商城项目”下可用的pom.xml配置如下：

```pom.xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.7.0</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>
    <groupId>com.example</groupId>
    <artifactId>demo1</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <name>demo1</name>
    <description>demo1</description>
    <properties>
        <java.version>1.8</java.version>
    </properties>
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-freemarker</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.mybatis.spring.boot</groupId>
            <artifactId>mybatis-spring-boot-starter</artifactId>
            <version>2.1.4</version>
        </dependency>

        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <scope>runtime</scope>
        </dependency>
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <optional>true</optional>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
                <configuration>
                    <excludes>
                        <exclude>
                            <groupId>org.projectlombok</groupId>
                            <artifactId>lombok</artifactId>
                        </exclude>
                    </excludes>
                </configuration>
            </plugin>
        </plugins>
    </build>

</project>
```

