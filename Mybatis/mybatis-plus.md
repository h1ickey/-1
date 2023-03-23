# 课程介绍

- 了解Mybatis-Plus
- 整合Mybatis-Plus
- 通用CRUD
- Mybatis-Plus的配置
- 条件构造器

# 1、了解Mybatis-Plus

## 1.1、Mybatis-Plus介绍

MyBatis-Plus（简称 MP）是一个 MyBatis 的增强工具，在 MyBatis 的基础上只做增强不做改变，为简化开发、提高 效率而生。

官网：https://mybatis.plus/ 或 https://mp.baomidou.com/

[![image-20221025121634953](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221025121634953.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221025121634953.png)

[![image-20221025121654252](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221025121654252.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221025121654252.png)

## 1.2、代码以及文档

文档地址：https://mybatis.plus/guide/

源码地址：https://github.com/baomidou/mybatis-plus

## 1.3、特性

- **无侵入**：只做增强不做改变，引入它不会对现有工程产生影响，如丝般顺滑
- **损耗小**：启动即会自动注入基本 CURD，性能基本无损耗，直接面向对象操作
- **强大的 CRUD 操作**：内置通用 Mapper、通用 Service，仅仅通过少量配置即可实现单表大部分 CRUD 操作， 更有强大的条件构造器，满足各类使用需求
- **支持 Lambda 形式调用**：通过 Lambda 表达式，方便的编写各类查询条件，无需再担心字段写错
- **支持多种数据库**：支持 MySQL、MariaDB、Oracle、DB2、H2、HSQL、SQLite、Postgre、 SQLServer2005、SQLServer 等多种数据库 支持主键自动生成：支持多达 4 种主键策略（内含分布式唯一 ID 生成器 - Sequence），可自由配置，完美解 决主键问题
- **支持 XML 热加载**：Mapper 对应的 XML 支持热加载，对于简单的 CRUD 操作，甚至可以无 XML 启动 支持 ActiveRecord 模式：
- **支持 ActiveRecord 形式调用**，实体类只需继承 Model 类即可进行强大的 CRUD 操 作
- **支持自定义全局通用操作**：支持全局通用方法注入（ Write once, use anywhere ）
- **支持关键词自动转义**：支持数据库关键词（order、key……）自动转义，还可自定义关键词
- **内置代码生成器**：采用代码或者 Maven 插件可快速生成 Mapper 、 Model 、 Service 、 Controller 层代码， 支持模板引擎，更有超多自定义配置等您来使用
- **内置分页插件**：基于 MyBatis 物理分页，开发者无需关心具体操作，配置好插件之后，写分页等同于普通 List 查询 内置性能分析插件：可输出 Sql 语句以及其执行时间，建议开发测试时启用该功能，能快速揪出慢查询
- **内置全局拦截插件**：提供全表 delete 、 update 操作智能分析阻断，也可自定义拦截规则，预防误操作
- **内置 Sql 注入剥离器**：支持 Sql 注入剥离，有效预防 Sql 注入攻击

## 1.4、架构

[![image-20221025122017908](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221025122017908.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221025122017908.png)

## 1.5、作者

Mybatis-Plus是由baomidou（苞米豆）组织开发并且开源的，目前该组织大概有30人左右。

码云地址：https://gitee.com/organizations/baomidou

[![image-20221025122245055](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221025122245055.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221025122245055.png)

# 2、快速开始

对于Mybatis整合MP有常常有三种用法，分别是`Mybatis+MP`、`Spring+Mybatis+MP`、`Spring Boot+Mybatis+MP`。

## 2.1、创建数据库以及表

[![image-20221025122741423](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221025122741423.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221025122741423.png)

```
SQL
-- 创建测试表
CREATE TABLE `tb_user` (
`id` bigint(20) NOT NULL AUTO_INCREMENT COMMENT '主键ID',
`user_name` varchar(20) NOT NULL COMMENT '用户名',
`password` varchar(20) NOT NULL COMMENT '密码',
`name` varchar(30) DEFAULT NULL COMMENT '姓名',
`age` int(11) DEFAULT NULL COMMENT '年龄',
`email` varchar(50) DEFAULT NULL COMMENT '邮箱',
PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8;
-- 插入测试数据
INSERT INTO `tb_user` (`id`, `user_name`, `password`, `name`, `age`, `email`) VALUES
('1', 'zhangsan', '123456', '张三', '18', 'test1@itcast.cn');
INSERT INTO `tb_user` (`id`, `user_name`, `password`, `name`, `age`, `email`) VALUES
('2', 'lisi', '123456', '李四', '20', 'test2@itcast.cn');
INSERT INTO `tb_user` (`id`, `user_name`, `password`, `name`, `age`, `email`) VALUES
('3', 'wangwu', '123456', '王五', '28', 'test3@itcast.cn');
INSERT INTO `tb_user` (`id`, `user_name`, `password`, `name`, `age`, `email`) VALUES
('4', 'zhaoliu', '123456', '赵六', '21', 'test4@itcast.cn');
INSERT INTO `tb_user` (`id`, `user_name`, `password`, `name`, `age`, `email`) VALUES
('5', 'sunqi', '123456', '孙七', '24', 'test5@itcast.cn');
```

## 2.2、创建工程

**创建maven工程**

[![image-20221025142419290](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221025142419290.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221025142419290.png)

**配置依赖**

```
XML
<!-- mybatis-plus插件依赖 -->
       <dependency>
           <groupId>com.baomidou</groupId>
           <artifactId>mybatis-plus</artifactId>
           <version>3.1.1</version>
       </dependency>
       <!-- MySql -->
       <dependency>
           <groupId>mysql</groupId>
           <artifactId>mysql-connector-java</artifactId>
           <version>5.1.47</version>
       </dependency>
       <!-- 连接池 -->
       <dependency>
           <groupId>com.alibaba</groupId>
           <artifactId>druid</artifactId>
           <version>1.0.11</version>
       </dependency>
       <!--简化bean代码的工具包-->
       <dependency>
           <groupId>org.projectlombok</groupId>
           <artifactId>lombok</artifactId>
           <optional>true</optional>
           <version>1.18.4</version>
       </dependency>
       <dependency>
           <groupId>junit</groupId>
           <artifactId>junit</artifactId>
           <version>4.12</version>
       </dependency>
       <dependency>
           <groupId>org.slf4j</groupId>
           <artifactId>slf4j-log4j12</artifactId>
           <version>1.6.4</version>
       </dependency>

   </dependencies>

   <build>
       <plugins>
           <plugin>
               <groupId>org.apache.maven.plugins</groupId>
               <artifactId>maven-compiler-plugin</artifactId>
               <version>3.10.1</version>
               <configuration>
                   <source>1.8</source>
                   <target>1.8</target>
               </configuration>
           </plugin>
       </plugins>
   </build>
```

## 2.3、Mybatis + MP

下面演示，通过纯Mybatis与Mybatis-Plus整合。

### 2.3.1、创建子Module

![截屏2022-10-25 14.41.43](/img/黑马程序员-Mybatis-Plus/截屏2022-10-25 14.41.43.png)

![截屏2022-10-25 14.45.35](/img/黑马程序员-Mybatis-Plus/截屏2022-10-25 14.45.35.png)

```
XML
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <parent>
        <artifactId>itcast-mybatis-plus</artifactId>
        <groupId>org.example</groupId>
        <version>1.0-SNAPSHOT</version>
    </parent>
    <modelVersion>4.0.0</modelVersion>

    <artifactId>itcast-mybatis-plus-simple</artifactId>

    <properties>
        <maven.compiler.source>8</maven.compiler.source>
        <maven.compiler.target>8</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>

</project>
```

**新建配置文件**`log4j.properties`

```
XML
log4j.rootLogger=DEBUG,A1
log4j.appender.A1=org.apache.log4j.ConsoleAppender
log4j.appender.A1.layout=org.apache.log4j.PatternLayout
log4j.appender.A1.layout.ConversionPattern=[%t] [%c]-[%p] %m%n
```

[![image-20221025145455050](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221025145455050.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221025145455050.png)

### 2.3.2、Mybatis实现查询User

**第一步，编写mybatis-config.xml文件**：

```
XML
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
    <environments default="development">
        <environment id="development">
            <transactionManager type="JDBC"/>
            <dataSource type="POOLED">
                <property name="driver" value="com.mysql.jdbc.Driver"/>
                <property name="url" value="jdbc:mysql://127.0.0.1:3306/mp?useUnicode=true&amp;characterEncoding=utf8&amp;autoReconnect=true&amp;allowMultiQueries=true&amp;useSSL=false"/>
                <property name="username" value="root"/>
                <property name="password" value="Xuwei19941214~"/>
            </dataSource>
        </environment>
    </environments>
    <mappers>
        <mapper resource="UserMapper.xml"/>
    </mappers>
</configuration>
```

[![image-20221025150511683](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221025150511683.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221025150511683.png)

第二步，编写User实体对象：（这里使用lombok进行了进化bean操作）

```
JAVA
package org.example.cn.itcast.mp.simple.pojo;

import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;
@Data
@NoArgsConstructor
@AllArgsConstructor
public class User {
    private Long id;
    private String userName;
    private String password;
    private String name;
    private Integer age;
    private String email;
}
```

第三步，编写UserMapper接口：

```
JAVA
package org.example.cn.itcast.mp.simple.mapper;

import org.example.cn.itcast.mp.simple.pojo.User;

import java.util.List;
public interface UserMapper {
    List<User> findAll();
}
```

第四步，编写UserMapper.xml文件：

```
XML
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="cn.itcast.mp.simple.mapper.UserMapper">
    <select id="findAll" resultType="org.example.cn.itcast.mp.simple.pojo.User">
        select * from tb_user
    </select>
</mapper>
```

第五步，编写TestMybatis测试用例：

```
JAVA
package cn.itcast.mp.simple;

import org.apache.ibatis.io.Resources;
import org.apache.ibatis.session.SqlSession;
import org.apache.ibatis.session.SqlSessionFactory;
import org.apache.ibatis.session.SqlSessionFactoryBuilder;
import org.example.cn.itcast.mp.simple.mapper.UserMapper;
import org.example.cn.itcast.mp.simple.pojo.User;
import org.junit.Test;

import java.io.InputStream;
import java.util.List;

public class TestMybatis {


    @Test
    public void testUserList() throws Exception{
        String resource = "mybatis-config.xml";
        InputStream inputStream = Resources.getResourceAsStream(resource);
        SqlSessionFactory sqlSessionFactory = new
                SqlSessionFactoryBuilder().build(inputStream);
        SqlSession sqlSession = sqlSessionFactory.openSession();
        UserMapper userMapper = sqlSession.getMapper(UserMapper.class);
        List<User> list = userMapper.findAll();

        for (User user : list) {
            System.out.println(user);
        }

    }

}
```

测试结果：

```
BASH
[main] [org.apache.ibatis.logging.LogFactory]-[DEBUG] Logging initialized using 'class org.apache.ibatis.logging.slf4j.Slf4jImpl' adapter.
[main] [org.apache.ibatis.datasource.pooled.PooledDataSource]-[DEBUG] PooledDataSource forcefully closed/removed all connections.
[main] [org.apache.ibatis.datasource.pooled.PooledDataSource]-[DEBUG] PooledDataSource forcefully closed/removed all connections.
[main] [org.apache.ibatis.datasource.pooled.PooledDataSource]-[DEBUG] PooledDataSource forcefully closed/removed all connections.
[main] [org.apache.ibatis.datasource.pooled.PooledDataSource]-[DEBUG] PooledDataSource forcefully closed/removed all connections.
[main] [org.apache.ibatis.transaction.jdbc.JdbcTransaction]-[DEBUG] Opening JDBC Connection
[main] [org.apache.ibatis.datasource.pooled.PooledDataSource]-[DEBUG] Created connection 1997287019.
[main] [org.apache.ibatis.transaction.jdbc.JdbcTransaction]-[DEBUG] Setting autocommit to false on JDBC Connection [com.mysql.jdbc.JDBC4Connection@770c2e6b]
[main] [org.example.cn.itcast.mp.simple.mapper.UserMapper.findAll]-[DEBUG] ==>  Preparing: select * from tb_user 
[main] [org.example.cn.itcast.mp.simple.mapper.UserMapper.findAll]-[DEBUG] ==> Parameters: 
[main] [org.example.cn.itcast.mp.simple.mapper.UserMapper.findAll]-[DEBUG] <==      Total: 5
User(id=1, userName=null, password=123456, name=张三, age=18, email=test1@itcast.cn)
User(id=2, userName=null, password=123456, name=李四, age=20, email=test2@itcast.cn)
User(id=3, userName=null, password=123456, name=王五, age=28, email=test3@itcast.cn)
User(id=4, userName=null, password=123456, name=赵六, age=21, email=test4@itcast.cn)
User(id=5, userName=null, password=123456, name=孙七, age=24, email=test5@itcast.cn)

Process finished with exit code 0
```

### 2.3.3、Mybatis+MP实现查询User

第一步，将UserMapper继承BaseMapper，将拥有了BaseMapper中的所有方法：

```
JAVA
package org.example.cn.itcast.mp.simple.mapper;

import com.baomidou.mybatisplus.core.mapper.BaseMapper;
import org.example.cn.itcast.mp.simple.pojo.User;

import java.util.List;
public interface UserMapper extends BaseMapper<User> {
    List<User> findAll();
}
```

第二步，使用MP中的MybatisSqlSessionFactoryBuilder进程构建：

```
JAVA
package cn.itcast.mp.simple;

import com.baomidou.mybatisplus.core.MybatisSqlSessionFactoryBuilder;
import org.apache.ibatis.io.Resources;
import org.apache.ibatis.session.SqlSession;
import org.apache.ibatis.session.SqlSessionFactory;
import org.apache.ibatis.session.SqlSessionFactoryBuilder;
import org.example.cn.itcast.mp.simple.mapper.UserMapper;
import org.example.cn.itcast.mp.simple.pojo.User;
import org.junit.Test;

import java.io.InputStream;
import java.util.List;

public class TestMybatisPlus {


    @Test
    public void testUserList() throws Exception{
        String resource = "mybatis-config.xml";
        InputStream inputStream = Resources.getResourceAsStream(resource);
        //这里使用的是MP中的MybatisSqlSessionFactoryBuilder
        SqlSessionFactory sqlSessionFactory = new
                MybatisSqlSessionFactoryBuilder().build(inputStream);
        SqlSession sqlSession = sqlSessionFactory.openSession();
        UserMapper userMapper = sqlSession.getMapper(UserMapper.class);

        // 可以调用BaseMapper中定义的方法
        List<User> list = userMapper.selectList(null);
        for (User user : list) {
            System.out.println(user);
        }

    }

}
```

运行报错：

[![image-20221026110214512](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221026110214512.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221026110214512.png)

解决：在`User`对象中添加`@TableName`，指定数据库表名

[![image-20221026110321585](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221026110321585.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221026110321585.png)

测试：

```
JAVA
[main] [org.example.cn.itcast.mp.simple.mapper.UserMapper.selectList]-[DEBUG] ==>  Preparing: SELECT id,user_name,password,name,age,email FROM tb_user 
[main] [org.example.cn.itcast.mp.simple.mapper.UserMapper.selectList]-[DEBUG] ==> Parameters: 
[main] [org.example.cn.itcast.mp.simple.mapper.UserMapper.selectList]-[DEBUG] <==      Total: 5
User(id=1, userName=zhangsan, password=123456, name=张三, age=18, email=test1@itcast.cn)
User(id=2, userName=lisi, password=123456, name=李四, age=20, email=test2@itcast.cn)
User(id=3, userName=wangwu, password=123456, name=王五, age=28, email=test3@itcast.cn)
User(id=4, userName=zhaoliu, password=123456, name=赵六, age=21, email=test4@itcast.cn)
User(id=5, userName=sunqi, password=123456, name=孙七, age=24, email=test5@itcast.cn)
```

简单说明：

由于使用了`MybatisSqlSessionFactoryBuilder`进行了构建，继承的`BaseMapper`中的方法就载入到了 `SqlSession`中，所以就可以直接使用相关的方法；

如图：

[![image-20221026110808833](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221026110808833.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221026110808833.png)

## 2.4、Spring + Mybatis + MP

引入了Spring框架，数据源、构建等工作就交给了Spring管理。

### 2.4.1、创建子Module

[![image-20221026111546338](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221026111546338.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221026111546338.png)

```
XML
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <parent>
        <artifactId>itcast-mybatis-plus</artifactId>
        <groupId>org.example</groupId>
        <version>1.0-SNAPSHOT</version>
    </parent>
    <modelVersion>4.0.0</modelVersion>

    <artifactId>itcast-mybatis-plus-spring</artifactId>

    <dependencies>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-webmvc</artifactId>
            <version>${spring.version}</version>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-jdbc</artifactId>
            <version>${spring.version}</version>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-test</artifactId>
            <version>${spring.version}</version>
        </dependency>
    </dependencies>

    <properties>
        <spring.version>5.1.6.RELEASE</spring.version>
        <maven.compiler.source>8</maven.compiler.source>
        <maven.compiler.target>8</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>

</project>
```

### 2.4.2、实现查询User

第一步，编写`jdbc.properties`

```
PROPERTIES
jdbc.driver=com.mysql.jdbc.Driver
jdbc.url=jdbc:mysql://127.0.0.1:3306/mp?
useUnicode=true&characterEncoding=utf8&autoReconnect=true&allowMultiQueries=true&useSSL=false
jdbc.username=root
jdbc.password=root
```

第二步，编写`applicationContext.xml`

```
XML
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
http://www.springframework.org/schema/beans/spring-beans.xsd
http://www.springframework.org/schema/context
http://www.springframework.org/schema/context/spring-context.xsd">
    <context:property-placeholder location="classpath:*.properties"/>
    <!-- 定义数据源 -->
    <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource"
          destroy-method="close">
        <property name="url" value="${jdbc.url}"/>
        <property name="username" value="${jdbc.username}"/>
        <property name="password" value="${jdbc.password}"/>
        <property name="driverClassName" value="${jdbc.driver}"/>
        <property name="maxActive" value="10"/>
        <property name="minIdle" value="5"/>
    </bean>
    <!--这里使用MP提供的sqlSessionFactory，完成了Spring与MP的整合-->
    <bean id="sqlSessionFactory"
          class="com.baomidou.mybatisplus.extension.spring.MybatisSqlSessionFactoryBean">
        <property name="dataSource" ref="dataSource"/>
    </bean>
    <!--扫描mapper接口，使用的依然是Mybatis原生的扫描器-->
    <bean class="org.mybatis.spring.mapper.MapperScannerConfigurer">
        <property name="basePackage" value="org.example.cn.itcast.mp.simple.mapper"/>
    </bean>
</beans>
```

第三步，编写User对象以及UserMapper接口：

```
JAVA
package org.example.cn.itcast.mp.simple.pojo;

import com.baomidou.mybatisplus.annotation.TableName;
import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;

@Data
@NoArgsConstructor
@AllArgsConstructor
@TableName("tb_user")
public class User {
    private Long id;
    private String userName;
    private String password;
    private String name;
    private Integer age;
    private String email;
}
JAVA
package org.example.cn.itcast.mp.simple.mapper;

import com.baomidou.mybatisplus.core.mapper.BaseMapper;
import org.example.cn.itcast.mp.simple.pojo.User;

import java.util.List;

public interface UserMapper extends BaseMapper<User> {
  
}
```

第四步，编写测试用例：

```
JAVA
package cn.itcast.mp.simple;

import org.example.cn.itcast.mp.simple.mapper.UserMapper;
import org.example.cn.itcast.mp.simple.pojo.User;
import org.junit.Test;
import org.junit.runner.RunWith;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.test.context.ContextConfiguration;
import org.springframework.test.context.junit4.SpringJUnit4ClassRunner;

import java.util.List;

@RunWith(SpringJUnit4ClassRunner.class)
@ContextConfiguration(locations = "classpath:applicationContext.xml")
public class TestSpringMP {
    @Autowired
    private UserMapper userMapper;
    @Test
    public void testSelectList(){
        List<User> users = this.userMapper.selectList(null);
        for (User user : users) {
            System.out.println(user);
        }
    }

}
```

添加测试模块的配置

[![image-20221026121206190](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221026121206190.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221026121206190.png)

测试

```
BASH
[main] [org.example.cn.itcast.mp.simple.mapper.UserMapper.selectList]-[DEBUG] ==>  Preparing: SELECT id,user_name,password,name,age,email FROM tb_user 
[main] [org.example.cn.itcast.mp.simple.mapper.UserMapper.selectList]-[DEBUG] ==> Parameters: 
[main] [org.example.cn.itcast.mp.simple.mapper.UserMapper.selectList]-[DEBUG] <==      Total: 5
[main] [org.mybatis.spring.SqlSessionUtils]-[DEBUG] Closing non transactional SqlSession [org.apache.ibatis.session.defaults.DefaultSqlSession@24959ca4]
User(id=1, userName=zhangsan, password=123456, name=张三, age=18, email=test1@itcast.cn)
User(id=2, userName=lisi, password=123456, name=李四, age=20, email=test2@itcast.cn)
User(id=3, userName=wangwu, password=123456, name=王五, age=28, email=test3@itcast.cn)
User(id=4, userName=zhaoliu, password=123456, name=赵六, age=21, email=test4@itcast.cn)
User(id=5, userName=sunqi, password=123456, name=孙七, age=24, email=test5@itcast.cn)
```

## 2.5、SpringBoot + Mybatis + MP

使用`SpringBoot`将进一步的简化`MP`的整合，需要注意的是，由于使用`SpringBoot`需要继承`parent`，所以需要重新创 建工程，并不是创建子`Module`。

### 2.5.1、创建工程

[![image-20221026122123916](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221026122123916.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221026122123916.png)

### 2.5.2、导入依赖

```
XML
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.7.5</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>
    <groupId>com.example</groupId>
    <artifactId>itcast-mp-springboot</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <name>itcast-mp-springboot</name>
    <description>itcast-mp-springboot</description>
    <properties>
        <java.version>1.8</java.version>
    </properties>
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter</artifactId>
        </dependency>
        <!--简化代码的工具包-->
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <optional>true</optional>
        </dependency>
        <!--mybatis-plus的springboot支持-->
        <dependency>
            <groupId>com.baomidou</groupId>
            <artifactId>mybatis-plus-boot-starter</artifactId>
            <version>3.1.1</version>
        </dependency>
        <!--mysql驱动-->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>5.1.47</version>
        </dependency>
        <dependency>
            <groupId>org.slf4j</groupId>
            <artifactId>slf4j-log4j12</artifactId>
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

**配置日志文件**

```
PROPERTIES
log4j.rootLogger=DEBUG,A1
log4j.appender.A1=org.apache.log4j.ConsoleAppender
log4j.appender.A1.layout=org.apache.log4j.PatternLayout
log4j.appender.A1.layout.ConversionPattern=[%t] [%c]-[%p] %m%n
```

[![image-20221026150031093](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221026150031093.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221026150031093.png)

### 2.5.3、编写application.properties

```
PROPERTIES
spring.application.name = itcast-mp-springboot
spring.datasource.driver-class-name=com.mysql.jdbc.Driver
spring.datasource.url=jdbc:mysql://127.0.0.1:3306/mp?
useUnicode=true&characterEncoding=utf8&autoReconnect=true&allowMultiQueries=true&useSSL=false
spring.datasource.username=root
spring.datasource.password=root

logging.level.com.baomidou.mybatisplus=DEBUG
#项目mapper目录
logging.level.cn.itcast.mp.mapper=DEBUG
mybatis-plus.configuration.log-impl=org.apache.ibatis.logging.slf4j.Slf4jImpl
```

[![image-20221027112128002](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221027112128002.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221027112128002.png)

### 2.5.4、编写pojo

```
JAVA
package cn.itcast.mp.pojo;

import com.baomidou.mybatisplus.annotation.TableName;
import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;
@Data
@NoArgsConstructor
@AllArgsConstructor
@TableName("tb_user")
public class User {
    private Long id;
    private String userName;
    private String password;
    private String name;
    private Integer age;
    private String email;
}
```

[![image-20221026150647229](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221026150647229.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221026150647229.png)

### 2.5.5、编写mapper

```
JAVA
package cn.itcast.mp.mapper;

import cn.itcast.mp.pojo.User;
import com.baomidou.mybatisplus.core.mapper.BaseMapper;
public interface UserMapper extends BaseMapper<User> {
}
```

[![image-20221026150733439](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221026150733439.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221026150733439.png)

### 2.5.6、编写启动类

新建springboot项目时可以自动生成

```
JAVA
package com.example.itcastmpspringboot;

import org.mybatis.spring.annotation.MapperScan;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@MapperScan("cn.itcast.mp.mapper") //设置mapper接口的扫描包
@SpringBootApplication
public class ItcastMpSpringbootApplication {

    public static void main(String[] args) {
        SpringApplication.run(ItcastMpSpringbootApplication.class, args);
    }

}
```

[![image-20221026151123697](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221026151123697.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221026151123697.png)

### 2.5.7、编写测试用例

```
JAVA
package cn.itcast.mp;

import cn.itcast.mp.mapper.UserMapper;
import cn.itcast.mp.pojo.User;
import org.junit.jupiter.api.Test;
import org.junit.runner.RunWith;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.test.context.junit4.SpringRunner;

import java.util.List;

@SpringBootTest
@RunWith(SpringRunner.class)
class ItcastMpSpringbootApplicationTests {

    @Autowired
    private UserMapper userMapper;
    @Test
    public void testSelect() {
        List<User> userList = userMapper.selectList(null);
        for (User user : userList) {
            System.out.println(user);
        }
    }

}
```

测试

[![image-20221026153826286](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221026153826286.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221026153826286.png)

可以正常查询出数据，但是idea工具会有一个报红

**解决方法**

将mapper层进行注入

[![image-20221026153924016](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221026153924016.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221026153924016.png)

# 3、通用CRUD

通过前面的学习，我们了解到通过继承BaseMapper就可以获取到各种各样的单表操作，接下来我们将详细讲解这些 操作。

[![image-20221027103547226](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221027103547226.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221027103547226.png)

## 3.1、插入操作

### 3.1.1、方法定义

```
JAVA
/**
* 插入一条记录
*
* @param entity 实体对象
*/
int insert(T entity);
```

### 3.1.2、测试用例

```
JAVA
package cn.itcast.mp;


import cn.itcast.mp.mapper.UserMapper;
import cn.itcast.mp.pojo.User;
import org.junit.Test;
import org.junit.runner.RunWith;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.test.context.junit4.SpringRunner;

@RunWith(SpringRunner.class)
@SpringBootTest
public class UserMapperTest {

    @Autowired
    private UserMapper userMapper;

    @Test
    public void testInsert(){
        User user = new User();
        user.setAge(20);
        user.setEmail("test@itcast.cn");
        user.setName("曹操");
        user.setUserName("caocao");
        user.setPassword("123456");
        int result = this.userMapper.insert(user); //返回的result是受影响的行数，并不是自增后的id
        System.out.println("result = " + result);
        System.out.println(user.getId()); //自增后的id会回填到对象中
    }
}
```

### 3.1.3、测试

```
JAVA
2022-10-27 11:10:19.222  INFO 1387 --- [           main] cn.itcast.mp.UserMapperTest              : Started UserMapperTest in 3.961 seconds (JVM running for 5.2)
2022-10-27 11:10:19.597 DEBUG 1387 --- [           main] cn.itcast.mp.mapper.UserMapper.insert    : ==>  Preparing: INSERT INTO tb_user ( id, user_name, password, name, age, email ) VALUES ( ?, ?, ?, ?, ?, ? ) 
2022-10-27 11:10:19.620 DEBUG 1387 --- [           main] cn.itcast.mp.mapper.UserMapper.insert    : ==> Parameters: 1585468910826754050(Long), caocao(String), 123456(String), 曹操(String), 20(Integer), test@itcast.cn(String)
2022-10-27 11:10:19.626 DEBUG 1387 --- [           main] cn.itcast.mp.mapper.UserMapper.insert    : <==    Updates: 1
result = 1
1585468910826754050
2022-10-27 11:10:19.654  INFO 1387 --- [ionShutdownHook] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown initiated...
2022-10-27 11:10:19.690  INFO 1387 --- [ionShutdownHook] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown completed.
```

[![image-20221027112345047](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221027112345047.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221027112345047.png)

可以看到，数据已经写入到了数据库，但是，id的值不正确，我们期望的是数据库自增长，实际是MP生成了id的值 写入到了数据库。 如何设置id的生成策略呢？

MP支持的id策略：

```
JAVA
package com.baomidou.mybatisplus.annotation;
import lombok.Getter;
/**
* 生成ID类型枚举类
*
* @author hubin
* @since 2015-11-10
*/
@Getter
public enum IdType {
/**
* 数据库ID自增
*/
AUTO(0),
/**
* 该类型为未设置主键类型
*/
NONE(1),
/**
* 用户输入ID
* <p>该类型可以通过自己注册自动填充插件进行填充</p>
*/
INPUT(2),
/* 以下3种类型、只有当插入对象ID 为空，才自动填充。 */
/**
* 全局唯一ID (idWorker)
*/
ID_WORKER(3),
/**
* 全局唯一ID (UUID)
*/
UUID(4),
/**
* 字符串全局唯一ID (idWorker 的字符串表示)
*/
ID_WORKER_STR(5);
private final int key;
IdType(int key) {
this.key = key;
}
}
```

修改当前自增长的id

执行插入操作

[![image-20221027114545829](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221027114545829.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221027114545829.png)

[![image-20221027121309606](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221027121309606.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221027121309606.png)

[![image-20221027121339725](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221027121339725.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221027121339725.png)

### 3.1.4、@TableField

在MP中通过`@TableField`注解可以指定字段的一些属性，常常解决的问题有2个：

1、对象中的属性名和字段名不一致的问题（非驼峰）

2、对象中的属性字段在表中不存在的问题

使用：

[![image-20221027121954576](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221027121954576.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221027121954576.png)

[![image-20221027122717595](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221027122717595.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221027122717595.png)

添加`@TableField(exist = false )`后正常插入

[![image-20221027122919602](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221027122919602.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221027122919602.png)

其他用法，如大字段不加入查询字段：

[![image-20221027122023261](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221027122023261.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221027122023261.png)

效果：

[![image-20221027123203415](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221027123203415.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221027123203415.png)

## 3.2、更新操作

在MP中，更新操作有2种，一种是根据id更新，另一种是根据条件更新。

### 3.2.1、根据id更新

方法定义：

```
JAVA
/**
* 根据 ID 修改
*
* @param entity 实体对象
*/
int updateById(@Param(Constants.ENTITY) T entity);
```

测试：

```
JAVA
@Test
   public void testUpdateById() {
       User user = new User();
       user.setId(6L); //主键
       user.setAge(21); //更新的字段
       //根据id更新，更新不为null的字段
       this.userMapper.updateById(user);
   }
```

结果：

```
BASH
2022-10-28 10:14:47.302  INFO 1261 --- [           main] c.i.m.ItcastMpSpringbootApplicationTests : Started ItcastMpSpringbootApplicationTests in 4.081 seconds (JVM running for 5.654)
2022-10-28 10:14:47.603 DEBUG 1261 --- [           main] c.i.mp.mapper.UserMapper.updateById      : ==>  Preparing: UPDATE tb_user SET age=? WHERE id=? 
2022-10-28 10:14:47.637 DEBUG 1261 --- [           main] c.i.mp.mapper.UserMapper.updateById      : ==> Parameters: 21(Integer), 6(Long)
2022-10-28 10:14:47.643 DEBUG 1261 --- [           main] c.i.mp.mapper.UserMapper.updateById      : <==    Updates: 1
```

[![image-20221028101737072](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221028101737072.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221028101737072.png)

### 3.2.2、根据条件更新

方法定义：

```
JAVA
/**
* 根据 whereEntity 条件，更新记录
*
* @param entity 实体对象 (set 条件值,可以为 null)
* @param updateWrapper 实体对象封装操作类（可以为 null,里面的 entity 用于生成 where 语句）
*/
int update(@Param(Constants.ENTITY) T entity, @Param(Constants.WRAPPER) Wrapper<T>
updateWrapper);
```

测试用例：

```
JAVA
@Test
 public void testUpdateByQuery(){

     User user = new User();
     user.setAge(22);
	//更新的条件
     QueryWrapper<User> objectQueryWrapper = new QueryWrapper<>();
     objectQueryWrapper.eq("id",6);
	//执行更新操作
     int update = this.userMapper.update(user, objectQueryWrapper);
     System.out.println("result="+update);
 }
```

或者，通过UpdateWrapper进行更新：

```
JAVA
@Test
   public  void testUpdateByUpdateWrapper(){
			//更新的条件以及字段
       UpdateWrapper<User> objectUpdateWrapper = new UpdateWrapper<>();
       objectUpdateWrapper.eq("id",6).set("age",23);

			//执行更新操作
       int update = this.userMapper.update(null, objectUpdateWrapper);
       System.out.println("result="+update );


   }
```

测试结果：

```
BASH
2022-10-28 10:25:53.316  INFO 1314 --- [           main] c.i.m.ItcastMpSpringbootApplicationTests : Started ItcastMpSpringbootApplicationTests in 3.449 seconds (JVM running for 4.88)
2022-10-28 10:25:53.640 DEBUG 1314 --- [           main] cn.itcast.mp.mapper.UserMapper.update    : ==>  Preparing: UPDATE tb_user SET age=? WHERE id = ? 
2022-10-28 10:25:53.698 DEBUG 1314 --- [           main] cn.itcast.mp.mapper.UserMapper.update    : ==> Parameters: 23(Integer), 6(Integer)
2022-10-28 10:25:53.710 DEBUG 1314 --- [           main] cn.itcast.mp.mapper.UserMapper.update    : <==    Updates: 1
result=1
2022-10-28 10:25:53.763  INFO 1314 --- [ionShutdownHook] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown initiated...
2022-10-28 10:25:53.788  INFO 1314 --- [ionShutdownHook] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown completed.
```

均可达到更新的效果。 关于`wrapper`更多的用法后面会详细讲解。

## 3.3、删除操作

### 3.3.1、deleteById

方法定义：

```
JAVA
/**
* 根据 ID 删除
*
* @param id 主键ID
*/
int deleteById(Serializable id);
```

测试用例：

```
JAVA
@Test
   public void testDeleteById() {
       //执行删除操作
       int result = this.userMapper.deleteById(6L);
       System.out.println("result = " + result);
   }
```

结果：

```
BASH
2022-10-28 10:28:49.951  INFO 1326 --- [           main] c.i.m.ItcastMpSpringbootApplicationTests : Started ItcastMpSpringbootApplicationTests in 3.916 seconds (JVM running for 5.418)
2022-10-28 10:28:50.205 DEBUG 1326 --- [           main] c.i.mp.mapper.UserMapper.deleteById      : ==>  Preparing: DELETE FROM tb_user WHERE id=? 
2022-10-28 10:28:50.236 DEBUG 1326 --- [           main] c.i.mp.mapper.UserMapper.deleteById      : ==> Parameters: 6(Long)
2022-10-28 10:28:50.244 DEBUG 1326 --- [           main] c.i.mp.mapper.UserMapper.deleteById      : <==    Updates: 1
result = 1
2022-10-28 10:28:50.293  INFO 1326 --- [ionShutdownHook] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown initiated...
2022-10-28 10:28:50.318  INFO 1326 --- [ionShutdownHook] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown completed.
```

[![image-20221028102951516](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221028102951516.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221028102951516.png)

数据被删除。

### 3.3.2、deleteByMap

方法定义：

```
JAVA
/**
* 根据 columnMap 条件，删除记录
*
* @param columnMap 表字段 map 对象
*/
int deleteByMap(@Param(Constants.COLUMN_MAP) Map<String, Object> columnMap);
```

测试用例：

```
JAVA
@Test
   public  void  testDeleteByMap(){
       HashMap<String, Object> objectObjectHashMap = new HashMap<>();
       objectObjectHashMap.put("age",20);
       objectObjectHashMap.put("name","张三");

       int i = this.userMapper.deleteByMap(objectObjectHashMap);
       System.out.println("result="+i);

   }
```

结果：

```
BASH
2022-10-28 10:35:20.650  INFO 1365 --- [           main] c.i.m.ItcastMpSpringbootApplicationTests : Started ItcastMpSpringbootApplicationTests in 3.496 seconds (JVM running for 4.92)
2022-10-28 10:35:20.937 DEBUG 1365 --- [           main] c.i.mp.mapper.UserMapper.deleteByMap     : ==>  Preparing: DELETE FROM tb_user WHERE name = ? AND age = ? 
2022-10-28 10:35:20.967 DEBUG 1365 --- [           main] c.i.mp.mapper.UserMapper.deleteByMap     : ==> Parameters: 张三(String), 20(Integer)
2022-10-28 10:35:20.974 DEBUG 1365 --- [           main] c.i.mp.mapper.UserMapper.deleteByMap     : <==    Updates: 0
result=0
```

### 3.3.3、delete

方法定义：

```
JAVA
/**
* 根据 entity 条件，删除记录
*
* @param wrapper 实体对象封装操作类（可以为 null）
*/
int delete(@Param(Constants.WRAPPER) Wrapper<T> wrapper);
```

测试用例：

```
JAVA
@Test
  public void testDeleteByQueryWapper(){

      User user = new User();
      user.setAge(20);
      user.setName("张三");

      QueryWrapper<User> objectQueryWrapper = new QueryWrapper<>(user);
      int delete = this.userMapper.delete(objectQueryWrapper);
      System.out.println("result ="+ delete);

  }
```

结果：

```
BASH
2022-10-28 10:45:13.485  INFO 1392 --- [           main] c.i.m.ItcastMpSpringbootApplicationTests : Started ItcastMpSpringbootApplicationTests in 4.318 seconds (JVM running for 6.039)
2022-10-28 10:45:13.843 DEBUG 1392 --- [           main] cn.itcast.mp.mapper.UserMapper.delete    : ==>  Preparing: DELETE FROM tb_user WHERE name=? AND age=? 
2022-10-28 10:45:13.889 DEBUG 1392 --- [           main] cn.itcast.mp.mapper.UserMapper.delete    : ==> Parameters: 张三(String), 20(Integer)
2022-10-28 10:45:13.896 DEBUG 1392 --- [           main] cn.itcast.mp.mapper.UserMapper.delete    : <==    Updates: 0
result =0
```

### 3.3.4、deleteBatchIds

方法定义：

```
JAVA
/**
* 删除（根据ID 批量删除）
*
* @param idList 主键ID列表(不能为 null 以及 empty)
*/
int deleteBatchIds(@Param(Constants.COLLECTION) Collection<? extends Serializable>
idList);
```

测试用例：

```
BASH
@Test
public void testDeleteByBatchIds(){
    //根据id集合批量删除
    int i = this.userMapper.deleteBatchIds(Arrays.asList(1L, 2L, 3L));
    System.out.println("result ="+i);

}
```

结果：

```
BASH
2022-10-28 10:49:29.675  INFO 1415 --- [           main] c.i.m.ItcastMpSpringbootApplicationTests : Started ItcastMpSpringbootApplicationTests in 3.402 seconds (JVM running for 4.826)
2022-10-28 10:49:29.939 DEBUG 1415 --- [           main] c.i.mp.mapper.UserMapper.deleteBatchIds  : ==>  Preparing: DELETE FROM tb_user WHERE id IN ( ? , ? , ? ) 
2022-10-28 10:49:29.975 DEBUG 1415 --- [           main] c.i.mp.mapper.UserMapper.deleteBatchIds  : ==> Parameters: 1(Long), 2(Long), 3(Long)
2022-10-28 10:49:29.980 DEBUG 1415 --- [           main] c.i.mp.mapper.UserMapper.deleteBatchIds  : <==    Updates: 3
result =3
```

[![image-20221028105100892](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221028105100892.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221028105100892.png)

数据已删除。

## 3.4、查询操作

MP提供了多种查询操作，包括根据id查询、批量查询、查询单条数据、查询列表、分页查询等操作。

### 3.4.1、selectById

方法定义：

```
BASH
/**
* 根据 ID 查询
*
* @param id 主键ID
*/
T selectById(Serializable id);
```

测试用例：

```
JAVA
@Test
    public void testSelectById(){
        //根据id查询数据
        User user = this.userMapper.selectById(4L);
        System.out.println("result"+user);
    }
```

结果：

```
BASH
2022-10-28 11:00:38.546  INFO 1591 --- [           main] c.i.m.ItcastMpSpringbootApplicationTests : Started ItcastMpSpringbootApplicationTests in 3.542 seconds (JVM running for 5.09)
2022-10-28 11:00:38.806 DEBUG 1591 --- [           main] c.i.mp.mapper.UserMapper.selectById      : ==>  Preparing: SELECT id,user_name,name,age,email AS mail FROM tb_user WHERE id=? 
2022-10-28 11:00:38.836 DEBUG 1591 --- [           main] c.i.mp.mapper.UserMapper.selectById      : ==> Parameters: 4(Long)
2022-10-28 11:00:38.863 DEBUG 1591 --- [           main] c.i.mp.mapper.UserMapper.selectById      : <==      Total: 1
resultUser(id=4, userName=zhaoliu, password=null, name=赵六, age=21, mail=test4@itcast.cn, address=null)
```

### 3.4.2、selectBatchIds

方法定义：

```
JAVA
/**
* 查询（根据ID 批量查询）
*
* @param idList 主键ID列表(不能为 null 以及 empty)
*/
List<T> selectBatchIds(@Param(Constants.COLLECTION) Collection<? extends Serializable>
idList);
```

测试用例：

```
JAVA
@Test
public void testSelectByBatchIds(){
    //根据id集合批量查询
    List<User> users = this.userMapper.selectBatchIds(Arrays.asList(4L, 5L, 6L, 7L, 8L));
    for (User user:users){
        System.out.println(user);
    }
}
```

结果：

```
BASH
2022-10-28 11:04:38.814 DEBUG 1607 --- [           main] c.i.mp.mapper.UserMapper.selectBatchIds  : ==>  Preparing: SELECT id,user_name,name,age,email AS mail FROM tb_user WHERE id IN ( ? , ? , ? , ? , ? ) 
2022-10-28 11:04:38.848 DEBUG 1607 --- [           main] c.i.mp.mapper.UserMapper.selectBatchIds  : ==> Parameters: 4(Long), 5(Long), 6(Long), 7(Long), 8(Long)
2022-10-28 11:04:38.875 DEBUG 1607 --- [           main] c.i.mp.mapper.UserMapper.selectBatchIds  : <==      Total: 4
User(id=4, userName=zhaoliu, password=null, name=赵六, age=21, mail=test4@itcast.cn, address=null)
User(id=5, userName=sunqi, password=null, name=孙七, age=24, mail=test5@itcast.cn, address=null)
User(id=7, userName=caocao, password=null, name=曹操1, age=20, mail=test@itcast.cn, address=null)
User(id=8, userName=caocao, password=null, name=曹操2, age=20, mail=test@itcast.cn, address=null)
```

### 3.4.3、selectOne

方法定义：

```
JAVA
/**
* 根据 entity 条件，查询一条记录
*
* @param queryWrapper 实体对象封装操作类（可以为 null）
*/
T selectOne(@Param(Constants.WRAPPER) Wrapper<T> queryWrapper);
```

测试用例：

```
JAVA
    @Test
    public  void testSelectOne(){
        QueryWrapper<User> objectQueryWrapper = new QueryWrapper<>();
        objectQueryWrapper.eq("name","赵六");
//        根据条件查询一条数据，如果超过一条会报错
        User user = this.userMapper.selectOne(objectQueryWrapper);
        System.out.println(user);
    }
```

结果;

```
BASH
2022-10-28 11:11:44.288  INFO 1631 --- [           main] c.i.m.ItcastMpSpringbootApplicationTests : Started ItcastMpSpringbootApplicationTests in 3.242 seconds (JVM running for 4.637)
2022-10-28 11:11:44.616 DEBUG 1631 --- [           main] c.itcast.mp.mapper.UserMapper.selectOne  : ==>  Preparing: SELECT id,user_name,name,age,email AS mail FROM tb_user WHERE name = ? 
2022-10-28 11:11:44.646 DEBUG 1631 --- [           main] c.itcast.mp.mapper.UserMapper.selectOne  : ==> Parameters: 赵六(String)
2022-10-28 11:11:44.677 DEBUG 1631 --- [           main] c.itcast.mp.mapper.UserMapper.selectOne  : <==      Total: 1
User(id=4, userName=zhaoliu, password=null, name=赵六, age=21, mail=test4@itcast.cn, address=null)
```

### 3.4.4、selectCount

方法定义：

```
JAVA
/**
* 根据 Wrapper 条件，查询总记录数
*
* @param queryWrapper 实体对象封装操作类（可以为 null）
*/
Integer selectCount(@Param(Constants.WRAPPER) Wrapper<T> queryWrapper);
```

测试用例：

```
JAVA
@Test
public  void  testSelectByCount(){
    QueryWrapper<User> userQueryWrapper = new QueryWrapper<>();
    userQueryWrapper.gt("age",23);//年龄大于23
    Integer integer = this.userMapper.selectCount(userQueryWrapper);
    System.out.println("count="+ integer);
}
```

结果：

```
BASH
2022-10-28 11:22:52.858  INFO 1668 --- [           main] c.i.m.ItcastMpSpringbootApplicationTests : Started ItcastMpSpringbootApplicationTests in 3.627 seconds (JVM running for 5.165)
2022-10-28 11:22:53.203 DEBUG 1668 --- [           main] c.i.mp.mapper.UserMapper.selectCount     : ==>  Preparing: SELECT COUNT( 1 ) FROM tb_user WHERE age > ? 
2022-10-28 11:22:53.241 DEBUG 1668 --- [           main] c.i.mp.mapper.UserMapper.selectCount     : ==> Parameters: 23(Integer)
2022-10-28 11:22:53.272 DEBUG 1668 --- [           main] c.i.mp.mapper.UserMapper.selectCount     : <==      Total: 1
count=1
```

### 3.4.5、selectList

方法定义：

```
JAVA
/**
* 根据 entity 条件，查询全部记录
*
* @param queryWrapper 实体对象封装操作类（可以为 null）
*/
List<T> selectList(@Param(Constants.WRAPPER) Wrapper<T> queryWrapper);
```

测试用例：

```
JAVA
@Test
   public void testSelectList(){
       QueryWrapper<User> userQueryWrapper = new QueryWrapper<>();
       userQueryWrapper.gt("age",20);

       List<User> users = this.userMapper.selectList(userQueryWrapper);
       for (User user:users){
           System.out.println("user"+ user);
       };
   }
```

结果：

```
JAVA
2022-10-28 11:28:40.742  INFO 1700 --- [           main] c.i.m.ItcastMpSpringbootApplicationTests : Started ItcastMpSpringbootApplicationTests in 3.223 seconds (JVM running for 4.632)
2022-10-28 11:28:41.073 DEBUG 1700 --- [           main] c.i.mp.mapper.UserMapper.selectList      : ==>  Preparing: SELECT id,user_name,name,age,email AS mail FROM tb_user WHERE age > ? 
2022-10-28 11:28:41.107 DEBUG 1700 --- [           main] c.i.mp.mapper.UserMapper.selectList      : ==> Parameters: 20(Integer)
2022-10-28 11:28:41.135 DEBUG 1700 --- [           main] c.i.mp.mapper.UserMapper.selectList      : <==      Total: 2
userUser(id=4, userName=zhaoliu, password=null, name=赵六, age=21, mail=test4@itcast.cn, address=null)
userUser(id=5, userName=sunqi, password=null, name=孙七, age=24, mail=test5@itcast.cn, address=null)
```

### 3.4.6、selectPage

方法定义：

```
JAVA
/**
* 根据 entity 条件，查询全部记录（并翻页）
*
* @param page 分页查询条件（可以为 RowBounds.DEFAULT）
* @param queryWrapper 实体对象封装操作类（可以为 null）
*/
IPage<T> selectPage(IPage<T> page, @Param(Constants.WRAPPER) Wrapper<T> queryWrapper);
```

配置分页插件：

```
JAVA
package cn.itcast.mp.config;

import com.baomidou.mybatisplus.extension.plugins.PaginationInterceptor;
import org.mybatis.spring.annotation.MapperScan;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
@MapperScan("cn.itcast.mp.mapper")
public class MybatisPlusConfig {


    @Bean
    public PaginationInterceptor paginationInterceptor(){
        return  new PaginationInterceptor();
    }
}
```

[![image-20221028114304530](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221028114304530.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221028114304530.png)

测试用例;

```
JAVA
@Test
   public void testSelectPage(){

       QueryWrapper<User> userQueryWrapper = new QueryWrapper<>();
       userQueryWrapper.gt("age",20);

       Page<User> page = new Page<>(1, 1);

       //根据条件查询数据
       IPage<User> userIPage = this.userMapper.selectPage(page, userQueryWrapper);
       System.out.println("数据总条数："+userIPage.getTotal());
       System.out.println("总页数："+userIPage.getPages());

       for (User record : userIPage.getRecords()) {
           System.out.println("user="+record);
       }
   }
```

结果：

```
BASH
2022-10-28 11:41:24.264 DEBUG 1772 --- [           main] c.b.m.e.p.p.o.JsqlParserCountOptimize    : JsqlParserCountOptimize sql=SELECT  id,user_name,name,age,email AS mail  FROM tb_user 
 
 WHERE age > ?
2022-10-28 11:41:24.291 DEBUG 1772 --- [           main] c.i.mp.mapper.UserMapper.selectPage      : ==>  Preparing: SELECT COUNT(1) FROM tb_user WHERE age > ? 
2022-10-28 11:41:24.330 DEBUG 1772 --- [           main] c.i.mp.mapper.UserMapper.selectPage      : ==> Parameters: 20(Integer)
2022-10-28 11:41:24.362 DEBUG 1772 --- [           main] c.i.mp.mapper.UserMapper.selectPage      : ==>  Preparing: SELECT id,user_name,name,age,email AS mail FROM tb_user WHERE age > ? LIMIT ?,? 
2022-10-28 11:41:24.366 DEBUG 1772 --- [           main] c.i.mp.mapper.UserMapper.selectPage      : ==> Parameters: 20(Integer), 0(Long), 1(Long)
2022-10-28 11:41:24.374 DEBUG 1772 --- [           main] c.i.mp.mapper.UserMapper.selectPage      : <==      Total: 1
数据总条数：2
总页数：2
user=User(id=4, userName=zhaoliu, password=null, name=赵六, age=21, mail=test4@itcast.cn, address=null)
```

## 3.5、SQL注入的原理

前面我们已经知道，MP在启动后会将`BaseMapper`中的一系列的方法注册到`meppedStatements`中，那么究竟是如 何注入的呢？流程又是怎么样的？下面我们将一起来分析下。 在MP中，`ISqlInjector`负责`SQL`的注入工作，它是一个接口，`AbstractSqlInjector`是它的实现类，实现关系如下：

`ctrl+h`快速打开继承关系

[![image-20221028120423973](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221028120423973.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221028120423973.png)

在`AbstractSqlInjector`中，主要是由`inspectInject()`方法进行注入的，如下：

```
JAVA
public void inspectInject(MapperBuilderAssistant builderAssistant, Class<?> mapperClass) {
        Class<?> modelClass = this.extractModelClass(mapperClass);
        if (modelClass != null) {
            String className = mapperClass.toString();
            Set<String> mapperRegistryCache = GlobalConfigUtils.getMapperRegistryCache(builderAssistant.getConfiguration());
            if (!mapperRegistryCache.contains(className)) {
                List<AbstractMethod> methodList = this.getMethodList();
                if (CollectionUtils.isNotEmpty(methodList)) {
                    TableInfo tableInfo = TableInfoHelper.initTableInfo(builderAssistant, modelClass);
                  // 循环注入自定义方法
                    methodList.forEach((m) -> {
                        m.inject(builderAssistant, mapperClass, modelClass, tableInfo);
                    });
                } else {
                    logger.debug(mapperClass.toString() + ", No effective injection method was found.");
                }

                mapperRegistryCache.add(className);
            }
        }

    }
```

在实现方法中， `methodList.forEach(m -> m.inject(builderAssistant, mapperClass, modelClass, tableInfo)); `是关键，循环遍历方法，进行注入。

最终调用抽象方法`injectMappedStatement`进行真正的注入：

[![image-20221028120809868](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221028120809868.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221028120809868.png)

以`SelectById`为例查看：

```
JAVA
public class SelectById extends AbstractMethod {
    public SelectById() {
    }

    public MappedStatement injectMappedStatement(Class<?> mapperClass, Class<?> modelClass, TableInfo tableInfo) {
        SqlMethod sqlMethod = SqlMethod.LOGIC_SELECT_BY_ID;
        SqlSource sqlSource = new RawSqlSource(this.configuration, String.format(sqlMethod.getSql(), this.sqlSelectColumns(tableInfo, false), tableInfo.getTableName(), tableInfo.getKeyColumn(), tableInfo.getKeyProperty(), tableInfo.getLogicDeleteSql(true, false)), Object.class);
        return this.addSelectMappedStatement(mapperClass, sqlMethod.getMethod(), sqlSource, modelClass, tableInfo);
    }
}
```

可以看到，生成了`SqlSource`对象，再将`SQL`通过`addSelectMappedStatement`方法添加到`meppedStatements`中。

[![image-20221028182012422](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221028182012422.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221028182012422.png)

# 4、配置

在MP中有大量的配置，其中有一部分是Mybatis原生的配置，另一部分是MP的配置，详情：https://mybatis.plus/c onfig/ 下面我们对常用的配置做讲解。

## 4.1、基本配置

### 4.1.1、configLocation

MyBatis 配置文件位置，如果您有单独的 MyBatis 配置，请将其路径配置到 configLocation 中。 MyBatis Configuration 的具体内容请参考MyBatis 官方文档

Spring Boot：

```
BASH
mybatis-plus.config-location = classpath:mybatis-config.xml
```

Spring MVC：

```
XML
<bean id="sqlSessionFactory"
class="com.baomidou.mybatisplus.extension.spring.MybatisSqlSessionFactoryBean">
<property name="configLocation" value="classpath:mybatis-config.xml"/>
</bean>
```

演示1.在springboot配置文件中引入mybatis-plus配置地址;

```
PROPERTIES
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
    <plugins>
        <plugin interceptor="com.baomidou.mybatisplus.extension.plugins.PaginationInterceptor"></plugin>
    </plugins>
</configuration>
```

[![image-20221028184136424](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221028184136424.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221028184136424.png)

在springboot中添加mybatis-plus配置地址信息

[![image-20221028184623797](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221028184623797.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221028184623797.png)

将之前配置的分页插件注释掉

[![image-20221028184210257](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221028184210257.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221028184210257.png)

检测分页功能

[![image-20221028184255224](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221028184255224.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221028184255224.png)

演示2：spring配置文件中引入mybatis-config文件

[![image-20221028185218725](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221028185218725.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221028185218725.png)

### 4.1.2、mapperLocations

MyBatis Mapper 所对应的 XML 文件位置，如果您在 Mapper 中有自定义方法（XML 中有自定义实现），需要进行 该配置，告诉 Mapper 所对应的 XML 文件位置。

Spring Boot：

```
YAML
mybatis-plus.mapper-locations = classpath*:mybatis/*.xml
```

Spring MVC：

```
PROPERTIES
<bean id="sqlSessionFactory"
class="com.baomidou.mybatisplus.extension.spring.MybatisSqlSessionFactoryBean">
<property name="mapperLocations" value="classpath*:mybatis/*.xml"/>
</bean>
```

Maven 多模块项目的扫描路径需以 `classpath*: `开头 （即加载多个 jar 包下的 XML 文件）

测试：

UserMapper.xml：

```
XML
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
"http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="cn.itcast.mp.mapper.UserMapper">
<select id="findById" resultType="cn.itcast.mp.pojo.User">
select * from tb_user where id = #{id}
</select>
</mapper>
JAVA
package cn.itcast.mp.mapper;

import cn.itcast.mp.pojo.User;
import com.baomidou.mybatisplus.core.mapper.BaseMapper;
import org.apache.ibatis.annotations.Mapper;

import java.util.HashMap;

@Mapper
public interface UserMapper extends BaseMapper<User> {

    User findById(Long id);
}
```

测试用例：

```
JAVA
@Test
public void testSelectByXml(){
    User user = this.userMapper.findById(2L);
    System.out.println(user);
}
BASH
2022-10-29 13:42:49.230  INFO 3115 --- [           main] c.i.m.ItcastMpSpringbootApplicationTests : Started ItcastMpSpringbootApplicationTests in 3.257 seconds (JVM running for 4.729)
2022-10-29 13:42:49.609 DEBUG 3115 --- [           main] cn.itcast.mp.mapper.UserMapper.findById  : ==>  Preparing: select * from tb_user where id = ? 
2022-10-29 13:42:49.648 DEBUG 3115 --- [           main] cn.itcast.mp.mapper.UserMapper.findById  : ==> Parameters: 4(Long)
2022-10-29 13:42:49.672 DEBUG 3115 --- [           main] cn.itcast.mp.mapper.UserMapper.findById  : <==      Total: 1
User(id=4, userName=zhaoliu, password=123456, name=赵六, age=21, mail=null, address=null)
2022-10-29 13:42:49.719  INFO 3115 --- [ionShutdownHook] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown initiated...
2022-10-29 13:42:49.743  INFO 3115 --- [ionShutdownHook] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown completed.
```

### 4.1.3、typeAliasesPackage

MyBaits 别名包扫描路径，通过该属性可以给包中的类注册别名，注册后在 Mapper 对应的 XML 文件中可以直接使 用类名，而不用使用全限定的类名（即 XML 中调用的时候不用包含包名）。

Spring Boot：

```
YAML
mybatis-plus.type-aliases-package = cn.itcast.mp.pojo
```

Spring MVC：

```
YAML
<bean id="sqlSessionFactory"
class="com.baomidou.mybatisplus.extension.spring.MybatisSqlSessionFactoryBean">
<property name="typeAliasesPackage"
value="com.baomidou.mybatisplus.samples.quickstart.entity"/>
</bean>
```

[![image-20221029135138787](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221029135138787.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221029135138787.png)

```
BASH
2022-10-29 13:49:13.408  INFO 3144 --- [           main] c.i.m.ItcastMpSpringbootApplicationTests : Started ItcastMpSpringbootApplicationTests in 3.007 seconds (JVM running for 4.547)
2022-10-29 13:49:13.829 DEBUG 3144 --- [           main] cn.itcast.mp.mapper.UserMapper.findById  : ==>  Preparing: select * from tb_user where id = ? 
2022-10-29 13:49:13.866 DEBUG 3144 --- [           main] cn.itcast.mp.mapper.UserMapper.findById  : ==> Parameters: 4(Long)
2022-10-29 13:49:13.892 DEBUG 3144 --- [           main] cn.itcast.mp.mapper.UserMapper.findById  : <==      Total: 1
User(id=4, userName=zhaoliu, password=123456, name=赵六, age=21, mail=null, address=null)
2022-10-29 13:49:13.938  INFO 3144 --- [ionShutdownHook] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown initiated...
2022-10-29 13:49:13.958  INFO 3144 --- [ionShutdownHook] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown completed.
```

## 4.2、进阶配置

本部分（Configuration）的配置大都为 MyBatis 原生支持的配置，这意味着您可以通过 MyBatis XML 配置文件的形 式进行配置。

### 4.2.1、mapUnderscoreToCamelCase

- 类型： boolean
- 默认值： true

是否开启自动驼峰命名规则（camel case）映射，即从经典数据库列名 A_COLUMN（下划线命名） 到经典 Java 属 性名 aColumn（驼峰命名） 的类似映射。

> 注意： 此属性在 MyBatis 中原默认值为 false，在 MyBatis-Plus 中，此属性也将用于生成最终的 SQL 的 select body 如果您的数据库命名符合规则无需使用 @TableField 注解指定数据库字段名

示例（SpringBoot）：

```
PROPERTIES
#关闭自动驼峰映射，该参数不能和mybatis-plus.config-location同时存在
mybatis-plus.configuration.map-underscore-to-camel-case=false
```

[![image-20221029140044927](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221029140044927.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221029140044927.png)

### 4.2.2、cacheEnabled

- 类型： boolean
- 默认值： true

全局地开启或关闭配置文件中的所有映射器已经配置的任何缓存，默认为 true。

示例：

```
PROPERTIES
mybatis-plus.configuration.cache-enabled=false
```

## 4.3、DB 策略配置

### 4.3.1、idType

- 类型： com.baomidou.mybatisplus.annotation.IdType
- 默认值： ID_WORKER

全局默认主键类型，设置后，即可省略实体对象中的`@TableId(type = IdType.AUTO)`配置。

示例： SpringBoot：

```
PROPERTIES
mybatis-plus.global-config.db-config.id-type=auto
```

SpringMVC：

```
PROPERTIES
<!--这里使用MP提供的sqlSessionFactory，完成了Spring与MP的整合-->
<bean id="sqlSessionFactory"
class="com.baomidou.mybatisplus.extension.spring.MybatisSqlSessionFactoryBean">
	<property name="dataSource" ref="dataSource"/>
	<property name="globalConfig">
		<bean class="com.baomidou.mybatisplus.core.config.GlobalConfig">
				<property name="dbConfig">
						<bean class="com.baomidou.mybatisplus.core.config.GlobalConfig$DbConfig">
								<property name="idType" value="AUTO"/>
						</bean>
				</property>
		</bean>
	</property>
</bean>
```

演示

[![image-20221029144142516](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221029144142516.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221029144142516.png)

### 4.3.2、tablePrefix

- 类型： String
- 默认值： null

表名前缀，全局配置后可省略@TableName()配置。

SpringBoot：

```
PROPERTIES
mybatis-plus.global-config.db-config.table-prefix=tb_
```

SpringMVC：

```
PROPERTIES
<!--这里使用MP提供的sqlSessionFactory，完成了Spring与MP的整合-->
<bean id="sqlSessionFactory"
class="com.baomidou.mybatisplus.extension.spring.MybatisSqlSessionFactoryBean">
	<property name="dataSource" ref="dataSource"/>
	<property name="globalConfig">
		<bean class="com.baomidou.mybatisplus.core.config.GlobalConfig">
				<property name="dbConfig">
						<bean class="com.baomidou.mybatisplus.core.config.GlobalConfig$DbConfig">
								<property name="idType" value="AUTO"/>
								
						</bean>
				</property>
		</bean>
	</property>
</bean>
```

演示：

[![image-20221029150606459](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221029150606459.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221029150606459.png)

# 5、条件构造器

在MP中，Wrapper接口的实现类关系如下：

[![image-20221031121959035](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031121959035.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031121959035.png)

可以看到，AbstractWrapper和AbstractChainWrapper是重点实现，接下来我们重点学习AbstractWrapper以及其 子类。

说明: QueryWrapper(LambdaQueryWrapper) 和 UpdateWrapper(LambdaUpdateWrapper) 的父类 用于生成 sql 的 where 条件, entity 属性也用于生成 sql 的 where 条件 注意: entity 生成的 where 条件与 使用各个 api 生成 的 where 条件没有任何关联行为

## 5.1、allEq

### 5.1.1、说明

```
JAVA
allEq(Map<R, V> params)
allEq(Map<R, V> params, boolean null2IsNull)
allEq(boolean condition, Map<R, V> params, boolean null2IsNull)
```

#### 全部eq(或个别isNull)

个别参数说明:

- `params` : key 为数据库字段名, value 为字段值
- `null2IsNull` : 为 true 则在 map 的 value 为 null 时调用`isNull`方法,为 false 时则`忽略 value 为 null `的

```
JAVA
例1: allEq({id:1,name:"老王",age:null}) ---> id = 1 and name = '老王' and age is null
例2: allEq({id:1,name:"老王",age:null}, false) ---> id = 1 and name = '老王'
```

演示：

[![image-20221031124213548](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031124213548.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031124213548.png)

[![image-20221031124317921](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031124317921.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031124317921.png)

#### 个别参数说明: filter

过滤函数,是否允许字段传入比对条件中 `params `与 `null2IsNull `: 同上

```
JAVA
例1: allEq((k,v) -> k.indexOf("a") > 0, {id:1,name:"老王",age:null}) ---> name = '老王'
and age is null
例2: allEq((k,v) -> k.indexOf("a") > 0, {id:1,name:"老王",age:null}, false) ---> name =
'老王'
```

演示：

[![image-20221031130105531](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031130105531.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031130105531.png)

[![image-20221031130220538](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031130220538.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031130220538.png)

## 5.2、基本比较操作

```
JAVA
eq
	等于 =
ne
	不等于 <>
gt
	大于 >
ge
	大于等于 >=
lt
	小于 <
le
	小于等于 <=
between
	B	ETWEEN 值1 AND 值2
notBetween
	NOT BETWEEN 值1 AND 值2
in
	字段 IN (value.get(0), value.get(1), ...)
notIn
	字段 NOT IN (v0, v1, ...)
```

**演示**

[![image-20221031131021026](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031131021026.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031131021026.png)

## 5.3、模糊查询

```
JAVA
like
		LIKE '%值%'
		例: like("name", "王") ---> name like '%王%'
notLike
		NOT LIKE '%值%'
		例: notLike("name", "王") ---> name not like '%王%'
likeLeft
		LIKE '%值's
		例: likeLeft("name", "王") ---> name like '%王'
likeRight
		LIKE '值%'
		例: likeRight("name", "王") ---> name like '王%'
```

**演示**

[![image-20221031135149453](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031135149453.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031135149453.png)

[![image-20221031135824338](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031135824338.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031135824338.png)

## 5.4、排序

```
JAVA
orderBy
		排序：ORDER BY 字段, ...
		例: orderBy(true, true, "id", "name") ---> order by id ASC,name ASC
orderByAsc
		排序：ORDER BY 字段, ... ASC
		例: orderByAsc("id", "name") ---> order by id ASC,name ASC
orderByDesc
		排序：ORDER BY 字段, ... DESC
		例: orderByDesc("id", "name") ---> order by id DESC,name DESC
```

[![image-20221031140819993](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031140819993.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031140819993.png)

[![image-20221031141233451](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031141233451.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031141233451.png)

## 5.5、逻辑查询

```
JAVA
or
		拼接 OR
    主动调用 or 表示紧接着下一个方法不是用 and 连接!(不调用 or 则默认为使用 and 连接)
and
		AND 嵌套
		例: and(i -> i.eq("name", "李白").ne("status", "活着")) ---> and (name = '李白' and status <> '活着')
```

演示：

[![image-20221031141838014](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031141838014.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031141838014.png)

## 5.6、select

在MP查询中，默认查询所有的字段，如果有需要也可以通过`select`方法进行指定字段。

演示

[![image-20221031153051092](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031153051092.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031153051092.png)

# 6、 ActiveRecord

ActiveRecord（简称AR）一直广受动态语言（ PHP 、 Ruby 等）的喜爱，而 Java 作为准静态语言，对于 ActiveRecord 往往只能感叹其优雅，所以我们也在 AR 道路上进行了一定的探索，喜欢大家能够喜欢。

什么是ActiveRecord？

ActiveRecord也属于ORM（对象关系映射）层，由Rails最早提出，遵循标准的ORM模型：表映射到记录，记 录映射到对象，字段映射到对象属性。配合遵循的命名和配置惯例，能够很大程度的快速实现模型的操作，而 且简洁易懂。

`ActiveRecord`的主要思想是：

- 每一个数据库表对应创建一个类，类的每一个对象实例对应于数据库中表的一行记录；通常表的每个字段 在类中都有相应的Field；
- ActiveRecord同时负责把自己持久化，在ActiveRecord中封装了对数据库的访问，即CURD;
- ActiveRecord是一种领域模型(Domain Model)，封装了部分业务逻辑；

## 6.1、开启AR之旅

在MP中，开启AR非常简单，只需要将实体对象继承`Model`即可。

```
JAVA
package cn.itcast.mp.pojo;

import com.baomidou.mybatisplus.annotation.IdType;
import com.baomidou.mybatisplus.annotation.TableField;
import com.baomidou.mybatisplus.annotation.TableId;
import com.baomidou.mybatisplus.annotation.TableName;
import com.baomidou.mybatisplus.extension.activerecord.Model;
import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;
@Data
@NoArgsConstructor
@AllArgsConstructor
//@TableName("tb_user")
public class User extends Model<User> {
//    @TableId(type= IdType.AUTO) //指定id类型为自增长
    private Long id;
    private String userName;
    @TableField(select = false)
    private String password;
    private String name;
    private Integer age;
    @TableField(value = "email")//解决字段名不一致
    private String mail;
    @TableField(exist = false )
    private String address;//该字段在数据库表中不存在
}
```

## 6.2、根据主键查询

```
JAVA
@Test
 public void testAR(){
     User user = new User();
     user.setId(4L);
     User user1 = user.selectById();
     System.out.println(user1);
 }
```

[![image-20221031155306066](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031155306066.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031155306066.png)

## 6.3、新增数据

```
JAVA
@Test
   public void testARInster(){
       User user = new User();
       user.setUserName("刘备");
       user.setAge(30);
       user.setPassword("1234");
       user.setMail("liubei@qq.com");
       boolean insert = user.insert();
       System.out.println(insert);
   }
```

[![image-20221031160710800](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031160710800.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031160710800.png)

[![image-20221031160805990](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031160805990.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031160805990.png)

## 6.5、更新操作

```
JAVA
@Test
public void testARUpdate(){
  User user = new User();
  user.setId(10L);
  user.setName("999");
  boolean b = user.updateById();
  System.out.println(b);
}
```

[![image-20221031161124086](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031161124086.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031161124086.png)

[![image-20221031161151596](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031161151596.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031161151596.png)

## 6.6、删除操作

```
JAVA
@Test
public void testARDelete() {
    User user = new User();
    user.setId(10L);
    boolean b = user.deleteById(user);
    System.out.println(b);
}
```

[![image-20221031161347813](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031161347813.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031161347813.png)

## 6.7、根据条件查询

```
JAVA
@Test
  public void testARQuery(){
      User user = new User();
      QueryWrapper<User> objectQueryWrapper = new QueryWrapper<>();
      objectQueryWrapper.le("age",20);

      List<User> users = user.selectList(objectQueryWrapper);
      users.forEach(user1 -> System.out.println(user1));
  }
```

[![image-20221031163524827](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031163524827.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031163524827.png)

# 7、 Oracle 主键Sequence

在mysql中，主键往往是自增长的，这样使用起来是比较方便的，如果使用的是Oracle数据库，那么就不能使用自增 长了，就得使用Sequence 序列生成id值了。

## 7.1、部署Oracle环境

为了简化环境部署，这里使用`Docker`环境进行部署安装`Oracle`。

```
BASH
#拉取镜像
docker pull sath89/oracle-12c
#创建容器
docker create --name oracle -p 1521:1521 sath89/oracle-12c
#启动
docker start oracle && docker logs -f oracle
#下面是启动过程
Database not initialized. Initializing database.
Starting tnslsnr
Copying database files
1% complete
3% complete
11% complete
18% complete
26% complete
37% complete
Creating and starting Oracle instance
40% complete
45% complete
50% complete
55% complete
56% complete
60% complete
62% complete
Completing Database Creation
66% complete
70% complete
73% complete
85% complete
96% complete
100% complete
Look at the log file "/u01/app/oracle/cfgtoollogs/dbca/xe/xe.log" for further details.
Configuring Apex console
Database initialized. Please visit http://#containeer:8080/em
http://#containeer:8080/apex for extra configuration if needed
Starting web management console
PL/SQL procedure successfully completed.
Starting import from '/docker-entrypoint-initdb.d':
ls: cannot access /docker-entrypoint-initdb.d/*: No such file or directory
Import finished
Database ready to use. Enjoy! ;)
#通过用户名密码即可登录
用户名和密码为： system/oracle
```

下面使用navicat12进行连接并操作oracle，使用资料中提供的安装包，可以试用14天。

需要注意的是：由于安装的Oracle是64位版本，所以navicat也是需要使用64为版本，否则连接不成功。

[![image-20221031164832681](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031164832681.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031164832681.png)

连接成功：

[![image-20221031164901839](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031164901839.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031164901839.png)

## 7.2、创建表以及序列

```
SQL
--创建表，表名以及字段名都要大写
CREATE TABLE "TB_USER" (
"ID" NUMBER(20) VISIBLE NOT NULL ,
"USER_NAME" VARCHAR2(255 BYTE) VISIBLE ,
"PASSWORD" VARCHAR2(255 BYTE) VISIBLE ,
"NAME" VARCHAR2(255 BYTE) VISIBLE ,
"AGE" NUMBER(10) VISIBLE ,
"EMAIL" VARCHAR2(255 BYTE) VISIBLE
)
--创建序列
CREATE SEQUENCE SEQ_USER START WITH 1 INCREMENT BY 1
```

## 7.3、jdbc驱动包

由于版权原因，我们不能直接通过maven的中央仓库下载oracle数据库的jdbc驱动包，所以我们需要将驱动包安装到 本地仓库。

```
BASH
#ojdbc8.jar文件在资料中可以找到
mvn install:install-file -DgroupId=com.oracle -DartifactId=ojdbc8 -Dversion=12.1.0.1 -
Dpackaging=jar -Dfile=ojdbc8.jar
```

安装完成后的坐标：

```
XML
<dependency>
  <groupId>com.oracle</groupId>
  <artifactId>ojdbc8</artifactId>
  <version>12.1.0.1</version>
</dependency>
```

## 7.4、修改application.properties

对于application.properties的修改，需要修改2个位置，分别是：

```
PROPERTIES
#数据库连接配置
spring.datasource.driver-class-name=oracle.jdbc.OracleDriver
spring.datasource.url=jdbc:oracle:thin:@192.168.31.81:1521:xe
spring.datasource.username=system
spring.datasource.password=oracle
#id生成策略
mybatis-plus.global-config.db-config.id-type=input
```

## 7.5、配置序列

使用Oracle的序列需要做2件事情：

第一，需要配置MP的序列生成器到Spring容器：

```
JAVA
package cn.itcast.mp;
import com.baomidou.mybatisplus.extension.incrementer.OracleKeyGenerator;
import com.baomidou.mybatisplus.extension.plugins.PaginationInterceptor;
import org.mybatis.spring.annotation.MapperScan;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
@Configuration
@MapperScan("cn.itcast.mp.mapper") //设置mapper接口的扫描包
public class MybatisPlusConfig {
  /**
  * 分页插件
  */
  @Bean
  public PaginationInterceptor paginationInterceptor() {
  return new PaginationInterceptor();
  }
  /**
  * 序列生成器
  */
  @Bean
  public OracleKeyGenerator oracleKeyGenerator(){
  return new OracleKeyGenerator();
    }
}
```

第二，在实体对象中指定序列的名称：

```
JAVA
@KeySequence(value = "SEQ_USER", clazz = Long.class)
public class User{
......
}
```

2.7、测试

```
JAVA
package cn.itcast.mp;
import cn.itcast.mp.mapper.UserMapper;
import cn.itcast.mp.pojo.User;
import org.junit.Test;
import org.junit.runner.RunWith;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.test.context.junit4.SpringRunner;
import java.util.List;
@RunWith(SpringRunner.class)
@SpringBootTest
public class UserMapperTest {
@Autowired
	private UserMapper userMapper;
	@Test
 public void testInsert(){
  User user = new User();
  user.setAge(20);
  user.setEmail("test@itcast.cn");
  user.setName("曹操");
  user.setUserName("caocao");
  user.setPassword("123456");
  int result = this.userMapper.insert(user); //返回的result是受影响的行数，并不是自增后的id
  System.out.println("result = " + result);
  System.out.println(user.getId()); //自增后的id会回填到对象中
  }
  
  @Test
  public void testSelectById(){
    User user = this.userMapper.selectById(8L);
    System.out.println(user);
  }
}
```

[![image-20221031165648820](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031165648820.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031165648820.png)

# 8、插件

## 3.1、mybatis的插件机制

MyBatis 允许你在已映射语句执行过程中的某一点进行拦截调用。默认情况下，MyBatis 允许使用插件来拦截的方法 调用包括：

1. Executor (update, query, flushStatements, commit, rollback, getTransaction, close, isClosed)
2. ParameterHandler (getParameterObject, setParameters)
3. ResultSetHandler (handleResultSets, handleOutputParameters)
4. StatementHandler (prepare, parameterize, batch, update, query)

我们看到了可以拦截Executor接口的部分方法，比如update，query，commit，rollback等方法，还有其他接口的 一些方法等。

总体概括为：

1. 拦截执行器的方法
2. 拦截参数的处理
3. 拦截结果集的处理
4. 拦截Sql语法构建的处理

拦截器示例：

```
JAVA
package cn.itcast.mp.plugins;

import org.apache.ibatis.executor.Executor;
import org.apache.ibatis.mapping.MappedStatement;
import org.apache.ibatis.plugin.*;

import java.util.Properties;



@Intercepts({@Signature(
        type= Executor.class,
        method = "update",
        args = {MappedStatement.class,Object.class})})
public class MyInterceptor implements Interceptor {
    @Override
    public Object intercept(Invocation invocation) throws Throwable {
        //拦截方法，具体业务逻辑编写的位置
        return invocation.proceed();
    }

    @Override
    public Object plugin(Object target) {
        //创建target对象的代理对象,目的是将当前拦截器加入到该对象中
        return Plugin.wrap(target, this);
    }

    @Override
    public void setProperties(Properties properties) {
        //属性设置
    }
}
```

注入到Spring容器：

```
JAVA
/**
* 自定义拦截器
*/
@Bean
public MyInterceptor myInterceptor(){
	return new MyInterceptor();
}
```

或者通过`xml`配置，`mybatis-config.xml`：

```
XML
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
"http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
<plugins>
<plugin interceptor="cn.itcast.mp.plugins.MyInterceptor"></plugin>
</plugins>
</configuration>
```

**演示**

[![image-20221031194748030](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031194748030.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031194748030.png)

## 3.2、执行分析插件

在MP中提供了对SQL执行的分析的插件，可用作阻断全表更新、删除的操作，注意：该插件仅适用于开发环境，不 适用于生产环境。 SpringBoot配置：

```
JAVA
@Bean
public SqlExplainInterceptor sqlExplainInterceptor(){
  SqlExplainInterceptor sqlExplainInterceptor = new SqlExplainInterceptor();
  List<ISqlParser> sqlParserList = new ArrayList<>();
  // 攻击 SQL 阻断解析器、加入解析链
  sqlParserList.add(new BlockAttackSqlParser());
  sqlExplainInterceptor.setSqlParserList(sqlParserList);
  return sqlExplainInterceptor;
}
```

测试：

```
JAVA
@Test
public void testUpdate(){
    User user = new User();
    user.setAge(20);
    int result = this.userMapper.update(user, null);
    System.out.println("result = " + result);
}
```

[![image-20221031195715922](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031195715922.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031195715922.png)

## 3.3、性能分析插件

性能分析拦截器，用于输出每条 SQL 语句及其执行时间，可以设置最大执行时间，超过时间会抛出异常。

该插件只用于开发环境，不建议生产环境使用。

```
XML
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
    <plugins>
        <plugin interceptor="com.baomidou.mybatisplus.extension.plugins.PaginationInterceptor"></plugin>
        <!-- SQL 执行性能分析，开发环境使用，线上不推荐。 maxTime 指的是 sql 最大执行时长 -->
        <plugin interceptor="com.baomidou.mybatisplus.extension.plugins.PerformanceInterceptor">
            <property name="maxTime" value="100" />
            <!--SQL是否格式化 默认false-->
            <property name="format" value="true" />
        </plugin>
    </plugins>
</configuration>
```

[![image-20221031204132228](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031204132228.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031204132228.png)

可以看到，执行时间为11ms。如果将maxTime设置为1，那么，该操作会抛出异常。

[![image-20221031204527580](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031204527580.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031204527580.png)

## 3.4、乐观锁插件

### 3.4.1、主要适用场景

意图： 当要更新一条记录的时候，希望这条记录没有被别人更新

乐观锁实现方式：

- 取出记录时，获取当前`version`
- 更新时，带上这个`version`
- 执行更新时， `set version = newVersion where version = oldVersion`
- 如果`version`不对，就更新失败

### 3.4.2、插件配置

方式1、spring xml:

```
XML
<bean class="com.baomidou.mybatisplus.extension.plugins.OptimisticLockerInterceptor"/>
```

方式2、spring boot:

```
JAVA
@Bean
public OptimisticLockerInterceptor optimisticLockerInterceptor() {
	return new OptimisticLockerInterceptor();
}
```

### 3.4.3、注解实体字段

需要为实体字段添加@Version注解。

第一步，为表添加version字段，并且设置初始值为1：

```
SQL
ALTER TABLE `tb_user`
ADD COLUMN `version` int(10) NULL AFTER `email`;
UPDATE `tb_user` SET `version`='1';
```

[![image-20221031205743138](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031205743138.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031205743138.png)

第二步，为User实体对象添加version字段，并且添加@Version注解：

```
JAVA
@Version
private Integer version;
```

3.4.4、测试

测试用例;

```
JAVA
@Test
public void testUpdateByVersion2(){
    User user = new User();
    user.setId(7L);
    User user1 = this.userMapper.selectById(user);
    user1.setName("威少");
    int i = this.userMapper.updateById(user1);
    System.out.println(i);

}
```

[![image-20221031211518043](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221031211518043.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221031211518043.png)

可以看到，更新的条件中有`version`条件，并且更新的`version`为2。 如果再次执行，更新则不成功。这样就避免了多人同时更新时导致数据的不一致。

### 3.4.5、特别说明

- **支持的数据类型只有**:int,Integer,long,Long,Date,Timestamp,LocalDateTime
- 整数类型下 newVersion = oldVersion + 1
- newVersion 会回写到 entity 中
- 仅支持 updateById(id) 与 update(entity, wrapper) 方法
- 在 update(entity, wrapper) 方法下, wrapper 不能复用!!!

# 9、Sql 注入器

我们已经知道，在MP中，通过AbstractSqlInjector将BaseMapper中的方法注入到了Mybatis容器，这样这些方法才 可以正常执行。 那么，如果我们需要扩充BaseMapper中的方法，又该如何实现呢？ 下面我们以扩展findAll方法为例进行学习。

## 9.1、编写MyBaseMapper

```
JAVA
package cn.itcast.mp.mapper;

import com.baomidou.mybatisplus.core.mapper.BaseMapper;

import java.util.List;

public interface MybaseMapper<T> extends BaseMapper<T> {
    List<T> findAll();

}
```

其他的Mapper都可以继承该Mapper，这样实现了统一的扩展。

```
JAVA
package cn.itcast.mp.mapper;

import cn.itcast.mp.pojo.User;
import com.baomidou.mybatisplus.core.mapper.BaseMapper;
import org.apache.ibatis.annotations.Mapper;

import java.util.HashMap;

@Mapper
public interface UserMapper extends MybaseMapper<User> {
    User findById(Long id);
}
```

## 9.2、编写MySqlInjector

如果直接继承AbstractSqlInjector的话，原有的BaseMapper中的方法将失效，所以我们选择继承DefaultSqlInjector 进行扩展。

```
JAVA
package cn.itcast.mp.sqlInjector;

import com.baomidou.mybatisplus.core.injector.AbstractMethod;
import com.baomidou.mybatisplus.core.injector.DefaultSqlInjector;

import java.util.List;

public class MySqlInjector extends DefaultSqlInjector {

    @Override
    public List<AbstractMethod> getMethodList() {
        List<AbstractMethod> methodList = super.getMethodList();
        methodList.add(new FindAll());
        return methodList;
    }

}
```

## 9.3、编写FindAll

```
JAVA
package cn.itcast.mp.sqlInjector;

import com.baomidou.mybatisplus.core.injector.AbstractMethod;
import com.baomidou.mybatisplus.core.metadata.TableInfo;
import org.apache.ibatis.mapping.MappedStatement;
import org.apache.ibatis.mapping.SqlSource;


public class FindAll extends AbstractMethod {

    @Override
    public MappedStatement injectMappedStatement(Class<?> mapperClass, Class<?> modelClass, TableInfo tableInfo) {
        String sqlMethod = "findAll";
        String sql = "select * from " + tableInfo.getTableName();
        SqlSource sqlSource = languageDriver.createSqlSource(configuration, sql, modelClass);
        return this.addSelectMappedStatement(mapperClass, sqlMethod, sqlSource,modelClass, tableInfo);

    }
}
```

## 9.4、注册到Spring容器

```
JAVA
/**
 * 自定义SQL注入器
 */
@Bean
public MySqlInjector mySqlInjector(){
    return new MySqlInjector();
}
```

## 9.5、测试

```
JAVA
@Test
 public void testFindAll(){
     List<User> all = this.userMapper.findAll();
     all.forEach(user -> System.out.println(user));
 }
```

[![image-20221101110931990](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221101110931990.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221101110931990.png)

至此，我们实现了全局扩展SQL注入器。

# 10、自动填充功能

有些时候我们可能会有这样的需求，插入或者更新数据时，希望有些字段可以自动填充数据，比如密码、version 等。在MP中提供了这样的功能，可以实现自动填充。

## 10.1、添加`@TableField`注解

```
JAVA
@TableField(fill = FieldFill.INSERT) //插入数据时进行填充
private String password;
```

为`password`添加自动填充功能，在新增数据时有效。 FieldFill提供了多种模式选择：

```
JAVA
public enum FieldFill {
/**
* 默认不处理
*/
DEFAULT,
/**
* 插入时填充字段
*/
INSERT,
/**
* 更新时填充字段
*/
UPDATE,
/**
* 插入和更新时填充字段
*/
INSERT_UPDATE
}
```

## 10.2、编写MyMetaObjectHandler

```
JAVA
package cn.itcast.mp.handler;

import com.baomidou.mybatisplus.core.handlers.MetaObjectHandler;
import org.apache.ibatis.reflection.MetaObject;
import org.springframework.stereotype.Component;


@Component
public class MyMetaObjectHandler implements MetaObjectHandler {
    /**
     * 插入式进行填充
     * @param metaObject
     */
    @Override
    public void insertFill(MetaObject metaObject) {
        Object password = getFieldValByName("password", metaObject);
        if (null==password){
            setFieldValByName("password","123456",metaObject);
        }
    }

    @Override
    public void updateFill(MetaObject metaObject) {

    }
}
```

## 10.3、测试

```
JAVA
@Test
public void testInsert(){
    User user = new User();
    user.setName("关羽");
    user.setUserName("guanyu");
    user.setAge(30);
    user.setMail("guanyu@itast.cn");
    user.setVersion(1);
    int result = this.userMapper.insert(user);
    System.out.println("result = " + result);
}

 @Test
public void testInsert(){
    User user = new User();
    user.setName("诸葛亮");
    user.setUserName("zhugeliang");
    user.setAge(21);
    user.setMail("guanyu@itast.cn");
    user.setVersion(1);
    user.setPassword("88877000");
    int result = this.userMapper.insert(user);
    System.out.println("result = " + result);
}
```

[![image-20221101114020878](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221101114020878.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221101114020878.png)

[![image-20221101114146430](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221101114146430.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221101114146430.png)

[![image-20221101120626037](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221101120626037.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221101120626037.png)

# 11、 逻辑删除

开发系统时，有时候在实现功能时，删除操作需要实现逻辑删除，所谓逻辑删除就是将数据标记为删除，而并非真正 的物理删除（非DELETE操作），查询时需要携带状态条件，确保被标记的数据不被查询到。这样做的目的就是避免 数据被真正的删除。

## 11.1、修改表结构

为`tb_user`表增加`deleted`字段，用于表示数据是否被删除，1代表删除，0代表未删除。

```
SQL
ALTER TABLE `tb_user`
ADD COLUMN `deleted` int(1) NULL DEFAULT 0 COMMENT '1代表删除，0代表未删除' AFTER
`version`;
```

同时，也修改User实体，增加deleted属性并且添加`@TableLogic`注解：

```
JAVA
@TableLogic
private Integer deleted;
```

## 6.2、配置

application.properties：

```
PROPERTIES
# 逻辑已删除值(默认为 1)
mybatis-plus.global-config.db-config.logic-delete-value=1
# 逻辑未删除值(默认为 0)
mybatis-plus.global-config.db-config.logic-not-delete-value=0
```

## 6.3、测试

```
JAVA
@Test
public void testDeleteByIdLogic(){
    this.userMapper.deleteById(4L);
}
```

执行的sql：

```
PLAINTEXT
2022-11-01 15:44:46.718 DEBUG 8030 --- [           main] c.i.mp.mapper.UserMapper.deleteById      : ==>  Preparing: UPDATE tb_user SET deleted=1 WHERE id=? AND deleted=0 
2022-11-01 15:44:46.760 DEBUG 8030 --- [           main] c.i.mp.mapper.UserMapper.deleteById      : ==> Parameters: 4(Long)
2022-11-01 15:44:46.767 DEBUG 8030 --- [           main] c.i.mp.mapper.UserMapper.deleteById      : <==    Updates: 1
```

[![image-20221101154618822](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221101154618822.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221101154618822.png)

测试查询：

```
BASH
2022-11-01 15:47:12.683 DEBUG 8043 --- [           main] c.i.mp.mapper.UserMapper.selectById      : ==>  Preparing: SELECT id,user_name,name,age,email AS mail,version,deleted FROM tb_user WHERE id=? AND deleted=0 
2022-11-01 15:47:12.727 DEBUG 8043 --- [           main] c.i.mp.mapper.UserMapper.selectById      : ==> Parameters: 4(Long)
2022-11-01 15:47:12.749 DEBUG 8043 --- [           main] c.i.mp.mapper.UserMapper.selectById      : <==      Total: 0
```

可见，已经实现了逻辑删除。

# 12、 通用枚举

解决了繁琐的配置，让 mybatis 优雅的使用枚举属性！

## 12.1、修改表结构

```
SQL
ALTER TABLE `tb_user`
ADD COLUMN `sex` int(1) NULL DEFAULT 1 COMMENT '1-男，2-女' AFTER `deleted`;
```

## 12.2、定义枚举

```
JAVA
package cn.itcast.mp.enums;

import com.baomidou.mybatisplus.core.enums.IEnum;

public enum SexEnum implements IEnum<Integer> {
    MAN(1,"男"),
    WOMAN(2,"女");

    private int value;
    private String desc;

    SexEnum(int value, String desc) {
        this.value=value;
        this.desc=desc;
    }

    @Override
    public Integer getValue() {
        return this.value;
    }

    @Override
    public String toString() {
        return this.desc;
    }
}
```

## 12.3、配置

```java
JAVA
# 枚举包扫描
mybatis-plus.type-enums-package=cn.itcast.mp.enums
```

## 12.4、修改实体

```java
JAVA
private SexEnum sex;
```

## 12.5、测试

测试插入数据：

```java
JAVA
@Test
  public void testInsertEnums(){
      User user = new User();
      user.setName("貂蝉");
      user.setUserName("diaochan");
      user.setAge(20);
      user.setMail("diaochan@itast.cn");
      user.setVersion(1);
      user.setSex(SexEnum.WOMAN);
      int result = this.userMapper.insert(user);
      System.out.println("result = " + result);
  }
BASH
2022-11-01 16:13:39.695 DEBUG 8599 --- [           main] c.b.m.e.parsers.BlockAttackSqlParser     : parser sql: INSERT INTO tb_user (user_name, password, name, age, email, version, sex) VALUES (?, ?, ?, ?, ?, ?, ?)
2022-11-01 16:13:39.704 DEBUG 8599 --- [           main] cn.itcast.mp.mapper.UserMapper.insert    : ==>  Preparing: INSERT INTO tb_user ( user_name, password, name, age, email, version, sex ) VALUES ( ?, ?, ?, ?, ?, ?, ? ) 
2022-11-01 16:13:39.741 DEBUG 8599 --- [           main] cn.itcast.mp.mapper.UserMapper.insert    : ==> Parameters: diaochan(String), 123456(String), 貂蝉(String), 20(Integer), diaochan@itast.cn(String), 1(Integer), 2(Integer)
2022-11-01 16:13:39.747 DEBUG 8599 --- [           main] cn.itcast.mp.mapper.UserMapper.insert    : <==    Updates: 1
```

[![image-20221101162947312](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221101162947312.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221101162947312.png)

查询

```java
JAVA
@Test
 public void testSelectByIdEnum(){
     User user = this.userMapper.selectById(15L);
     System.out.println(user);
 }
BASH
2022-11-01 16:30:38.311 DEBUG 8922 --- [           main] c.i.mp.mapper.UserMapper.selectById      : ==>  Preparing: SELECT id,user_name,name,age,email AS mail,version,deleted,sex FROM tb_user WHERE id=? AND deleted=0 
2022-11-01 16:30:38.356 DEBUG 8922 --- [           main] c.i.mp.mapper.UserMapper.selectById      : ==> Parameters: 15(Long)
2022-11-01 16:30:38.383 DEBUG 8922 --- [           main] c.i.mp.mapper.UserMapper.selectById      : <==      Total: 1
User(id=15, userName=diaochan, password=null, name=貂蝉, age=20, mail=diaochan@itast.cn, address=null, version=1, deleted=0, sex=女)
```

从测试可以看出，可以很方便的使用枚举了。 查询条件时也是有效的：

```java
JAVA
@Test
 public  void testSelectBySex(){
     QueryWrapper<User> objectQueryWrapper = new QueryWrapper<>();
     objectQueryWrapper.eq("sex",SexEnum.MAN);
     List<User> users = this.userMapper.selectList(objectQueryWrapper);
     users.forEach(user -> System.out.println(user));
 }
BASH
2022-11-01 16:34:13.534 DEBUG 8938 --- [           main] c.i.mp.mapper.UserMapper.selectList      : ==>  Preparing: SELECT id,user_name,name,age,email AS mail,version,deleted,sex FROM tb_user WHERE deleted=0 AND sex = ? 
2022-11-01 16:34:13.572 DEBUG 8938 --- [           main] c.i.mp.mapper.UserMapper.selectList      : ==> Parameters: 1(Integer)
2022-11-01 16:34:13.601 DEBUG 8938 --- [           main] c.i.mp.mapper.UserMapper.selectList      : <==      Total: 8
User(id=5, userName=sunqi, password=null, name=威少, age=24, mail=test5@itcast.cn, address=null, version=2, deleted=0, sex=男)
User(id=7, userName=caocao, password=null, name=威少, age=20, mail=test@itcast.cn, address=null, version=2, deleted=0, sex=男)
User(id=8, userName=caocao, password=null, name=曹操2, age=20, mail=test@itcast.cn, address=null, version=1, deleted=0, sex=男)
User(id=9, userName=caocao, password=null, name=曹操2, age=20, mail=test@itcast.cn, address=null, version=1, deleted=0, sex=男)
User(id=11, userName=caocao, password=null, name=曹操2, age=20, mail=test@itcast.cn, address=null, version=1, deleted=0, sex=男)
User(id=12, userName=caocao, password=null, name=曹操2, age=20, mail=test@itcast.cn, address=null, version=1, deleted=0, sex=男)
User(id=13, userName=guanyu, password=null, name=关羽, age=30, mail=guanyu@itast.cn, address=null, version=1, deleted=0, sex=男)
User(id=14, userName=zhugeliang, password=null, name=诸葛亮, age=21, mail=guanyu@itast.cn, address=null, version=1, deleted=0, sex=男)
```

# 13、代码生成器

AutoGenerator 是 MyBatis-Plus 的代码生成器，通过 AutoGenerator 可以快速生成 Entity、Mapper、Mapper XML、Service、Controller 等各个模块的代码，极大的提升了开发效率。

## 13.1、创建工程

```xml
XML
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.1.4.RELEASE</version>
    </parent>

    <groupId>org.example</groupId>
    <artifactId>mybatis-plus-sample-generator</artifactId>
    <version>1.0-SNAPSHOT</version>

    <properties>
        <maven.compiler.source>8</maven.compiler.source>
        <maven.compiler.target>8</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
        <!--mybatis-plus的springboot支持-->
        <dependency>
            <groupId>com.baomidou</groupId>
            <artifactId>mybatis-plus-boot-starter</artifactId>
            <version>3.1.1</version>
        </dependency>
        <dependency>
            <groupId>com.baomidou</groupId>
            <artifactId>mybatis-plus-generator</artifactId>
            <version>3.1.1</version>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-freemarker</artifactId>
        </dependency>
        <!--mysql驱动-->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>5.1.47</version>
        </dependency>
        <dependency>
            <groupId>org.slf4j</groupId>
            <artifactId>slf4j-log4j12</artifactId>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>

</project>
```

## 13.2、代码

```java
JAVA
package org.example.generator;


/**
 * <p>
 * mysql 代码生成器演示例子
 * </p>
 */


import com.baomidou.mybatisplus.core.exceptions.MybatisPlusException;
import com.baomidou.mybatisplus.core.toolkit.StringPool;
import com.baomidou.mybatisplus.core.toolkit.StringUtils;
import com.baomidou.mybatisplus.generator.AutoGenerator;
import com.baomidou.mybatisplus.generator.InjectionConfig;
import com.baomidou.mybatisplus.generator.config.*;
import com.baomidou.mybatisplus.generator.config.po.TableInfo;
import com.baomidou.mybatisplus.generator.config.rules.NamingStrategy;
import com.baomidou.mybatisplus.generator.engine.FreemarkerTemplateEngine;

import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

/**
 * <p>
 * mysql 代码生成器演示例子
 * </p>
 */
public class MysqlGenerator {

    /**
     * <p>
     * 读取控制台内容
     * </p>
     */
    public static String scanner(String tip) {
        Scanner scanner = new Scanner(System.in);
        StringBuilder help = new StringBuilder();
        help.append("请输入" + tip + "：");
        System.out.println(help.toString());
        if (scanner.hasNext()) {
            String ipt = scanner.next();
            if (StringUtils.isNotEmpty(ipt)) {
                return ipt;
            }
        }
        throw new MybatisPlusException("请输入正确的" + tip + "！");
    }

    /**
     * RUN THIS
     */
    public static void main(String[] args) {
// 代码生成器
        AutoGenerator mpg = new AutoGenerator();
// 全局配置
        GlobalConfig gc = new GlobalConfig();
        String projectPath = System.getProperty("user.dir");
        gc.setOutputDir(projectPath + "/src/main/java");
        gc.setAuthor("itcast");
        gc.setOpen(false);
        mpg.setGlobalConfig(gc);
// 数据源配置
        DataSourceConfig dsc = new DataSourceConfig();
        dsc.setUrl("jdbc:mysql://127.0.0.1:3306/mp? useUnicode=true&useSSL=false&characterEncoding=utf8");
// dsc.setSchemaName("public");
                dsc.setDriverName("com.mysql.jdbc.Driver");
        dsc.setUsername("root");
        dsc.setPassword("Xuwei19941214~");
        mpg.setDataSource(dsc);
// 包配置
        PackageConfig pc = new PackageConfig();
        pc.setModuleName(scanner("模块名"));
        pc.setParent("org.example.generator");
        mpg.setPackageInfo(pc);
        // 自定义配置
        InjectionConfig cfg = new InjectionConfig() {
            @Override
            public void initMap() {
        // to do nothing
            }
        };
        List<FileOutConfig> focList = new ArrayList<>();
        focList.add(new FileOutConfig("/templates/mapper.xml.ftl") {
            @Override
            public String outputFile(TableInfo tableInfo) {
        // 自定义输入文件名称
                return projectPath + "/src/main/resources/mapper/" + pc.getModuleName()+ "/" + tableInfo.getEntityName() + "Mapper" +
                        StringPool.DOT_XML;
            }
        });
        cfg.setFileOutConfigList(focList);
        mpg.setCfg(cfg);
        mpg.setTemplate(new TemplateConfig().setXml(null));
        // 策略配置
        StrategyConfig strategy = new StrategyConfig();
        strategy.setNaming(NamingStrategy.underline_to_camel);
        strategy.setColumnNaming(NamingStrategy.underline_to_camel);
        //
        strategy.setSuperEntityClass("com.baomidou.mybatisplus.samples.generator.common.BaseEntity");
                strategy.setEntityLombokModel(true);
        //
        strategy.setSuperControllerClass("com.baomidou.mybatisplus.samples.generator.common.BaseController");
                strategy.setInclude(scanner("表名"));
        strategy.setSuperEntityColumns("id");
        strategy.setControllerMappingHyphenStyle(true);
        strategy.setTablePrefix(pc.getModuleName() + "_");
        mpg.setStrategy(strategy);
        // 选择 freemarker 引擎需要指定如下加，注意 pom 依赖必须有！
        mpg.setTemplateEngine(new FreemarkerTemplateEngine());
        mpg.execute();
    }
}
```

## 13.3、测试

```bash
BASH
17:43:00.088 [main] DEBUG com.baomidou.mybatisplus.generator.engine.AbstractTemplateEngine - 模板:/templates/mapper.xml.ftl;  文件:/Users/xuwei/Desktop/项目/mybatis-plus-sample-generator/src/main/resources/mapper/usr/TbUserMapper.xml
17:43:00.199 [main] DEBUG com.baomidou.mybatisplus.generator.engine.AbstractTemplateEngine - 模板:/templates/entity.java.ftl;  文件:/Users/xuwei/Desktop/项目/mybatis-plus-sample-generator/src/main/java/org/example/generator/usr/entity/TbUser.java
17:43:00.207 [main] DEBUG com.baomidou.mybatisplus.generator.engine.AbstractTemplateEngine - 模板:/templates/mapper.java.ftl;  文件:/Users/xuwei/Desktop/项目/mybatis-plus-sample-generator/src/main/java/org/example/generator/usr/mapper/TbUserMapper.java
17:43:00.209 [main] DEBUG com.baomidou.mybatisplus.generator.engine.AbstractTemplateEngine - 模板:/templates/service.java.ftl;  文件:/Users/xuwei/Desktop/项目/mybatis-plus-sample-generator/src/main/java/org/example/generator/usr/service/ITbUserService.java
17:43:00.211 [main] DEBUG com.baomidou.mybatisplus.generator.engine.AbstractTemplateEngine - 模板:/templates/serviceImpl.java.ftl;  文件:/Users/xuwei/Desktop/项目/mybatis-plus-sample-generator/src/main/java/org/example/generator/usr/service/impl/TbUserServiceImpl.java
17:43:00.213 [main] DEBUG com.baomidou.mybatisplus.generator.engine.AbstractTemplateEngine - 模板:/templates/controller.java.ftl;  文件:/Users/xuwei/Desktop/项目/mybatis-plus-sample-generator/src/main/java/org/example/generator/usr/controller/TbUserController.java
17:43:00.213 [main] DEBUG com.baomidou.mybatisplus.generator.AutoGenerator - ==========================文件生成完成！！！==========================
```

[![image-20221101174415257](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Mybatis-Plus/image-20221101174415257.png)](https://weishao-996.github.io/img/黑马程序员-Mybatis-Plus/image-20221101174415257.png)

# 14、MybatisX 快速开发插件

MybatisX 是一款基于 IDEA 的快速开发插件，为效率而生。 安装方法：打开 IDEA，进入 File -> Settings -> Plugins -> Browse Repositories，输入 mybatisx 搜索并安装。 功能： Java 与 XML 调回跳转 Mapper 方法自动生成 XML