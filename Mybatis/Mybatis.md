# 1. 简介

## 1.1 什么是mybatis

[Mybatis文档网站：](https://mybatis.net.cn/)

- MyBatis 是一款优秀的**持久层框架**，
- 它支持自定义 SQL、存储过程以及高级映射。
- MyBatis 免除了几乎所有的 JDBC 代码以及设置参数和获取结果集的工作。
- MyBatis 可以通过简单的 XML 或注解来配置和映射原始类型、接口和 Java POJO（Plain Old Java Objects，普通老式 Java 对象）为数据库中的记录。

如何获取mybatis

![image-20220724155208165](typora图片/image-20220724155208165.png)

maveb仓库：

```xml
 <dependency>
          <groupId>org.mybatis</groupId>
          <artifactId>mybatis</artifactId>
          <version>3.5.9</version>
      </dependency>
```

## 1.2 持久化

![image-20220724182445812](typora图片/image-20220724182445812.png)

## 1.3持久层

![image-20220724182701924](typora图片/image-20220724182701924.png)

## 1.4为什么需要mybatis

![image-20220724183506117](typora图片/image-20220724183506117.png)

![image-20220724183535720](typora图片/image-20220724183535720.png)

# 2.第一个mybatis程序

![image-20220724184014225](typora图片/image-20220724184014225.png)

## 2.1 搭建环境

![image-20220724184038127](typora图片/image-20220724184038127.png)



```xml
  <dependencies>
<!-- mybatis依赖-->
      <dependency>
          <groupId>org.mybatis</groupId>
          <artifactId>mybatis</artifactId>
          <version>3.5.9</version>
      </dependency>
<!-- 数据库依赖-->
      <dependency>
          <groupId>mysql</groupId>
          <artifactId>mysql-connector-java</artifactId>
          <version>8.0.17</version>
      </dependency>
<!--  junit依赖-->
      <dependency>
          <groupId>junit</groupId>
          <artifactId>junit</artifactId>
          <version>4.13.1</version>
          <scope>test</scope>
      </dependency>
  </dependencies>
```

## 2.1 创建一个模块

- 编写mybatis的核心配置文件

  ```xml
  <!--configguration核心配置文件-->
  <configuration>
      <environments default="development">
          <environment id="development">
              <transactionManager type="JDBC"/>
              <dataSource type="POOLED">
                  <property name="driver" value="com.mysql.jdbc.Driver"/>
                  <property name="url" value="jdbc:mysql://localhost:3306/mybatis?useSSl=true&amp;characterEncoding=UTF-8&amp;useUnicode=true"/>
                  <property name="username" value="root"/>
                  <property name="password" value="root"/>
              </dataSource>
          </environment>
      </environments>
  ```

- 编写mybatis工具类

  ```java
  /**
  Mybatis工具类
   */
  public class MybatisUtils {
      static SqlSessionFactory sqlSessionFactory = null;
      static {
          //使用mybatis第一步：获取sqlSessionFactory对象
          String resource = "mybatis-config.xml";
          InputStream inputStream = null;
          try {
              inputStream = Resources.getResourceAsStream(resource);
          } catch (IOException e) {
              e.printStackTrace();
          }
           sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
      }
      //既然有了sqlSessionFactory，我们就可以从中获得SqlSession的实列了。
      // SqlSession 完全包含了面向数据库执行SQL命令所需要的所有方法
      public static SqlSession getSqlSession() {
          return sqlSessionFactory.openSession();
      }
  }
  ```

  ## 2.3编写代码

  - 实体类

    ```java
    /**
    user实体类
     */
    public class User {
        private int id;
        private String name;
        private String pwd;
        public User() {
        }
        public User(int id, String name, String pwd) {
            this.id = id;
            this.name = name;
            this.pwd = pwd;
        }
        public int getId() {
            return id;
        }
        public void setId(int id) {
            this.id = id;
        }
        public String getName() {
            return name;
        }
        public void setName(String name) {
            this.name = name;
        }
        public String getPwd() {
            return pwd;
        }
        public void setPwd(String pwd) {
            this.pwd = pwd;
        }
    }
    ```

    

  - Dao接口

    ```java
    package com.dao;
    import com.Pojo.User;
    import java.util.List;
    /**
    实现接口
     */
    public interface UserDap {
        List<User> getUserList();
    }
    ```

    

  - 接口实现类 由原来的UserDaoImpl转变成一个Mapper配置文件

    ```java
    <?xml version="1.0" encoding="UTF-8" ?>
    <!DOCTYPE mapper
            PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
            "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
    <!--namespace 绑定一个对应的Dao/Mapper接口-->
    <mapper namespace="com.dao.UserDap">
    <!-- id:对应的接口的方法名称  resultType：对应的返回的参数类型-->
        <select id="getUserList" resultType="com.Pojo.User">
            select * from user ;
        </select>
    </mapper>
    ```

    ## 2,2 测试

    注意点**:org.apache.ibatis.binding.BindingException: Type interface com.dao.UserDap is not known to the MapperRegistry.**

```xml
<!--<?xml version="1.0" encoding="UTF-8" ?>-->
<!--<!DOCTYPE configuration-->
<!--        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"-->
<!--        "http://mybatis.org/dtd/mybatis-3-config.dtd">-->

<!--&lt;!&ndash;configguration核心配置文件&ndash;&gt;-->
<!--<configuration>-->
<!--    <environments default="development">-->
<!--        <environment id="development">-->
<!--            <transactionManager type="JDBC"/>-->
<!--            <dataSource type="POOLED">-->
<!--                <property name="driver" value="com.mysql.jdbc.Driver"/>-->
<!--                <property name="url" value="jdbc:mysql://localhost:3306/mybatis?useSSl=true&amp;characterEncoding=UTF-8&amp;serverTimezone=UTC;&amp;useUnicode=true"/>-->
<!--                <property name="username" value="root"/>-->
<!--                <property name="password" value="root"/>-->
<!--            </dataSource>-->
<!--        </environment>-->
<!--    </environments>-->
<!--    &lt;!&ndash; 每一个Mapper.xml都需要在Mybatis核心配置文件中注册&ndash;&gt;-->
<!--    <mappers>-->
<!--        <mapper resource="com/dao/UserDao.xml"/>-->
<!--    </mappers>-->
<!--</configuration>-->
```

```xml
<!--    在build中配置resources ， 来防止我们资源导出失败的问题-->
<build>
    <resources>
        <resource>
            <directory>src/main/resources</directory>
            <includes>
                <include>**/*.properties</include>
                <include>**/*.xml</include>
            </includes>
        </resource>
        <resource>
            <directory>src/main/java</directory>
            <includes>
                <include>**/*.properties</include>
                <include>**/*.xml</include>
            </includes>
        </resource>
    </resources>
</build>
```

![image-20220724205627956](typora图片/image-20220724205627956.png)

# 3.CRUD(增删改查)

## 1.namespace

namespace中的包名要和Dao/mapper接口的包名一致！

## 2.select

选择，查询语句：

- id：就是对应的namespace中的方法名
- resultType：sql语句执行的返回值！
- parameterType:参数类型！

```java
 /**
     * 增删改需要提交事务
     */
    @Test
    public void insert(){
        SqlSession sqlSession = MybatisUtils.getSqlSession();
        UserMapper mapper = sqlSession.getMapper(UserMapper.class);
        User user = new User();
        user.setId(4);
        user.setName("张三");
        user.setPwd("111111");
        int i = mapper.addUser(user);
        if (i > 0){
            System.out.println("添加成功");
        }else {
            System.out.println("添加失败");
        }
         sqlSession.commit();//需要提交事务才可以
        sqlSession.close();
    }
```

## 3.错误分析

![image-20220725125828020](typora图片/image-20220725125828020.png)

## 4.万能Map

![image-20220725132323642](typora图片/image-20220725132323642.png)

```java
    //万能的map
    int addUser1(Map<String,Object> map);
```

```java
    <insert id="addUser1" parameterType="map">
        insert into user(id,name,pwd)
        values(#{i1d},#{na1me},#{p1wd})
    </insert>
```

```java
 @Test
    public void map(){
        SqlSession sqlSession = MybatisUtils.getSqlSession();
        UserMapper mapper = sqlSession.getMapper(UserMapper.class);
        Map<String, Object> map = new HashMap<>();
        map.put("i1d",11);
        map.put("na1me","12222");
        map.put("p1wd","1111111");
        int i = mapper.addUser1(map);
        if (i > 0 ){
            System.out.println("添加成功");
        }

        sqlSession.commit();
        sqlSession.close();
    }
```

![](typora图片/image-20220725132837072-1659192842418219-1659192844955221.png)

## 5.思考题

![image-20220725133511670](typora图片/image-20220725133511670.png)

# 4.配置解析

## 1. 核心配置文件

![image-20220725133750829](typora图片/image-20220725133750829.png)

```xml
properties（属性）
settings（设置）
typeAliases（类型别名）
typeHandlers（类型处理器）
objectFactory（对象工厂）
plugins（插件）
environments（环境配置）
environment（环境变量）
transactionManager（事务管理器）
dataSource（数据源）
databaseIdProvider（数据库厂商标识）
mappers（映射器）
```

## 2.环境配置（environments）

![image-20220725140028663](typora图片/image-20220725140028663.png)

## 3.属性（properties）

![image-20220725140401724](typora图片/image-20220725140401724.png)

```properties
driver = com.mysql.jdbc.Driver
url = "jdbc:mysql://localhost:3306/mybatis?useSSl=true&characterEncoding=UTF-8&serverTimezone=UTC&useUnicode=true"
username = root
password = root
```

![image-20220725140605943](typora图片/image-20220725140605943.png)

![image-20220725140706073](typora图片/image-20220725140706073.png)

## 4.类型别名（typeAliases）

![image-20220725152808599](typora图片/image-20220725152808599.png)

```java
    <!--起别名  给实体类取别名-->
    <typeAliases>
        <typeAlias type="com.Pojo.User" alias="User"/>
    </typeAliases>
```

![image-20220725152932218](typora图片/image-20220725152932218.png)

```java
    <!--起别名  给实体类取别名-->
    <typeAliases>
        <package name="com.Pojo"/> 
    </typeAliases>
```

![image-20220725153448253](typora图片/image-20220725153448253.png)

## 5.设置（settings）

![image-20220725154029188](typora图片/image-20220725154029188.png)

## 6.映射器（mappers）

![image-20220725154438487](typora图片/image-20220725154438487.png)

- 方式一

   ~~~xml
   ```xml
       <!-- 每一个Mapper.xml都需要在Mybatis核心配置文件中注册-->
       <mappers>
      <mapper resource="com/mapper/UserMapper.xml"/>
       </mappers>
   ```
   ~~~

-  方式二：使用class文件绑定注册

  ```xml
      <mappers>
     <mapper class="com/mapper/UserMapper"/>
      </mappers>
  ```

![image-20220725154807866](typora图片/image-20220725154807866.png)

- 方式三：使用扫描包进行注入绑定

 ```xml
    <mappers>
   <package name="com.mapper"/>//包扫描的方式
     </mappers>
 ```

![image-20220725160806457](typora图片/image-20220725160806457.png)

## 7.生命周期和作用域

![image-20220725161032538](typora图片/image-20220725161032538.png)

![image-20220725161136404](typora图片/image-20220725161136404.png)

![image-20220725161252529](typora图片/image-20220725161252529.png)

![image-20220725161307840](typora图片/image-20220725161307840.png)

![image-20220725161323998](typora图片/image-20220725161323998.png)

# 5.解决属性名和字段名不一致的问题

## 1.问题



![image-20220725161503655](typora图片/image-20220725161503655.png)

![image-20220725161610720](typora图片/image-20220725161610720.png)

![image-20220725161735382](typora图片/image-20220725161735382.png)

## 2.resultMap

![image-20220725162006245](typora图片/image-20220725162006245.png)

![image-20220725161950374](typora图片/image-20220725161950374.png)

![image-20220725162456031](typora图片/image-20220725162456031.png)

# 6.日志

## 1.日志工厂

![image-20220725164303006](typora图片/image-20220725164303006.png)

![image-20220725165153978](typora图片/image-20220725165153978.png)

![image-20220725165127011](typora图片/image-20220725165127011.png)

```xml
logImpl
```

```xml
<!--设置日志-->
<settings>
    <setting name="logImpl" value="STDOUT_LOGGING"/>
</settings>
```

## 2.Log4j

![image-20220725165418422](typora图片/image-20220725165418422.png)

```xml
  <dependency>
            <groupId>log4j</groupId>
            <artifactId>log4j</artifactId>
            <version>1.2.17</version>
        </dependency>
```

**这个之后在看**





# 7.分页

**思考：为什么需要分页？**

- 减少数据的处理量





## 1.**使用Limit分页**

```sql
语法： select * from user limit startIndex,pageSize
select * from user limit 3; #[0,n]
```



使用Mybatis实现分页，核心SQL

1.接口

```java
   //分页
    List<User2> getUserLimit(Map<String,Integer> map);
```

2.Mapper.xml

```xml
  <!--分页查询-->
    <select id="getUserLimit" resultType="user2" parameterType="map">
         select * from user limit #{startIndex},#{pageSize}
    </select>
```

3.测试

```java
    @Test
    public void t1(){
        SqlSession sqlSession = MybatisUtils.getSqlSession();
        UserMapper mapper = sqlSession.getMapper(UserMapper.class);
        Map<String, Integer> map= new HashMap<>();
        map.put("startIndex",0);
        map.put("pageSize",2);
        List<User2> userLimit = mapper.getUserLimit(map);
        System.out.println(userLimit);
        sqlSession.close();
    }
```



## 2.RowBounds分页

![image-20220725214413909](C:\Users\杨润\AppData\Roaming\Typora\typora-user-images\image-20220725214413909.png)

![image-20220725214428959](typora图片/image-20220725214428959.png)

![image-20220725214454549](typora图片/image-20220725214454549.png)

![image-20220725214512448](typora图片/image-20220725214512448.png)

![image-20220725214744572](typora图片/image-20220725214744572.png)

# 8.使用注解

 1.注解在接口上实现

```java
   //获取所有用户
    @Select("select * from user ")
    List<User3> getUser();
```

2.需要在核心配置文件中绑定接口！

```xml
 <!-- 每一个Mapper.xml都需要在Mybatis核心配置文件中注册-->
    <mappers> <!--绑定接口-->
   <mapper class="com.mapper.UserMapper"/>
    </mappers>
```

![image-20220725220302890](typora图片/image-20220725220302890.png)

![image-20220725220437319](typora图片/image-20220725220437319.png)

**之后看**

![image-20220725220649763](typora图片/image-20220725220649763.png)

# 9.Lombok

![image-20220725221128988](typora图片/image-20220725221128988.png)

![image-20220725221152062](typora图片/image-20220725221152062.png)

# 10.多对一处理

![image-20220725221437987](typora图片/image-20220725221437987.png)

![image-20220725223618422](typora图片/image-20220725223618422.png)

实体类：

```java
public class Student {
    private int id;
    private String name;
    private Teacher teacher;
}
```

## 1. 按照查询嵌套处理

```xml
    <!--
    思路：
        1.查询所有的学生信息
        2.根据查询出来的学生的tid，寻找对应的老师
    -->
    <!--//查询所有老师的信息，以及对应老师的信息-->
 <select id="getStudent" resultMap="studentTeacher">
     select * from student
 </select>
    <resultMap id="studentTeacher" type="student">
        <result column="id" property="id"></result>
        <result column="name" property="name"></result>
        <!--复杂的属性我们要单独处理
        对象：association
        集合：collection
        -->
        <association property="teacher" column="tid" javaType="Teacher" select="getTeacher"/>
    </resultMap>
 <select id="getTeacher" resultType="Teacher">
     select * from teacher where id = #{id}
 </select>
```

## 2. 按照结果嵌套处理

```xml
  <resultMap id="studentTeacher" type="Student">
     <result property="id" column="sid"/>
        <result property="name" column="sname"/>
        <association property="teacher" javaType="teacher">
            <result property="name" column="tname"/>
        </association>
    </resultMap>

    <select id="getStudent2" resultMap="studentTeacher">
        select s.id sid,s.name sname,t.name tname
        from student s,teacher t
        where s.tid = t.id;
    </select>
```

![image-20220726115355537](typora图片/image-20220726115355537.png)

# 11.一对多

![image-20220726115446566](typora图片/image-20220726115446566.png)

实体类：

```java
/**
学生实体类
 */
public class Student {
    private int id;
    private String name;
    //学生需要关联一个老师
    private int tid;
```

## 1.按结果嵌套查询

![image-20220726120450271](typora图片/image-20220726120450271.png)

## 2.按照查询嵌套处理

![image-20220726120609580](typora图片/image-20220726120609580.png)

![image-20220726120707690](typora图片/image-20220726120707690.png)

![image-20220726120809508](typora图片/image-20220726120809508.png)

# 12.动态SQL

![image-20220726121209542](typora图片/image-20220726121209542.png)

## 1.IF

```java
public class Blog {
    private String id;
    private String title;
    private String author;
    private Date createTime;
    private int views;
}
```

```xml
 <select id="getBlogif" resultType="Blog" parameterType="map">
        select * from blog
       where 1 = 1
    <if test="title!=null">
        and title = #{title}
    </if>
   <if test="author != null">
       and author = #{author}
   </if>
    </select>
```

| mapUnderscoreToCamelCase        | 是否开启驼峰命名自动映射，即从经典数据库列名 A_COLUMN 映射到经典 Java 属性名 aColumn。 | true \| false | False |
| ------------------------------- | ------------------------------------------------------------ | ------------- | ----- |
| 这个是到mybatis核心配置文件里面 |                                                              |               |       |

```xml
<settings>
    <setting name="mapUnderscoreToCamelCase" value="true "/>
</settings>
```

```java
 @Test
   public void t2(){
      SqlSession sqlSession = MybatisUtils.getSqlSession();
      BlogMapper mapper = sqlSession.getMapper(BlogMapper.class);
      Map<String, String> map = new HashMap<String, String>();
      map.put("title","Mybatis如此简单");
//      map.put("author","");
      List<Blog> blogif = mapper.getBlogif(map);
      for (Blog b: blogif) {
         System.out.println(b);
      }
      sqlSession.close();
   }
```

```java
//工具类
public class IDutils {

    public static String getId(){
        return UUID.randomUUID().toString().replaceAll("-","");
    }
    @Test
    public void w(){
        String id = IDutils.getId();
        System.out.println(id);
    }
}
```

## 2,choose(when、otherwise)

```xml
   <select id="queryChoose" resultType="com.Pojo.Blog">
        select * from blog
     <where>
         <choose>
             <when test="title!=null">
                 and title = #{title}
             </when>
             <when test="author != null">
                 and author = #{author}
             </when>
<otherwise>
    /*如果前面的不满足就执行这个，跟java中的switch一样*/
</otherwise>
         </choose>
     </where>
    </select>
```







## 3.trim(where、set)

![image-20220726145032681](typora图片/image-20220726145032681.png)

![image-20220726145706856](typora图片/image-20220726145706856.png)

**set：是用在update 中的，可以帮你去掉逗号。**

## 4.sql片段

![](typora图片/image-20220726150342714.png)

![image-20220726150406517](typora图片/image-20220726150406517.png)

减少代码的复用

##  5.foreach(用到了在学)

# 13.缓存

## 1.简介

![image-20220726150736330](typora图片/image-20220726150736330.png)

## 2.mybatis缓存

![image-20220726150802308](typora图片/image-20220726150802308.png)