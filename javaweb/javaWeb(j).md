## 1 、基本概念

### 1.1、前言

web开发：

web，网页的意思，www.baidu.com

静态web

html,css

提供给所有人看的数据始终不会发生变化！

动态web

淘宝，几乎是所有的网站；

提供给所有人看的数据始终会发生变化，每个人在不同的时间，不同的地点看到的信息各不相同！

技术栈：Servlet/JSP，ASP，PHP

### 1.2、web应用程序web应用程序：

可以提供浏览器访问的程序；

- a.html、b.html.....多个web资源，这些web资源可以被外界访问，对外界提供服务；
- 你们能访问到的任何一个页面或者资源，都存在于这个世界的某一个角落的计算机上。
- URL
- 这个统一的web资源会被放在同一个文件夹下，web应用程序>Tomcat：服务器
- 一个web应用由多部分组成（静态web，动态web)
  - html,css,js
  - jsp,servlet
  - Java程序
  - jar包
  - 配置文件（Properties)

Web使用程序编写完毕后，若想提供给外界访问；需要一个服务器来统一管理。

### 1.3、静态web

- *.htm， *.html这些都是网员的后境、如果服务器上一直存在这些东四，我们就可以直接进行读取、需要网络；

![静态web](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231116409-2120520000.png)

- 静态web存在的缺点
- Web页面无法动态更新，所有用户看到都是同一个页面
  - 轮播图，点击特效：伪动态
  - JavaScript[实际开发中，它用的最多]
  - VBScript

它无法和数据库交互（数据无法持久化，用户无法交互）

### 1.4、 动态web

页面会动态展示，“web页面的展示效果因人而异”，看个人

![动态web](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231116156-1254113150.png)

缺点：

- 加入服务器的动态web资源出现了错误，我们需要重新编写我们的后台程序，重新发布；
  - 停机维护优点：
- Web页面可以动态更新，所有用户看到都不是同一个页面
- 它可以与数据库交互（数据持久化：注册，商品信息，用户信息........）
- ![动态web2](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231115927-201764454.png)

## 2 、web服务器

### 2.1、技术讲解

##### ASP:

- 微软：国内最早流行的就是ASP；
- 在HTML中嵌入了VB的脚本，ASP+COM；
- 在ASP开发中，基本一个页面都有几干行的业务代码，页面极其换乱；
- 维护成本高！
- C#
- IIS

##### php:

- PHP开发速度很快，功能很强大，跨平台，代码很简单（70%，WP）；
- 无法承载大访问量的情况（局限性）；

##### jSP/Servlet:

B/S；浏览和服务器C/S：客户端和服务器

- sun公司主推的B/S架构
- 基于Java语言的（所有的大公司，或者一些开源的组件，都是用Java写的）；
- 可以承载三高问题带来的影响；（高并发，高可用。高性能）
- 语法像ASP，ASP->JSP，加强市场强度；

### 2.2、web服务器

服务器是一种被动的操作，用来处理用户的一些请求和给用户一些响应信息；

lIS

微软的；ASP.,Windows中自带的

Tomcat

![TomcatLogo](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231115738-1579938947.png)

面向百度编程：

Tomcat是Apache 软件基金会（Apache Software Foundation)的jakarta项目中的一个核心项目，最

新的Servlet 和JSP 规范总是能在Tomcat中得到体现，因为Tomcat 技术先进、性能稳定，而且免费，

因而深受lava爱好者的喜爱并得到了部分软件开发商的认可，成为目前比较流行的Web应用服务器。

Tomcat 服务器是一个免费的开放源代码的Web应用服务器，属于轻量级应用服务器，在中小型系统和

并发访问用户不是很多的场合下被普遍使用，是开发和调试JSP程序的首选。对于一个Java初学web的人

来说，它是最佳的选择。

Tomcat 实际上运行JSP页面和Serlet。Tornct最新版已经更新到了10

工作3-5年之后，可以尝试手写Tomcat服务器；

下载tomcat：

1. 安装or解压
2. 了解配置文件及目录结构
3. 了解这个东西的作用

## 3 、Tomcat

安装之前要知道

1. 确定自己Java环境变量是否安装好,JDK和JRE都需要配置环境变量
2. 在下载之前看好自己jdk的版本来选择，并不是最高的版本他就是最好的，看下面这里

![tomcat版本](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231115474-265516951.png)

### 3.1安装tomcat

官网：https://tomcat.apache.org/

![tomcat安装](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231115079-336189952.png)

![解压1](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231114721-513630865.png)

### 3.2、Tomcat启动和配置

文件夹作用:

![文件作用](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231114447-232345662.png)

启动和关闭Tomcat

![启动关闭](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231114184-705900978.png)

访问测试：http://localhost:8080/

可能遇到的问题：

1. Java环境变量没有配置
2. 闪退问题：需要配置兼容性，可能没配置好Java环境变量
3. 乱码问题：配置文件中设置

```xml
可以修改 conf/logging.properties 中的:java.util.logging.ConsoleHandler.encoding = GBK 解决乱码,但不建议，如果你改变了，在使用编辑器的时候编辑器可能会出现问题
```

### 3.3、配置

![conf](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231113926-1842585040.png)

可以配置启动的端口号

- tomcat的默认端口号为： 8080
- mysql: 3306
- http: 80
- https： 443

```java
<Connector port="8080" protocol="HTTP/1.1"
      connectionTimeout="20000"
      redirectPort="8443" />
```

可以配置主机的名称

- 默认的主机名为：localhost->127.0.0.
- 默认网站应用存放的位置为：webapps

```java
  <Host name="www.clear.com"  appBase="webapps"
        unpackWARs="true" autoDeploy="true">
```

高难度面试题：

请你谈谈网站是如何进行访问的！

1. 输入一个域名；回车

2. 检查本机的C:\Windows\System32\drivers\etc\hosts配置文件下有没有这个域名映射；

   1. 有：直接返回对应的ip地址，这个地址中，有我们需要访问的web程序，可以直接访问

   ```java
    127.0.0.1 www.clear.com
   ```

   1. 没有：去DNS服务器找，找到的话就返回，找不到就返回找不到；

   ![域名](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231113328-965329938.png)

3. 可以配置一下环境变量（可选性）

### 3.4、发布一个web网站

不会就先模仿

- 将自己写的网站，放到服务器（Tomcat)中指定的web应用的文件夹（webapps)下，就可以访问了

网站应该有的结构

```java
--webapps ：Tomcat服务器的web目录
	-ROOT
	-kuangstudy ：网站的目录名
		- WEB-INF
			-classes : java程序
			-lib：web应用所依赖的jar包
			-web.xml ：网站配置文件
		- index.html 默认的首页
		- static 
            -css
            	-style.css
            -js
            -img
         -.....
```

HTTP协议：面试
Maven:构建工具

- Maven安装包

Servlet入门

- HelloWorld!
- Servlet配置 ·原理

## 4、Http

### 4.1、什么是HTTP

(超文本传输协议）是一个简单的请求-响应协议，它通常运行在TCP之上。

- 文本：html，字符串，…
- 超文本：图片，音乐，视频，定位，地图.……
- 端口:80

Https:安全的

- 端口:443

### 4.2、两个时代

- http1.0
  - HTTP/1.0：客户端可以与web服务器连接后，只能获得一个web资源，断开连接
- http1.1
  - HTTP/1.1：客户端可以与web服务器连接后，可以获得多个web资源。

### 4.3、Http请求

- 客户端–发请求（Request）–服务器

百度：

```java
Request URL:https://www.baidu.com/   请求地址
Request Method:GET    get方法/post方法
Status Code:200 OK    状态码：200
Remote（远程） Address:14.215.177.39:443

Accept:text/html  
Accept-Encoding:gzip, deflate, br
Accept-Language:zh-CN,zh;q=0.9    语言
Cache-Control:max-age=0
Connection:keep-alive
```

#### 1、请求行

- 请求行中的请求方式：GET
- 请求方式：**Get,Post,**HEAD,DELETE,PUT,TRACT.…
  - get：请求能够携带的参数比较少，大小有限制，会在浏览器的URL地址栏显示数据内容，不安全，但高效
  - post:请求能够携带的参数没有限制，大小没有限制，不会在浏览器的URL地址栏显示数据内容，安全，但不高效。

#### 2、消息头

```java
Accept：告诉浏览器，它所支持的数据类型
Accept-Encoding：支持哪种编码格式  GBK   UTF-8   GB2312  ISO8859-1
Accept-Language：告诉浏览器，它的语言环境
Cache-Control：缓存控制
Connection：告诉浏览器，请求完成是断开还是保持连接
HOST：主机..../.
```

### 4.4、Http响应

- 服务器–响应…….客户端

百度：

```java
Cache-Control:private    缓存控制
Connection:Keep-Alive    连接
Content-Encoding:gzip    编码
Content-Type:text/html   类型  
```

#### 1、响应体

```java
Accept：告诉浏览器，它所支持的数据类型
Accept-Encoding：支持哪种编码格式  GBK   UTF-8   GB2312  ISO8859-1
Accept-Language：告诉浏览器，它的语言环境
Cache-Control：缓存控制
Connection：告诉浏览器，请求完成是断开还是保持连接
HOST：主机..../.
Refresh：告诉客户端，多久刷新一次；
Location：让网页重新定位；
```

#### 2、响应状态码

200：请求响应成功 200

3xx:请求重定向

- 重定向：你重新到我给你新位置去；

4xx:找不到资源 404

- 资源不存在；

5xx:服务器代码错误 500  502: 网关错误



##### **常见面试题：**

   **当你的浏览器中地址栏输入地址并会回车的一瞬间到页面能够展示回来，经历了什么？**

1. （域名解析）在客户端，浏览器输入地址后，首先会在windows系统文件的hosts中查找是否有对应的ip地址，如果没有则需要向DNS域名解析服务器询问该域名对应的ip地址。

2. （TCP三次握手）获取相应的ip地址后，客户端与服务器端建立TCP连接（三次握手），（网络层，数据链路层，物理层）

   三次握手-->

   1. 第一次握手：客户端向服务器端发送一个SYN段，该段中包含客户端的初始序列号。
   2. 第二次握手：服务器端返回客户端SYN+ACK，该端中包含服务器端的初始序列号，ACK表示，已经确定收到客户端的SYN段。
   3. 第三次握手：客户端向服务器端响应一个ACK端，ACK表示，已经确定接受到服务器端的SYN段。

3. （建立起TCP连接后发起http请求）客户端向服务器端发送请求，包含请求行，请求头。主要的两种请求方式（GET与POST）

   1. GET:请求能够携带的参数比较少，大小有限制，会在浏览器的URL地址栏显示数据的内容，不安全，但高效。
      1. POST:请求能够携带的参数没有限制，大小没有限制，不会在浏览器的URL地址栏显示数据内容，安全，但不高效。

4. （服务器响应http请求）服务器处理请求，并返回响应，包含状态码，响应头，响应体。

5. （浏览器解析http代码）浏览器收到响应，解析http代码渲染页面，并在浏览器页面展示出来。

6. （断开连接）http1.0短连接，http1.1长连接。



## 5、Maven

**我为什么要学习这个技术？**

1. 在Javaweb开发中，需要使用大量的jar包，我们手动去导入；
2. 如何能够让一个东西自动帮我导入和配置这个jar包。

由此，Maven诞生了！

### 5.1、Maven项目架构管理工具

我们目前用来就是方便导入jar包的！

Maven的核心思想：**约定大于配置**

- 有约束，不要去违反。

Maven会规定好你该如何去编写我们Java代码，必须要按照这个规范来；

### 5.2、下载安装Maven

官网：https://maven.apache.org/

![Maven下载](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231113046-904257473.png)

下载完成后，解压即可；

小狂神老师友情建议：电脑上的所有环境都放在一个文件夹下，方便管理；

### 5.3、配置环境变量

在我们的系统环境变量中配置如下配置：

- M2_HOME maven目录下的bin目录
- MAVEN_HOME maven的目录
- 在系统的path中配置%MAVEN_HOME%\bin

![test](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231112806-869251097.png)

使用命令 **mvn -version**测试Maven是否安装成功，保证必须配置完毕！

### 5.4、阿里云镜像

- 镜像：mirrors
- 作用：加速我们的下载
- 国内建议使用阿里云的镜像

```java
<mirror>
    <id>nexus-aliyun</id>  
    <mirrorOf>*,!jeecg,!jeecg-snapshots</mirrorOf>  
    <name>Nexus aliyun</name>  
    <url>http://maven.aliyun.com/nexus/content/groups/public</url> 
</mirror>
```

**F:\maven\apache-maven-3.6.1\conf\settings.xml**
（我的仓库配置源和仓库的文件位置）

### 5.5、本地仓库

在本地的仓库，远程仓库； 建立一个本地仓库：localRepository

```java
 <localRepository>F:\maven\apache-maven-3.8.6\maven-repo</localRepository>
```

### 5.6、在IDEA中使用Maven

##### **由于我的IDEA是2021版本的所以跟视频操作有点不一样，低版本可以看狂神老师**😁

1. 启动IDEA
2. 创建一个Maven项目

![Maven使用](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231112561-511985367.png)

![Maven03](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231112037-240104385.png)

![Maven04](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231111833-932319591.png)

1. 等待项目初始化完毕

![Maven06](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231111331-481458382.png)

1. 观察maven仓库中多了什么东西？

![Maven07](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231111081-1630812731.png)

1. IDEA中的Maven设置

![Maven08](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231110806-894389382.png)

![Maven09](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231110520-1925594007.png)

1. 到这里，Maven在IDEA中的配置和使用就OK了

### 5.7、创建一个普通的Maven项目

![Maven10](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231110266-575700739.png)

![Maven12](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231110022-1716725491.png)

### 5.8标记文件夹功能

第一种方法：

![Maven13](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231109705-1103798393.png)

第二种方法：

![Maven14](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231109278-525437858.png)

![Maven15](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231109058-292766214.png)

### 5.9在IDEA中配置Tomcat

![Tomcat01](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231108835-192093788.png)

![Tomcat02](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231108620-146923204.png)

![Tomcat03](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231108367-1746070518.png)

![Tomcat04](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231108124-449527678.png)

解决警告问题

为什么会有这个问题：我们访问一个网址，需要指定一个文件夹的名字；

artifacts警告我们要创建，点击右边的Fix或者点击Deployment

![Tomcat5](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231107882-1209978310.png)

![Tomcat6](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231107663-1612737127.png)

![Tomcat07](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231107397-785833956.png)

![Tomcat08](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231107149-1435656564.png)

![Tomcat09](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231106922-1574583612.png)

Tomcat到这里就配置成功了😊😁

### 5.10 pom文件

pom.xml是Maven的核心配置文件

![Maven介绍01](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231106678-1437584947.png)

![Maven介绍02](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231106340-1072925277.png)

pom.xml文件介绍

![Maven介绍03](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231106094-98018008.png)

![Maven介绍04](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231105856-636601007.png)

Maven由于他的约定大于配置，我们之后可能遇到我们写的配置文件，无法被导出或者不生效的问题，解决办法：

```java
<!--在bui1d中配置resources，来防止我们资源导出失败的问题-->
  <build>
    <resources>
      <resource>
        <directory>src/main/resources</directory>
        <includes>
          <include>**/*.properties</include>
          <include>**/*.xml</include>
        </includes>
        <filtering>false</filtering>
      </resource>
      <resource>
        <directory>src/main/java</directory>
        <includes>
          <include>**/*.properties</include>
          <include>**/*.xml</include>
        </includes>
        <filtering>false</filtering>
      </resource>
    </resources>
  </build>
```

### 5.11 IDEA操作

可能我IDEA版本太高还是因为啥，我的关系依赖的包就那么多😂

![Maven介绍05](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231105626-529889500.png)

### 5.12 解决遇到的问题

1. **建议不要用高版本的maven,用3.6.1**，否则会出现Plugins不出来或其他问题,如果出现了这些问题建议换maven3.6.1就能解决😁
2. IDEA中每次都要重复配置Maven的问题

![配置1](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231105390-1173442208.png)

![配置2](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231104961-1157907351.png)

![配置3](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231104754-1953315384.png)

1. maven默认web项目中的web.xml版本问题！

![版本4](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231104495-565207158.png)

‘’替换为webapp4.0版本和tomcat一致！

![版本2](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231104230-1153716028.png)

这里是web.xml文件😊

```java
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0"
         metadata-complete="true">
</web-app >
```

### 5.13 Maven仓库的使用

地址：https://mvnrepository.com/

![maven使用1](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231103937-572926593.png)

![Maven使用2](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231103640-1132452370.png)

![Maven使用03](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231103280-527201044.png)

![Maven使用05](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231102961-2062405956.png)

作用域一般可以删掉

正常情况应该导入完上面的包就OK了

## 6、Servlet

### 6.1、Servlet简介

- Servlet就是sun公司开发动态web的一门技术
- Sun在这些API中提供一个接口叫做：Servlet，如果你想开发一个Servlet程序，只需要完成两个小步骤：
  - 编写一个类，实现Serlet接口
  - 把开发好java类部署到web服务器中。

### 6.2、HelloServlet

Serlvet接口Sun公司有两个默认的实现类：HttpServlet，GenericServled

### 6.2、HelloServlet

1. 构建一个普通的Maven项目，等理面的sc目录，以后我们的学习就在这个项目里面建立Moudel；这个空的工程就题Maven主工程；
2. 关于Maven父子工程的理解；

父项目中会有

```java
      <modules>
          <module>servlet-01</module>
      </modules>
```

子项目会有

```java
    <parent>
        <artifactId>javaweb-02-servlet</artifactId>
        <groupId>com.shen</groupId>
        <version>1.0-SNAPSHOT</version>
    </parent>
```

父项目中的java子项目可以直接使用(相当于儿子继承了爸爸的东西)

```java
son extends father
```

1. Maven环境优化
2. 修改web.xml为最新的
3. 将maven的结构搭建完整
   .
4. 编写一个Servlet程序
   1. 编写一个普通类
   2. 实现Servlet接口，这里我们直接继承HttpServlet

```java
     public class HelloServlet extends HttpServlet {
         
         //由于get或者post只是请求实现的不同的方式，可以相互调用，业务逻辑都一样；
         @Override
         protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
             //ServletOutputStream outputStream = resp.getOutputStream();
             PrintWriter writer = resp.getWriter(); //响应流
             writer.print("Hello,Serlvet");
         }
     
         @Override
         protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
             doGet(req, resp);
         }
     }
    
```

1. 编写Servlet的映射
   为什么需要映射：我们写的是JAVA程序，但是要通过浏览器访问，而浏览器需要连接web服务器，所以我们需
   要再web服务中注册我们写的Servlet，还需给他一个浏览器能够访问的路径；

```java
	<!--注册Servlet-->
      <servlet>
          <servlet-name>hello</servlet-name>
          <servlet-class>com.shen.servlet.HelloServlet</servlet-class>
      </servlet>
      <!--Servlet的请求路径-->
      <servlet-mapping>
          <servlet-name>hello</servlet-name>
          <url-pattern>/hello</url-pattern>
      </servlet-mapping>
```

 6. 配置Tomcat

注意：配置项目发布的路径就可以了

![Tomcats1](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231102728-113437164.png)

![Tomcats02](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231102464-538256734.png)

1. 启动测试，OK！

### 6.3、Servlet原理

Servlet是由Web服务器调用，web服务器在收到浏览器请求之后，会：

![1](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231102155-249789999.png)

### 6.4、Mapping问题

1. 一个Servlet可以指定一个映射路径

```java
      <servlet-mapping>
          <servlet-name>hello</servlet-name>
          <url-pattern>/hello</url-pattern>
      </servlet-mapping>
```

1. 一个servlet可以指定多个映射路径

```java
      <servlet-mapping>
          <servlet-name>hello</servlet-name>
          <url-pattern>/hello</url-pattern>
      </servlet-mapping>
      <servlet-mapping>
          <servlet-name>hello</servlet-name>
          <url-pattern>/hello2</url-pattern>
      </servlet-mapping>
      <servlet-mapping>
          <servlet-name>hello</servlet-name>
          <url-pattern>/hello3</url-pattern>
      </servlet-mapping>
      <servlet-mapping>
          <servlet-name>hello</servlet-name>
          <url-pattern>/hello4</url-pattern>
      </servlet-mapping>
      <servlet-mapping>
          <servlet-name>hello</servlet-name>
          <url-pattern>/hello5</url-pattern>
      </servlet-mapping>
  
```

1. 一个servlet可以指定通用映射路径

```java
<servlet-mapping>
    <servlet-name>hello</servlet-name>
    <url-pattern>/hello/*</url-pattern>
</servlet-mapping>
```

1. 默认请求路径

```java
   <!--默认请求路径-->
   <servlet-mapping>
       <servlet-name>hello</servlet-name>
       <url-pattern>/*</url-pattern>
   </servlet-mapping>
```

1. 指定一些后缀或者前缀等等…

```java
 <!--可以自定义后缀实现请求映射
      注意点，*前面不能加项目映射的路径
      hello/sajdlkajda.clear
      -->
  <servlet-mapping>
      <servlet-name>hello</servlet-name>
      <url-pattern>*.clear</url-pattern>
  </servlet-mapping>
```

1. 优先级问题

 指定了固有的映射路径优先级最高，如果找不到就会走默认的处理请求；

```java
  <!--404-->
  <servlet>
      <servlet-name>error</servlet-name>
      <servlet-class>com.kuang.servlet.ErrorServlet</servlet-class>
  </servlet>
  <servlet-mapping>
      <servlet-name>error</servlet-name>
      <url-pattern>/*</url-pattern>
  </servlet-mapping>
```

### 6.5、ServletContext

web容器在启动的时候，它会为每个web程序都创建一个对应的ServletContext对象，它代表了当前的web应用；

#### 1、共享数据

我在这个Servlet中保存的数据，可以在另外一个servlet中拿到；

```java
public class HelloServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        
        //this.getInitParameter()   初始化参数
        //this.getServletConfig()   Servlet配置
        //this.getServletContext()  Servlet上下文
        ServletContext context = this.getServletContext();

        String username = "胡凯莉"; //数据
        context.setAttribute("username",username); //将一个数据保存在了	ServletContext中，名字为：username 。值 username

    }

}
public class GetServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        ServletContext context = this.getServletContext();
        String username = (String) context.getAttribute("username");

        resp.setContentType("text/html");
        resp.setCharacterEncoding("utf-8");
        resp.getWriter().print("名字"+username);

    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
    <servlet>
        <servlet-name>hello</servlet-name>
        <servlet-class>com.shen.servlet.HelloServlet</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>hello</servlet-name>
        <url-pattern>/hello</url-pattern>
    </servlet-mapping>


    <servlet>
        <servlet-name>getc</servlet-name>
        <servlet-class>com.shen.servlet.GetServlet</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>getc</servlet-name>
        <url-pattern>/getc</url-pattern>
    </servlet-mapping>
```

测试访问结果；

#### 2、获取初始化参数

```java
<!--配置一些web应用初始化参数-->
<context-param>
    <param-name>url</param-name>
    <param-value>jdbc:mysql://localhost:3306/mybatis</param-value>
</context-param>
protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    ServletContext context = this.getServletContext();
    String url = context.getInitParameter("url");
    resp.getWriter().print(url);
}
```

#### 3、请求转发

```java
@Override
protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    ServletContext context = this.getServletContext();
    System.out.println("进入了ServletDemo04");
    //RequestDispatcher requestDispatcher = context.getRequestDispatcher("/gp"); //转发的请求路径
    //requestDispatcher.forward(req,resp); //调用forward实现请求转发；
    context.getRequestDispatcher("/gp").forward(req,resp);
}
```

![2](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231100802-781448740.png)

4、读取资源文件
Properties

- 在java目录下新建properties
- 在resources目录下新建properties

发现：都被打包到了同一个路径下：classes，我们俗称这个路径为classpath:

思路：需要一个文件流

```properties
username=root12312
password=zxczxczxc
public class ServletDemo05 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {

        InputStream is = this.getServletContext().getResourceAsStream("/WEB-INF/classes/com/kuang/servlet/aa.properties");

        Properties prop = new Properties();
        prop.load(is);
        String user = prop.getProperty("username");
        String pwd = prop.getProperty("password");

        resp.getWriter().print(user+":"+pwd);

    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
```

访问测试即可ok;

### 6.6、HttpServletResponse

```java
web服务器接收到客户端的http请求，针对这个请求，分别创建一个代表请求的HttpServletRequest
对象，代表响应的一个HttpServletResponse;
```

- 如果要获取客户端请求过来的参数：找HttpServletRequest
- 如果要给客户端响应一些信息：找HttpServletResponse

#### 1、简单分类

负责向浏览器发送数据的方法

```java
 servletOutputstream getOutputstream() throws IOException;
 Printwriter getwriter() throws IOException;
```

负责向浏览器发送响应头的方法

```java
void setCharacterEncoding(String var1)；
void setContentLength(int var1)；
void setContentLengthLong(long var1);
void setContentType(String var1)；
void setDateHeader(String varl,long var2)
void addDateHeader(String var1,long var2)
void setHeader(String var1,String var2);
void addHeader(String var1,String var2)；
void setIntHeader(String var1,int var2);
void addIntHeader(String varl,int var2);
```

响应的状态码

![3](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231101427-1638950517.png)

#### 2、下载文件

1. 向浏览器输出消息
2. 下载文件
   1. 要获取下载文件的路径
   2. 下载的文件名是啥？
   3. 设置想办法让浏览器能够支持下载我们需要的东西
   4. 获取下载文件的输入流
   5. 创建缓冲区
   6. 获取OutputStream对象
   7. 将FileOutputStream流写入到bufer缓冲区
   8. 使用OutputStream将缓冲区中的数据输出到客户端！

```java
package com.shen.servlet;

import javax.servlet.ServletException;
import javax.servlet.ServletOutputStream;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.FileInputStream;
import java.io.IOException;
import java.net.URLEncoder;

public class FileServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //1.获取下载文件的路径
        String realPath = "E:\\Workspace\\JavaWorkspace\\StudyJavaweb\\javaweb-02-servlet\\response\\target\\classes\\1.png";
        System.out.println("下载文件的路径："+realPath);
        //2.下载的文件名是啥
        String fileName = realPath.substring(realPath.lastIndexOf("\\") + 1);
        //3.设置想办法让浏览器能够支持下载我们需要的东西
        resp.setHeader("Content-disposition","attachment;filename="+ URLEncoder.encode(fileName,"utf-8"));
        //4.获取下载文件的输入流
        FileInputStream in = new FileInputStream(realPath);
        //5.创建缓冲区
        int len =0;
        byte[] buffer = new byte[1024];
        //6.获得OutputStream对象
        ServletOutputStream out = resp.getOutputStream();
        //7.将FileOutputStream流写入到buffer缓冲区,使用OutputStream将缓冲区中的数据输出到客户端！
        while (in.read(buffer)>0){
            out.write(buffer,0,len);
        }
        in.close();
        out.close();
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
```

#### 3、验证码功能

验证怎么来的?

- 前端实现
- 后端实现，需要用到Java的图片类，生产一个图片

```java
package com.shen.servlet;

import javax.imageio.ImageIO;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.awt.*;
import java.awt.image.BufferedImage;
import java.io.IOException;
import java.util.Random;

public class ImageServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        // 如何让浏览器3秒自动刷新一次;
        resp.setHeader("refresh","3");
        //在内存中创建一个图片
        BufferedImage image = new BufferedImage(80,20,BufferedImage.TYPE_INT_RGB);
       //得到图片
        Graphics2D g =(Graphics2D)image.getGraphics();//笔
        //设置图片的背景颜色
        g.setColor(Color.white);
        g.fillRect(0,0,80,20);
        //给图片写数据
        g.setColor(Color.blue);
        g.setFont(new Font(null,Font.BOLD,20));
        g.drawString(makeNum(),0,20);
//      告诉浏览器，这个请求用图片的方式打开
        resp.setContentType("image/jpeg");
//        网站存在缓存，不让浏览器缓存
        resp.setDateHeader("expires",-1);
        resp.setHeader("Cache-Control","no-cache");
        resp.setHeader("Pragma","no-cache");
        //把图片写给浏览器
        ImageIO.write(image,"jpg",resp.getOutputStream());
    }
//    生成随机数
    private String makeNum(){
        Random random = new Random();
        String  num = random.nextInt(9999999)+"";
        StringBuffer sb = new StringBuffer();
        for (int i = 0; i < 7- num.length(); i++) {
            sb.append("0");
        }
        num= sb.toString()+num;
        return num;
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
折叠 
```

web.xml

```java
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0"
         metadata-complete="true">

    <servlet>
        <servlet-name>ImageServlet</servlet-name>
        <servlet-class>com.shen.servlet.ImageServlet</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>ImageServlet</servlet-name>
        <url-pattern>/img</url-pattern>
    </servlet-mapping>
</web-app >
```

#### 4.实现重定向

![4](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231101090-990124254.png)

什么是重定向：B一个web资源收到客户端A请求后，B他会通知A客户端去访问另一个web资源C，这个过程叫重定向。

常见场景:

- 用户登录

```java
 void sendRedirect(String var1) throws IOException;
```

测试：

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //
       resp.sendRedirect("/response_war/img");//重定向
    }
```

重定向和转发的区别

相同点

- 页面都会实现跳转

不同点

- 请求转发的时候，url不会产生变化 307
- 重定向的时候，url地址会发生变化 302

![2](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231100802-781448740.png)

**index.jsp**

```xml
<html>
	<body>
		<h2>Hel1o World!</h2>
		
		《%--这里超交的路径,需要寻找到项目的路径--%>
		<%--${pageContext. request, contextPath}代表当前的项目--%>
		<form action="${pageContext. request.contextPath}/login" method="get">
			用户名: <input type="text" name="username"> <br>
			密码: <input type="password" name="password"> <br>
			<input type="submit" value="登录">
		</form>
	
	</body>
</html>
```

**RequestTest.java**

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        System.out.println("进入了get方法");
        //  处理请求
        String username = req.getParameter("username");
        String password = req.getParameter("password");
        System.out.println(username+":"+password);
        //  重定向时候一定要注意，路径问题，否则404
        resp.sendRedirect("/response_war/success.jsp");

    }
```

**重定向页面success.jsp**

```java
<%@ page contentType="text/html; charset=UTF-8" language="java" %>
<html>
    <head>
	    <title>Title</title>
	    </head>
    <body>
    	<h1>success</h1>
    </body>
</html>
```

**web.xml配置**

```java
    <servlet>
        <servlet-name>request</servlet-name>
        <servlet-class>com.shen.servlet.RequestTest</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>request</servlet-name>
        <url-pattern>/login</url-pattern>
    </servlet-mapping>
```

**导入依赖的jar包**

```java
    <dependencies>
    <!-- https://mvnrepository. com/artifact/javax. servLet/javax. servlet-opi -->
    <dependency>
    <groupld>javax.servlet</grouptd>
    <artifactId>javax. servlet-api</artifactId>
    <version>4.0.1</version>
    </dependency>
    <!-- https://mvnrepository.com/artifact/javax. servLet.jsp/javax. servLet.jsp-opi -->
    <dependency>
    <groupId>javax.servlet.jsp</groupld>
    <artifactId>javax. servlet.jsp-api</artifactId>
    <version>2.3.3</version>
    </dependency>
    </dependencies>
    </project>
```

### 6.7、HttpServletRequest

HttpServletRequest代表客户端的请求,用户通过Http协议访问服务器, HTTP请求中的所有信息会被封装到HttpServletRequest,通过这个HttpServletRequest的方法,获得客户端的所有信息;

![5](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231100542-63072630.png)

#### 获取参数,请求转发

![6](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231100223-832260337.png)

**自己创建类，且需要继承HttpServlet类**

LoginServlet

```java
public class LoginServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //后台接收乱码问题
        req.setCharacterEncoding("utf-8");
        resp.setCharacterEncoding("utf-8");

        String username = req.getParameter("username");
        String password = req.getParameter("password");
        String[] hobbys = req.getParameterValues("hobbys");
        System.out.println("-----------------------");
        System.out.println(username);
        System.out.println(password);
        System.out.println(Arrays.toString(hobbys));
        System.out.println("-----------------------");
        // 通过请求转发
        //这里的/代表当前的web应用
        req.getRequestDispatcher("/success.jsp").forward(req,resp);

    }
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
```

index.jsp

```java
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>登录</title>
</head>
<body>
<h1>登录</h1>
<div>
<%--    这里表单表示的意思：一post方式提交表单，提交到我们的login请求--%>
    <form action="${pageContext.request.contextPath}/login" method="post">
        用户名：<input type="text" name="username"><br>
        密码：<input type="password" name="password"><br>
        爱好：
        <input type="checkbox" name="hobbys" value="打篮球">打篮球
        <input type="checkbox" name="hobbys" value="代码">代码
        <input type="checkbox" name="hobbys" value="唱歌">唱歌
        <input type="checkbox" name="hobbys" value="电影">电影
        <br>
        <input type="submit" value="登录">
    </form>
</div>
</body>
</html>
```

## 7、Cookie、Session

### 7.1、会话

**会话**：用户打开一个浏览器，点击了很多超链接，访问多个web资源，关闭浏览器，这个过程可以称之为会话；

**有状态会话**：一个同学来过教室，下次再来教室，我们会知道这个同学，曾经来过，称之为有状态会话；

**一个网站，怎么证明你来过？**

客户端 服务端

1. 服务端给客户端一个 信件，客户端下次访问服务端带上信件就可以了； cookie
2. 服务器登记你来过了，下次你来的时候我来匹配你； seesion

### 7.2、保存会话的两种技术

**cookie**

- 客户端技术 （响应，请求）

**session**

- 服务器技术，利用这个技术，可以保存用户的会话信息？ 我们可以把信息或者数据放在Session中！

常见常见：网站登录之后，你下次不用再登录了，第二次访问直接就上去了！

### 7.3、Cookie

![Cookie](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231059939-1535502904.png)

1. 从请求中拿到cookie信息
2. 服务器响应给客户端cookie

```java
Cookie[] cookies = req.getCookies(); //获得Cookie
cookie.getName(); //获得cookie中的key
cookie.getValue(); //获得cookie中的vlaue
new Cookie("lastLoginTime", System.currentTimeMillis()+""); //新建一个cookie
cookie.setMaxAge(24*60*60); //设置cookie的有效期
resp.addCookie(cookie); //响应给客户端一个cookie
```

**cookie：一般会保存在本地的 用户目录下 appdata；**

一个网站cookie是否存在上限！**聊聊细节问题**

- 一个Cookie只能保存一个信息；
- 一个web站点可以给浏览器发送多个cookie，最多存放20个cookie；
- Cookie大小有限制4kb；
- 300个cookie浏览器上限

**删除Cookie；**

- 不设置有效期，关闭浏览器，自动失效；
- 设置有效期时间为 0 ；

**编码解码：**

```java
URLEncoder.encode("鲁班","utf-8") //编码
URLDecoder.decode(cookie.getValue(),"UTF-8")//解码
```

### 7.4、Session（重点）

![Session](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231059539-451942111.png)

什么是Session：

- 服务器会给每一个用户（浏览器）创建一个Seesion对象；
- 一个Seesion独占一个浏览器，只要浏览器没有关闭，这个Session就存在；
- 用户登录之后，整个网站它都可以访问！–> 保存用户的信息；保存购物车的信息……

Session和cookie的区别：

- Cookie是把用户的数据写给用户的浏览器，浏览器保存 （可以保存多个）
- Session把用户的数据写到用户独占Session中，服务器端保存 （保存重要的信息，减少服务器资源的浪费）
- Session对象由服务创建；

使用场景：

- 保存一个登录用户的信息；
- 购物车信息；
- 在整个网站中经常会使用的数据，我们将它保存在Session中；

使用Session：

```java
package com.shen.servlet;

import com.shen.pojo.Person;

import javax.servlet.ServletException;
import javax.servlet.http.*;
import java.io.IOException;

public class SessionDemo01 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        
        //解决乱码问题
        req.setCharacterEncoding("UTF-8");
        resp.setCharacterEncoding("UTF-8");
        resp.setContentType("text/html;charset=utf-8");
        
        //得到Session
        HttpSession session = req.getSession();
        //给Session中存东西
        session.setAttribute("name",new Person("鲁班",1));
        //获取Session的ID
        String sessionId = session.getId();

        //判断Session是不是新创建
        if (session.isNew()){
            resp.getWriter().write("session创建成功,ID:"+sessionId);
        }else {
            resp.getWriter().write("session以及在服务器中存在了,ID:"+sessionId);
        }

        //Session创建的时候做了什么事情；
//        Cookie cookie = new Cookie("JSESSIONID",sessionId);
//        resp.addCookie(cookie);

    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
//得到Session
HttpSession session = req.getSession();

Person person = (Person) session.getAttribute("name");

System.out.println(person.toString());

HttpSession session = req.getSession();
session.removeAttribute("name");
//手动注销Session
session.invalidate();
```

**会话自动过期：web.xml配置**

```java
<!--设置Session默认的失效时间-->
<session-config>
    <!--15分钟后Session自动失效，以分钟为单位-->
    <session-timeout>15</session-timeout>
</session-config>
```

![session2](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231059199-79485472.png)

## 8、JSP

### 8.1、什么是JSP

Java Server Pages ： Java服务器端页面，也和Servlet一样，用于动态Web技术！

最大的特点：

- 写JSP就像在写HTML
- 区别：
  - HTML只给用户提供静态的数据
  - JSP页面中可以嵌入JAVA代码，为用户提供动态数据；

### 8.2、JSP原理

思路：JSP到底怎么执行的！

- 代码层面没有任何问题

- 服务器内部工作

  tomcat中有一个work目录；

  IDEA中使用Tomcat的会在IDEA的tomcat中生产一个work目录

  ![工作空间](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231058876-37819801.png)

我电脑的地址：

1. 如果未进行修改默认路径，可以到以下路径寻找

```java
C:\Users\<机器用户名>\.IntelliJIdea2018.1\system\tomcat\项目名\work\Catalina\localhost\项目名\org\apache\jsp\
```

1. 2020版本可以尝试到查找

```java
C:\Users\<机器用户名>\AppData\Local\JetBrains\IntelliJIdea2020.2\tomcat\项目名
```

![7](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231058688-94320766.png)

**浏览器向服务器发送请求，不管访问什么资源，其实都是在访问Servlet！**

JSP最终也会被转换成为一个Java类！

**JSP 本质上就是一个Servlet**

```java
//初始化
  public void _jspInit() {
      
  }
//销毁
  public void _jspDestroy() {
  }
//JSPService
  public void _jspService(.HttpServletRequest request,HttpServletResponse response)
```

1. 判断请求
2. 内置一些对象

```java
final javax.servlet.jsp.PageContext pageContext;  //页面上下文
javax.servlet.http.HttpSession session = null;    //session
final javax.servlet.ServletContext application;   //applicationContext
final javax.servlet.ServletConfig config;         //config
javax.servlet.jsp.JspWriter out = null;           //out
final java.lang.Object page = this;               //page：当前
HttpServletRequest request                        //请求
HttpServletResponse response                      //响应
```

1. 输出页面前增加的代码

```java
response.setContentType("text/html");       //设置响应的页面类型
pageContext = _jspxFactory.getPageContext(this, request, response,
       null, true, 8192, true);
_jspx_page_context = pageContext;
application = pageContext.getServletContext();
config = pageContext.getServletConfig();
session = pageContext.getSession();
out = pageContext.getOut();
_jspx_out = out;
```

1. 以上的这些个对象我们可以在JSP页面中直接使用！

![JSP](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231058410-1060139272.png)

在JSP页面中；

只要是 JAVA代码就会原封不动的输出；

如果是HTML代码，就会被转换为：

```java
out.write("<html>\r\n");
```

这样的格式，输出到前端！

### 8.3、JSP基础语法

任何语言都有自己的语法，JAVA中有,。 JSP 作为java技术的一种应用，它拥有一些自己扩充的语法（了解，知道即可！），Java所有语法都支持！

#### JSP表达式 <%= %>

```java
<%--JSP表达式
    作用：用来将程序的输出，输出到客户端
    <%= 变量或者表达式%>
--%>
<%= new java.util.Date()%>
```

#### jsp脚本片段 <% %>

```java
  <%--jsp脚本片段--%>
  <%
    int sum = 0;
    for (int i = 1; i <=100 ; i++) {
      sum+=i;
    }
    out.println("<h1>Sum="+sum+"</h1>");
  %>
```

**脚本片段的再实现**

```java
<%
    int x=10;
    out.print(x);
%>
<p>这是一个JSP文档</p>
<%
    int y=20;
    out.print(y);
%>
<hr>

<%--在代码嵌入HTML元素--%>
<%
    for (int i = 0; i < 5; i++) {
%>
    <h1>Hello,World<%= i%></h1>
<%
    }
%>
```

#### JSP声明 <%! %>

```java
<%--相当于定义的变量或方法都属于全局--%>
<%!
    static {
        System.out.println("Loading Servlet！");
    }
    private int globalVar = 0;

    public void shen(){
        System.out.println("进入了方法shen");
    }

%>
```

JSP声明：会被编译到JSP生成Java的类中！其他的，就会被生成到_jspService方法中！

在JSP，嵌入Java代码即可！

#### 注释

```java
<%--我是JSP注释--%>
<!--我是HTML注释-->
//  我是Java注释
```

JSP的注释，不会在客户端显示，HTML就会！

### 8.4、JSP指令

```java
//定制报错页面信息
<%@page args... %>
<%@page errorPage="error/500.jsp" %>  <%--定制错误页面,配置了就可以不需要配这个了--%>
<%@page isErrorPage="true" %>    <%--显示的声明这是一个错误页面--%>
<%@page pageEncoding="UTF-8" %>		<%--解决乱码--%>
   
    
//拼接页面
<%@include file="..."%>
<%--<%@include 会将两个页面合二为一 "%>--%>
<%@include file="common/header.jsp"%>
<h1>网页主题</h1>
<%@include file="common/footer.jsp"%>
    
<hr>
    
<%--jsp标签(推荐使用这个)
jsp:include：拼接页面，本质还是三个
--%>
<jsp:include page="/common/header.jsp"/>
<h1>网页主题</h1>
<jsp:include page="/common/footer.jsp"/>
    
//引入标签库
<%@ taglib prefix="..." %>
<%--引入JSTL核心标签库，我们才能使用JSTL标签--%>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
```

### 8.5、9大内置对象

- PageContext 存东西
- Request 存东西
- Response
- Session 存东西
- Application 【SerlvetContext】 存东西
- config 【SerlvetConfig】
- out
- page ，不用了解
- exception

##### 数据作用域：

```java
pageContext.setAttribute("name1","鲁班1号"); //保存的数据只在一个页面中有效
request.setAttribute("name2","鲁班2号"); //保存的数据只在一次请求中有效，请求转发会携带这个数据
session.setAttribute("name3","鲁班3号"); //保存的数据只在一次会话中有效，从打开浏览器到关闭浏览器
application.setAttribute("name4","鲁班4号");  //保存的数据只在服务器中有效，从打开服务器到关闭服务器
```

![8](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231058127-2140621803.png)

request：客户端向服务器发送请求，产生的数据，用户看完就没用了，比如：新闻，用户看完没用的！

session：客户端向服务器发送请求，产生的数据，用户用完一会还有用，比如：购物车；

application：客户端向服务器发送请求，产生的数据，一个用户用完了，其他用户还可能使用，比如：聊天数据；

小知识1

```java
<%-- pageContext也可以变成session的作用域，但不推荐 --%>
<%
    pageContext.setAttribute("hello","hello",PageContext.SESSION_SCOPE);
    //上面这一句相当于下面这一句
    session.setAttribute("hello","hello");
%>
```

小知识2

```java
<%
<%--两种方式相同，在前端推荐第一种--%>
    pageContext.forward("/index.jsp");
	request.getRequestDispatcher("/index.jsp").forward(request,response);
%>
```

### 8.6、JSP标签、JSTL标签、EL表达式

```java
<!-- JSTL表达式的依赖 -->
<dependency>
    <groupId>javax.servlet.jsp.jstl</groupId>
    <artifactId>jstl-api</artifactId>
    <version>1.2</version>
</dependency>
<!-- standard标签库 -->
<dependency>
    <groupId>taglibs</groupId>
    <artifactId>standard</artifactId>
    <version>1.1.2</version>
</dependency>
```

EL表达式： ${ }

- **获取数据**
- **执行运算**
- **获取web开发的常用对象**

**JSP标签**

```java
<%-- <jsp:include page=""/>
作用：拼接页面
--%>

<%--
http://localhost:8080/jsptag1.jsp?name=hyd&age=20
--%>
<%--jsp:forward 可以写入数据--%>
<jsp:forward page="/jsptag2.jsp">
    <jsp:param name="name" value="hyd"/>
    <jsp:param name="age" value="20"/>
</jsp:forward>
```

**JSTL表达式**

JSTL标签库的使用就是为了弥补HTML标签的不足；它自定义许多标签，可以供我们使用，标签的功能和Java代码一样！

**格式化标签**

**SQL标签**

**XML 标签**

**核心标签** （掌握部分）

![9](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231057808-572932659.png)

**JSTL标签库使用步骤**

- 引入对应的 taglib
- 使用其中的方法
- **在Tomcat 也需要引入 jstl的包，否则会报错：JSTL解析错误**，**解决方法：在Tomcat lib目录导入standard-1.1.2.jar和jstl-api-1.2.jar的jar包**

##### **c: if**

```java
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<%--引入JSTL核心标签库，我们才能使用JSTL标签--%>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<h4>if测试</h4>
<hr>
<form action="" method="get">
<%--
EL表达式获取表单中的数据
${param.参数名}
--%>
    <input type="text" name="username" value="${param.username}">
    <input type="submit" value="登录">

</form>
<%--判断如果提交的用户名是管理员，则登录成功--%>
<c:if test="${param.username=='admin'}" var="isAdmin">
    <c:out value="管理员欢迎您！" />

</c:if>
<%--自闭合标签--%>
<c:out value="${isAdmin}" />
</body>
</html>
```

**c:choose c:when**

```java
<body>

<%--定义一个变量score，值为85--%>
<c:set var="score" value="55"/>

<c:choose>
    <c:when test="${score>=90}">
        你的成绩为优秀
    </c:when>
    <c:when test="${score>=80}">
        你的成绩为一般
    </c:when>
    <c:when test="${score>=70}">
        你的成绩为良好
    </c:when>
    <c:when test="${score<=60}">
        你的成绩为不及格
    </c:when>
</c:choose>

</body>
```

**c:forEach**

```java
<body>
<%
    ArrayList<String> people = new ArrayList<>();
    people.add(0,"张三");
    people.add(1,"李四");
    people.add(2,"王五");
    people.add(3,"赵六");
    people.add(4,"田六");
    request.setAttribute("list",people);
%>
<%--
var , 每一次遍历出来的变量
items, 要遍历的对象
begin,   哪里开始
end,     到哪里
step,   步长
--%>
<c:forEach var="people" items="${list}">
    <c:out value="${people}"/> <br>
</c:forEach>

<hr>

<c:forEach var="people" items="${list}" begin="1" end="3" step="1" >
    <c:out value="${people}"/> <br>
</c:forEach>
</body>
```

## 9、JavaBean

实体类

JavaBean有特定的写法：

- 必须要有一个无参构造
- 属性必须私有化
- 必须有对应的get/set方法；

一般用来和数据库的字段做映射 ORM；

ORM ：对象关系映射

- 表—>类
- 字段–>属性
- 行记录---->对象

**people表**

| id   | name    | age  | address  |
| ---- | ------- | ---- | -------- |
| 1    | 鲁班1号 | 20   | 西安     |
| 2    | 鲁班2号 | 18   | 北上广   |
| 3    | 鲁班3号 | 19   | 广东深圳 |

```cpp
class People{
    private int id;
    private String name;
    private int age;
    private String address;
}
//使用的时候new一下对象就可以了
class A{
    new People(1,"鲁班1号",3，"西安");
    new People(2,"鲁班2号",3，"北上广");
    new People(3,"鲁班3号",3，"广东深圳");
}
```

练习：

实体类

```java
package com.shem.entity;

//实体类，我们一般是和数据库中的表结构一一对应！
public class People {
    private int id;
    private String name;
    private int age;
    private String address;
    
    public People(int id, String name, int age, String address) {
        this.id = id;
        this.name = name;
        this.age = age;
        this.address = address;
    }
    public People() {
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

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getAddress() {
        return address;
    }

    public void setAddress(String address) {
        this.address = address;
    }

    @Override
    public String toString() {
        return "People{" +
                "id=" + id +
                ", name='" + name + '\'' +
                ", age=" + age +
                ", address='" + address + '\'' +
                '}';
    }
}

折叠 
```

javabean.jsp

```java
<%@ page import="com.shem.entity.People" %>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
</head>
<body>

<%
//    People people = new People();
//    people.setId(1);
//    people.setName("张三");
//    people.setAge(19);
//    people.setAddress("广西");
%>
<jsp:useBean id="people" class="com.shem.entity.People" scope="page"/>
<jsp:setProperty name="people" property="address" value="广西"/>
<jsp:setProperty name="people" property="id" value="1"/>
<jsp:setProperty name="people" property="age" value="19"/>
<jsp:setProperty name="people" property="name" value="张三"/>

姓名：<jsp:getProperty name="people" property="name"/>
id：<jsp:getProperty name="people" property="id"/>
年龄：<jsp:getProperty name="people" property="age"/>
地址：<jsp:getProperty name="people" property="address"/>
</body>
</html>
```

## 10、MVC三层架构

- 什么是MVC： Model view Controller 模型、视图、控制器

### 10.1、以前的架构

![mvc1](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231057475-2104784461.png)

用户直接访问控制层，控制层就可以直接操作数据库；

```java
servlet--CRUD-->数据库
弊端：程序十分臃肿，不利于维护  
servlet的代码中：处理请求、响应、视图跳转、处理JDBC、处理业务代码、处理逻辑代码

架构：没有什么是加一层解决不了的！
程序猿调用
↑
JDBC （实现该接口）
↑
Mysql Oracle SqlServer ....（不同厂商）
```

### 10.2、MVC三层架构

![mvc2](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231056966-350016665.png)

Model

- 业务处理 ：业务逻辑（Service）
- 数据持久层：CRUD （Dao - 数据持久化对象）

View

- 展示数据
- 提供链接发起Servlet请求 （a，form，img…）

Controller （Servlet）

- 接收用户的请求 ：（req：请求参数、Session信息….）
- 交给业务层处理对应的代码
- 控制视图的跳转

```java
登录--->接收用户的登录请求--->处理用户的请求（获取用户登录的参数，username，password）---->交给业务层处理登录业务（判断用户名密码是否正确：事务）--->Dao层查询用户名和密码是否正确-->数据库
```

## 11、Filter （重点）

比如 Shiro安全框架技术就是用Filter来实现的

Filter：过滤器 ，用来过滤网站的数据；

- 处理中文乱码
- 登录验证….

（比如用来过滤网上骂人的话，我***我自己 0-0）

![10](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231056623-402351679.png)

Filter开发步骤：

1. 导包
2. 编写过滤器
   1. 导包不要错 **（注意）**

![12](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231056336-1254848072.png)

实现Filter接口，重写对应的方法即可😁

```java
package com.shen.filter;

import javax.servlet.*;
import java.io.IOException;

public class CharacterEncodingFilter implements Filter {
    //初始化:web服务器启动，就已经初始化了，随时等待过滤对象出现！
    @Override
    public void init(FilterConfig filterConfig) throws ServletException {
        System.out.println("CharacterEncodingFilter初始化");
    }
    //chain :链
    /*
    1.过滤器中所有代码，在过滤特定请求的时候都会执行
    2.必须要让过滤器继续同行
     */
    @Override
    public void doFilter(ServletRequest request, ServletResponse response, FilterChain filterChain) throws IOException, ServletException {
        request.setCharacterEncoding("utf-8");
        response.setCharacterEncoding("utf-8");
        response.setContentType("text/html;charset=UTF-8");

        System.out.println("CharacterEncodingFilter执行前....");
        filterChain.doFilter(request,response);//让我们的请求继续走，如果不写，程序到这里就被拦截停止了
        System.out.println("CharacterEncodingFilter执行后....");
    }
    //销毁：web服务器关闭的时候，过滤器会被销毁
    @Override
    public void destroy() {
        System.out.println("CharacterEncodingFilter销毁");
    }
}
```

1. 在web.xml中配置 Filter

```java
    <filter>
        <filter-name>CharacterEncodingFilter</filter-name>
        <filter-class>com.shen.filter.CharacterEncodingFilter</filter-class>
    </filter>
    <filter-mapping>
        <filter-name>CharacterEncodingFilter</filter-name>
        <!--只要是servlet的任何请求，会经过这个过滤器-->
        <url-pattern>/servlet/*</url-pattern>
        <!--<url-pattern>/*</url-pattern>-->
    </filter-mapping>
```

## 12、监听器

实现一个监听器的接口；（有n种监听器）

1. 编写一个监听器

   实现监听器的接口…

```java
package com.shen.listener;

import javax.servlet.ServletContext;
import javax.servlet.http.HttpSessionEvent;
import javax.servlet.http.HttpSessionListener;

//统计网站在线人数：统计session
public class OnlineCountListener implements HttpSessionListener {
    //创建session监听:看你的一举一动
    //一旦创建session就会触发这个事件！
    @Override
    public void sessionCreated(HttpSessionEvent se) {
        System.out.println(se.getSession().getId());
        ServletContext ctx = se.getSession().getServletContext();
        Integer onlineCount = (Integer) ctx.getAttribute("OnlineCount");
        if (onlineCount==null){
            onlineCount=new Integer(1);
        }else{
            int count = onlineCount.intValue();
            onlineCount = new Integer(count+1);
        }
        ctx.setAttribute("OnlineCount",onlineCount);
    }
    //销毁session监听
    //一旦销毁session就会触发这个事件！
    @Override
    public void sessionDestroyed(HttpSessionEvent se) {
        ServletContext ctx = se.getSession().getServletContext();
        Integer onlineCount = (Integer) ctx.getAttribute("OnlineCount");
        if (onlineCount==null){
            onlineCount=new Integer(0);
        }else{
            int count = onlineCount.intValue();
            onlineCount = new Integer(count-1);
        }
        ctx.setAttribute("OnlineCount",onlineCount);
    }
    /*
    Session销毁：
    1. 手动销毁     getSession().invalidate();
    2. 自动销毁
    */
}
```

1. web.xml中注册监听器

```java
    <!--注册监听器-->
    <listener>
        <listener-class>com.shen.listener.OnlineCountListener</listener-class>
    </listener>
```

1. 看情况是否使用！

## 13、过滤器、监听器常见应用

**监听器：GUI编程中经常使用；**

```java
package com.shen.listener;

import java.awt.*;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;

public class TestPanel {
    public static void main(String[] args) {
        Frame frame = new Frame("中秋节快乐"); //新建一个窗体
        Panel panel = new Panel(null); //面板
        frame.setLayout(null);//设置窗体的布局

        frame.setBounds(300,300,500,500);
        frame.setBackground(new Color(0,0,255));//设置背景颜色
        panel.setBounds(50,50,300,300);
        panel.setBackground(new Color(0,255,0));//设置背景颜色
        frame.add(panel);

        frame.setVisible(true);

        //监听事件：监听关闭事件
        frame.addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
                System.exit(0);
            }
        });
    }
}
```

#### Filter过滤器实现用户登录功能😀

用户登录之后才能进入主页！用户注销后就不能进入主页了！

1. 用户登录之后，向Sesison中放入用户的数据
2. 进入主页的时候要判断用户是否已经登录；要求：在过滤器中实现！

```java
HttpServletRequest request = (HttpServletRequest) req;
HttpServletResponse response = (HttpServletResponse) resp;

if (request.getSession().getAttribute(Constant.USER_SESSION)==null){
    response.sendRedirect("/error.jsp");
}

chain.doFilter(request,response);
```

##### **练习登录功能：**

登录界面login.jsp：

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
</head>
<body>

<h1>登录</h1>
<form action="/servlet/login" method="post">
    账号：<input type="text" name="username"><br>
    密码：<input type="password" name="password"><br>
    <input type="submit" value="登录">
</form>
</body>
</html>
```

错误页面error.jsp

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<h1>错误</h1>
<h3>没有权限，用户名或密码错误</h3>
<a href="/login.jsp">返回登录页面</a>
</body>
</html>
```

主页success.jsp

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<h1>主页</h1>
<p><a href="/servlet/logout">注销</a></p>
</body>
</html>
```

定制一个util类放常量😊

```java
package com.shen.util;
public class Constant {
    public final static String USER_SESSION ="USER_SESSION";
}
```

编写LoginServlet是否能登录

```java
package com.shen.servlet;
import com.shen.util.Constant;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

public class LoginServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //获取前段请求的参数
        String username = req.getParameter("username");
        String password = req.getParameter("password");
        if (username.equals("admin")&&password.equals("123")){//登录成功
            req.getSession().setAttribute(Constant.USER_SESSION,req.getSession().getId());
            resp.sendRedirect("/sys/success.jsp");
        }else {//登录失败
            resp.sendRedirect("/error.jsp");
        }
    }
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
```

编写Logout退出登录功能

```java
package com.shen.servlet;
import com.shen.util.Constant;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

public class LogoutServlet extends HttpServlet {

    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        Object user_session = req.getSession().getAttribute(Constant.USER_SESSION);
        if (user_session!=null){
            req.getSession().removeAttribute(Constant.USER_SESSION);
            resp.sendRedirect("/login.jsp");
        }else {
            resp.sendRedirect("/login.jsp");
        }
    }
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
```

编写过滤器，让那些没登录就输入网址的也进不去主页面

```java
package com.shen.filter;
import com.shen.util.Constant;
import javax.servlet.*;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

public class SysFilter implements Filter {
    @Override
    public void init(FilterConfig filterConfig) throws ServletException {
    }
    @Override
    public void doFilter(ServletRequest req, ServletResponse resp, FilterChain chain) throws IOException, ServletException {
    // 这里是ServletRequest取不到Session,我们使用的是HttpServletRequest可以取Session,所以我们需要转一下
        HttpServletRequest request=(HttpServletRequest) req;
        HttpServletResponse response=(HttpServletResponse) resp;
        Object user_session = request.getSession().getAttribute(Constant.USER_SESSION);
        if(user_session==null){
            response.sendRedirect("/error.jsp");
        }
        chain.doFilter(req,resp);
    }
    @Override
    public void destroy() {
    }
}
```

注册web.xml,个人建议写好一个Servlet就先注册一个web.xml，不然老是忘记😂

```java
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">
             
    <!--登录-->
    <servlet>
        <servlet-name>loginServlet</servlet-name>
        <servlet-class>com.shen.servlet.LoginServlet</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>loginServlet</servlet-name>
        <url-pattern>/servlet/login</url-pattern>
    </servlet-mapping>
    <!--退出登录-->
    <servlet>
        <servlet-name>logoutServlet</servlet-name>
        <servlet-class>com.shen.servlet.LogoutServlet</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>logoutServlet</servlet-name>
        <url-pattern>/servlet/logout</url-pattern>
    </servlet-mapping>
    <!-- 过滤器-->
    <filter>
        <filter-name>SysFilter</filter-name>
        <filter-class>com.shen.filter.SysFilter</filter-class>
    </filter>
    <filter-mapping>
        <filter-name>SysFilter</filter-name>
        <url-pattern>/sys/*</url-pattern>
    </filter-mapping>
    
    
    </web-app>
```

我的web目录文件是这样😁

![14](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231056086-184340382.png)

## 14、JDBC

什么是JDBC ： Java连接数据库！

![jdbc01](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231055810-935855758.png)

需要jar包的支持：

- java.sql
- javax.sql
- mysql-conneter-java… 连接驱动（必须要导入）

**实验环境搭建**

```java
CREATE TABLE users(
    id INT PRIMARY KEY,
    `name` VARCHAR(40),
    `password` VARCHAR(40),
    email VARCHAR(60),
    birthday DATE
);

INSERT INTO users(id,`name`,`password`,email,birthday)
VALUES(1,'张三','123','zs@qq.com','2000-01-01');
INSERT INTO users(id,`name`,`password`,email,birthday)
VALUES(2,'李四','123','ls@qq.com','2000-01-01');
INSERT INTO users(id,`name`,`password`,email,birthday)
VALUES(3,'王五','123','ww@qq.com','2000-01-01');

SELECT	* FROM users;
```

导入数据库依赖

注意：依赖这里可能要看数据库版本，我学习使用5.1.47一直报错，**我的mysql是5.7.36**，我换了5.1.36的依赖就可以跑了

```java
<!--mysql的驱动-->
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>5.1.36</version>
</dependency>
```

IDEA中连接数据库：

![jdbc2](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231055564-1981213979.png)

**JDBC 固定步骤：**

1. 加载驱动
2. 连接数据库,代表数据库
3. 向数据库发送SQL的对象Statement : CRUD
4. 编写SQL （根据业务，不同的SQL）
5. 执行SQL
6. 关闭连接（先开的后关）

**查询：**

```java
package com.shen.Test;

import java.sql.*;

public class TestJdbc {
    public static void main(String[] args) throws ClassNotFoundException, SQLException {
        //配置信息
        //?useUnicode=true&characterEncoding=utf-8" 解决中文乱码
        String url="jdbc:mysql://localhost:3306/jdbc?characterEncoding=UTF8&autoReconnect=true";
        String username = "root";
        String password ="123456";

        //1.加载驱动
        Class.forName("com.mysql.jdbc.Driver");
        //2.连接数据库,代表数据库
            Connection connection = DriverManager.getConnection(url, username, password);
            //3.向数据库发送SQL的对象Statement，prepareStatement：CRUD
            Statement statement = connection.createStatement();
            //4.编写SQL
            String sql = "select * from users";
            //5.执行查询SQL,返回一个ResultSet结果集
            ResultSet rs = statement.executeQuery(sql);
            while (rs.next()){
                System.out.println("id="+rs.getObject("id"));
                System.out.println("name="+rs.getObject("name"));
                System.out.println("password="+rs.getObject("password"));
                System.out.println("email="+rs.getObject("email"));
                System.out.println("birthday="+rs.getObject("birthday"));
            }
            //6. 关闭连接 释放资源（一定要做）先开后关
            rs.close();
            statement.close();
            connection.close();
    }
}
```

**增删改：**

```java
package com.shen.Test;

import java.sql.*;

public class TestJdbc2 {
    public static void main(String[] args) throws ClassNotFoundException, SQLException {
        //配置信息
        //?useUnicode=true&characterEncoding=utf-8" 解决中文乱码
        String url="jdbc:mysql://localhost:3306/jdbc?characterEncoding=UTF8&autoReconnect=true";
        String username = "root";
        String password ="123456";

        //1.加载驱动
        Class.forName("com.mysql.jdbc.Driver");
        //2.连接数据库,代表数据库
        Connection connection = DriverManager.getConnection(url, username, password);
        //3.向数据库发送SQL的对象Statement：CRUD
        Statement statement = connection.createStatement();
        //4.编写SQL
        //String sql = "INSERT INTO users(id,`name`,`password`,email,birthday)"; //添加
        //String sql = "UPDATE users SET `name`='李柳青' WHERE id =1;"; //修改
        String sql = "delete from users where id = 3"; //删除
        //5.执行查询SQL,返回一个ResultSet结果集

        //受影响的行数，增删改都使用executeUpdate即可
        int i = statement.executeUpdate(sql);

        System.out.println("受影响的行为："+i);

        //6. 关闭连接 释放资源（一定要做）先开后关
        statement.close();
        connection.close();
    }
}
```

**预编译SQL**，建议使用这个,prepareStatement可以防止sql注入

```java
package com.shen.Test;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.util.Date;

public class TestJdbc3 {
    public static void main(String[] args) throws Exception {
        //配置信息
        //useUnicode=true&characterEncoding=utf-8 解决中文乱码
        String url="jdbc:mysql://localhost:3306/jdbc?useUnicode=true&characterEncoding=utf-8";
        String username = "root";
        String password = "123456";

        //1.加载驱动
        Class.forName("com.mysql.jdbc.Driver");
        //2.连接数据库,代表数据库
        Connection connection = DriverManager.getConnection(url, username, password);

        //3.编写SQL
        String sql = "insert into  users(id, name, password, email, birthday) values (?,?,?,?,?);";

        //4.预编译
        PreparedStatement preparedStatement = connection.prepareStatement(sql);

        preparedStatement.setInt(1,7);//给第一个占位符？ 的值赋值为7；
        preparedStatement.setString(2,"鲁班七号");//给第二个占位符？ 的值赋值为鲁班七号；
        preparedStatement.setString(3,"999");//给第三个占位符？ 的值赋值为999；
        preparedStatement.setString(4,"10086@qq.com");//给第四个占位符？ 的值赋值为10086@qq.com；
        preparedStatement.setDate(5, new java.sql.Date(new Date().getTime()));//给第五个占位符？ 的值赋值为new java.sql.Date(new Date().getTime())；

        //5.执行SQL
        int i = preparedStatement.executeUpdate();

        if (i>0){
            System.out.println("插入成功");
        }

        //6.关闭连接，释放资源（一定要做） 先开后关
        preparedStatement.close();
        connection.close();
    }
}
```

**事务**

要么都成功，要么都失败！

ACID原则：保证数据的安全。

```java
开启事务
事务提交  commit()
事务回滚  rollback()
关闭事务

转账：
A:1000
B:1000
   
A(900)   --100-->   B(1100) 
```

**Junit单元测试**

依赖

```java
<!--单元测试-->
<dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
    <version>4.12</version>
</dependency>
```

简单使用

@Test注解只有在方法上有效，只要加了这个注解的方法，就可以直接运行了

```java
@Test
public void test(){
    System.out.println("Hello");
}
```

成功的时候是绿色的打钩

![Jdbc03](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231055360-1998707357.png)

失败的时候是红色感叹号：

![Jdbc04](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231055025-439032637.png)

**搭建一个环境**

```java
CREATE TABLE account(
   id INT PRIMARY KEY AUTO_INCREMENT,
   `name` VARCHAR(40),
   money FLOAT
);

INSERT INTO account(`name`,money) VALUES('A',1000);
INSERT INTO account(`name`,money) VALUES('B',1000);
INSERT INTO account(`name`,money) VALUES('C',1000);
package com.shen.Test;

import org.junit.Test;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class TestJdbc4 {
    @Test
    public void Test(){
        //配置信息
        //?useUnicode=true&characterEncoding=utf-8" 解决中文乱码
        String url="jdbc:mysql://localhost:3306/jdbc?characterEncoding=UTF8&autoReconnect=true";
        String username = "root";
        String password ="123456";
        Connection connection=null;
        //1.加载驱动
        try {
            Class.forName("com.mysql.jdbc.Driver");

            //2.连接数据库,代表数据库
            connection = DriverManager.getConnection(url, username, password);
            //3.通知数据库开启事务,false开启
            connection.setAutoCommit(false);
            String sql ="update account set money =money-100 where name='A'";
            connection.prepareStatement(sql).executeUpdate();
            //制造错误
//            int i =1/0;
            String sql2 ="update account set money =money+100 where name='B'";
            connection.prepareStatement(sql2).executeUpdate();
            connection.commit();//以上两条SQL都执行成功了，就提交事务！
            System.out.println("success");
        } catch (Exception e) {
            try {
                //如果出现异常，就通知数据库回滚事务
                connection.rollback();
            } catch (SQLException throwables) {
                throwables.printStackTrace();
            }
            e.printStackTrace();
        }finally {
            try {
                connection.close();
            } catch (SQLException throwables) {
                throwables.printStackTrace();
            }
        }
    }
}
```

#### **额，这个往下就是拿项目来练手了，可以找两个项目来练手，或者跟狂神老师一起敲他的SMBMS(超市订单管理系统)**😊

## 15、SMBMS(超市订单管理系统)

![项目01](https://img2022.cnblogs.com/blog/2467723/202203/2467723-20220329231054651-1195632259.png)

# 16.MD5加密算法

```java
/**
 * Description: MD5加密的公共方法，传入密码，返回加密后的密码<br/>
 * @author liYan
 * @param pwd
 * @return
 */
public static String MD5Tools(String pwd) {
    String[] digitals = { "0", "1", "2", "3", "4", "5", "6", "7", "8", "9", "a", "b", "c", "d", "e", "f" };
    String result = "";
    try {
        MessageDigest md5 = MessageDigest.getInstance("MD5");
        byte[] bytes = md5.digest(pwd.getBytes("utf-8"));
        for (int i = 0; i < bytes.length; i++) {
            int num = bytes[i];
            if (num < 0) {
                num = num + 255;
            }
            int j = num / 16;
            int k = num % 16;
            result = digitals[j] + digitals[k] + result;
        }
    } catch (Exception e) {
        e.printStackTrace();
    }
    return result;
}
```