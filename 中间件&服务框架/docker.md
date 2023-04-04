# 1.初始Docker

![image-20230316105135148](typora图片/image-20230316105135148.png)

![image-20230316105358594](typora图片/image-20230316105358594.png)



## 安装Docker

```shell
# 1、yum 包更新到最新 
yum update
# 2、安装需要的软件包， yum-util 提供yum-config-manager功能，另外两个是devicemapper驱动依赖的 
yum install -y yum-utils device-mapper-persistent-data lvm2
# 3、 设置yum源
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
# 4、 安装docker，出现输入的界面都按 y 
yum install -y docker-ce
# 5、 查看docker版本，验证是否验证成功
docker -v
```

当发生如下报错

```shell
Error: Failed to download metadata for repo 'appstream': Cannot prepare internal mirrorlist: No URLs in mirrorlist
```

依次执行  （这个是发生错误了之后在执行）

```shell
cd /etc/yum.repos.d/
sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
yum makecache
yum update -y
```

## Docker架构

![image-20230316110655278](typora图片/image-20230316110655278.png)

## 配置Docker镜像加速器

![image-20230316110710674](typora图片/image-20230316110710674.png)

登录阿里云

![image-20230316110736423](typora图片/image-20230316110736423.png)

![image-20230316110752122](typora图片/image-20230316110752122.png)

执行

![image-20230316110815901](typora图片/image-20230316110815901.png)

查看是否配置成功

![image-20230316110832033](typora图片/image-20230316110832033.png)

# Docker命令

![image-20230316110853053](typora图片/image-20230316110853053.png)

## Docker进程相关命令

![image-20230316110910472](typora图片/image-20230316110910472.png)

### 启动docker服务

```shell
systemctl start docker
```

### 停止docker服务

```shell
systemctl stop docker
```

### 重启docker服务

```shell
systemctl restart docker
```

### 查看docker服务状态

```shell
systemctl status docker
```

### 设置开机启动docker服务

```shell
systemctl enable docker
```

演示

![image-20230316110934079](typora图片/image-20230316110934079.png)

![image-20230316110947965](typora图片/image-20230316110947965.png)

## Docker镜像相关命令

![image-20230316111001412](typora图片/image-20230316111001412.png)

### 查看镜像

查看本地所有的镜像

```shell
docker images
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
第一次使用这个就只显示这个
docker images –q # 查看所用镜像的id
```

### 搜索镜像

从网络中查找需要的镜像

```shell
docker search 镜像名称
```

### 拉取镜像

从Docker仓库下载镜像到本地，镜像名称格式为 名称:版本号，如果版本号不指定则是最新的版本。 如果不知道镜像版本，可以去docker hub 搜索对应镜像查看。

```shell
docker pull 镜像名称
docker pull 镜像名称 : 加版本号
```

### 删除镜像

删除本地镜像

![image-20230316144410574](typora图片/image-20230316144410574.png)

```shell
docker rmi 镜像id # 删除指定本地镜像
docker rmi `docker images -q` # 删除所有本地镜像
```

演示

查看指定镜像版本

```shell
HTTP
https://hub.docker.com
```

![image-20230316111023373](typora图片/image-20230316111023373.png)

![image-20230316111037998](typora图片/image-20230316111037998.png)

![image-20230316111057718](typora图片/image-20230316111057718.png)

## Docker容器相关命令

![image-20230316111111600](typora图片/image-20230316111111600.png)

### 查看容器

```shell

docker ps # 查看正在运行的容器 
docker ps –a # 查看所有容器
```

### 创建并启动容器

```shell
BASH
docker run 参数
docker run -id --name=容器名称 使用的镜像:镜像的版本 

docker run -d -p 8080:8080 --name tomcatqaq tomcat
```

参数说明:

- `-i`:保持容器运行。通常与 -t 同时使用。加入it这两个参数后，容器创建后自动进入容器中，退出容器后，容器自动关闭。
- `-t`:为容器重新分配一个伪输入终端，通常与 -i 同时使用。
- `-d`:以守护(后台)模式运行容器。创建一个容器在后台运行，需要使用docker exec 进入容器。退出后，容器不会关闭。
- `-it `创建的容器一般称为交互式容器，-id 创建的容器一般称为守护式容器
- `--name`:为创建的容器命名。

![image-20230403143810095](typora图片/image-20230403143810095.png)



演示

![image-20230316111133508](typora图片/image-20230316111133508.png)

以后台方式运行容器，并进入容器

```shell
BASH
[root@hecs-33111 ~]# docker run -id --name=c2 redis:5.0 /bin/bash
这个是在后台创建
3842cee27f9b97fa7fb512aa53f835351f38860ffd5a4dc0e19b9e36d7aadf54
[root@hecs-33111 ~]# docker exec -it c2 /bin/bash
root@3842cee27f9b:/data# 
```

![image-20230316111153604](typora图片/image-20230316111153604.png)

### 进入容器

```shell
docker exec 参数 # 退出容器，容器不会关闭
```

![image-20230320154622775](typora图片/image-20230320154622775.png)

### 停止容器

```shell
docker stop 容器名称
```

### 启动容器

```shell
docker start 容器名称
```

### 删除容器

如果容器是运行状态则删除失败，需要停止容器才能删除

```shell
docker rm 容器名称
docker rm '容器id'//删除指定容器
docker rm 'docker ps -aq'//删除所有容器
```

### 查看容器信息

```shell
docker inspect 容器名称
```

演示

![image-20230316111210268](typora图片/image-20230316111210268.png)

# Docker容器的数据卷

![image-20230316111223240](typora图片/image-20230316111223240.png)

## 数据卷的概念

![image-20230316111235722](typora图片/image-20230316111235722.png)

![image-20230316111254658](typora图片/image-20230316111254658.png)



## 配置数据卷

```shell
BASH
docker run ... –v 宿主机目录(文件):容器内目录(文件) ...
```

![image-20230316111309791](typora图片/image-20230316111309791.png)

演示

创建centos容器

```shell
BASH
docker run -it --name=c3 -v /root/data:/root/data_container centos /bin/bash
```

观察创建的目录

![image-20230316111328928](typora图片/image-20230316111328928.png)

观察到宿主机创建的数据卷

![image-20230316111346257](typora图片/image-20230316111346257.png)

在宿主机data目录下创建文件

![image-20230316111359027](typora图片/image-20230316111359027.png)

观察容器内的同步情况

![image-20230316111412167](typora图片/image-20230316111412167.png)

在容器内修改文件

![image-20230316111422698](typora图片/image-20230316111422698.png)

观察宿主机内同步情况

![image-20230316111434857](typora图片/image-20230316111434857.png)

退出并关闭centos容器

![image-20230316111447243](typora图片/image-20230316111447243.png)

观察宿主机数据卷是否还在

![image-20230316111459239](typora图片/image-20230316111459239.png)

数据卷未丢失

重启启动容器

![image-20230316111515137](typora图片/image-20230316111515137.png)

一个容器内同步多个数据卷

```shell
BASH
docker run -it --name=c2 -v ~/data2:/root/data2 -v ~/data3:/root/data3 centos
```

容器内

![image-20230316111528314](typora图片/image-20230316111528314.png)

宿主机

![image-20230316111540050](typora图片/image-20230316111540050.png)

容器与容器之间的同步

创建两个容器c1,c2

[![image-20221119155040681](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221119155040681.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221119155040681.png)

进入容器c1并创建文件

[![image-20221119155244415](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221119155244415.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221119155244415.png)

进入容器c2观察同步情况

[![image-20221119155402217](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221119155402217.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221119155402217.png)

## 数据卷容器

[![image-20221119155535372](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221119155535372.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221119155535372.png)

### **配置数据卷容器**

1. 创建启动c3数据卷容器，使用 –v 参数 设置数据卷

```shell
docker run –it --name=c3 –v /volume centos:7 /bin/bash
```

1. 创建启动 c1 c2 容器，使用 –-volumes-from 参数 设置数据卷

```shell
docker run –it --name=c1 --volumes-from c3 centos:7 /bin/bash 
docker run –it --name=c2 --volumes-from c3 centos:7 /bin/bash
```

演示

创建数据卷容器c3和两个测试同步容器

```shell
PLAINTEXT
[root@hecs-33111 data]# docker run -id --name=c3 -v /volume centos
5a43ebf4f327441ae82f9fdebe640f88125f03e35ddfd34e5a7e21982f39a48c
[root@hecs-33111 data]# docker run -id --name=c1 --volumes-from c3 centos
e2ceb7739b1f57cd5b76c2c155b23fe5d1dedb29b9b1fc80c6e7ac50f1dd9eaf
[root@hecs-33111 data]# docker run -id --name=c2 --volumes-from c3 centos
f8cc38cff52549d6be3e3604d679b1556fda4c5ad1641a1cee4bde7fc63da9d4
```

在c1容器内修改数据

```shell
PLAINTEXT
[root@hecs-33111 data]# docker exec -it c1 /bin/bash
[root@e2ceb7739b1f /]# cd volume/
[root@e2ceb7739b1f volume]# ls
[root@e2ceb7739b1f volume]# 
[root@e2ceb7739b1f volume]# touch test.txt
[root@e2ceb7739b1f volume]# 
[root@e2ceb7739b1f volume]# ls
test.txt
```

观察c2容器数据变化,数据已经成功同步

[![image-20221119173008858](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221119173008858.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221119173008858.png)

[![image-20221119203158768](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221119203158768.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221119203158768.png)

# Docker应用部署

## MsSQL部署

[![image-20221119203218070](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221119203218070.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221119203218070.png)

[![image-20221119203229479](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221119203229479.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221119203229479.png)

[![image-20221119203345769](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221119203345769.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221119203345769.png)

### 搜索mysql镜像

```shell
SHELL
docker search mysql
```

[![image-20221119204432501](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221119204432501.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221119204432501.png)

### 拉取mysql镜像

```shell
SHELL
docker pull mysql:5.6
```

[![image-20221119204625163](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221119204625163.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221119204625163.png)

### 创建容器，设置端口映射、目录映射

```shell
# 在/root目录下创建mysql目录用于存储mysql数据信息
mkdir ~/mysql
cd ~/mysql
SHELL
docker run -id \
-p 3307:3306 \
--name=c_mysql \
-v $PWD/conf:/etc/mysql/conf.d \
-v $PWD/logs:/logs \
-v $PWD/data:/var/lib/mysql \
-e MYSQL_ROOT_PASSWORD=123456 \
mysql:5.6

在进去到数据库
mysql -uroot -p 密码
```

- 参数说明：
  - **-p 3307:3306**：将容器的 3306 端口映射到宿主机的 3307 端口。
  - **-v $PWD/conf:/etc/mysql/conf.d**：将主机当前目录下的 conf/my.cnf 挂载到容器的 /etc/mysql/my.cnf。配置目录
  - **-v $PWD/logs:/logs**：将主机当前目录下的 logs 目录挂载到容器的 /logs。日志目录
  - **-v $PWD/data:/var/lib/mysql** ：将主机当前目录下的data目录挂载到容器的 /var/lib/mysql 。数据目录
  - **-e MYSQL_ROOT_PASSWORD=123456：**初始化 root 用户的密码。

[![image-20221119204847664](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221119204847664.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221119204847664.png)

[![image-20221119205037008](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221119205037008.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221119205037008.png)

## Tomcat部署

[![image-20221119213329980](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221119213329980.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221119213329980.png)

### 搜索tomcat镜像

```shell
SHELL
docker search tomcat
```

### 拉取tomcat镜像

```shell
SHELL
docker pull tomcat
```

[![image-20221119214222638](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221119214222638.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221119214222638.png)

### 创建容器，设置端口映射、目录映射

```shell
SHELL
# 在/root目录下创建tomcat目录用于存储tomcat数据信息
mkdir ~/tomcat
cd ~/tomcat
SHELL
docker run -id --name=c_tomcat \
-p 8080:8080 \
-v $PWD:/usr/local/tomcat/webapps \
tomcat 



进去tomcat容器
docker exec -it 容器名称 /bin/bash
```

- 参数说明：

  - **-p 8080:8080：**将容器的8080端口映射到主机的8080端口

    **-v $PWD:/usr/local/tomcat/webapps：**将主机中当前目录挂载到容器的webapps

[![image-20221119214349524](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221119214349524.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221119214349524.png)

### 使用外部机器访问tomcat

## Nginx部署

[![image-20221119214456006](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221119214456006.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221119214456006.png)

### 搜索nginx镜像

```shell
SHELL
docker search nginx
```

### 拉取nginx镜像

```shell
SHELL
docker pull nginx
```

### 创建容器，设置端口映射、目录映射

```shell
SHELL
# 在/root目录下创建nginx目录用于存储nginx数据信息
mkdir ~/nginx
cd ~/nginx
mkdir conf
cd conf
# 在~/nginx/conf/下创建nginx.conf文件,粘贴下面内容
vim nginx.conf
SHELL
user  nginx;
worker_processes  1;

error_log  /var/log/nginx/error.log warn;
pid        /var/run/nginx.pid;


events {
    worker_connections  1024;
}


http {
    include       /etc/nginx/mime.types;
    default_type  application/octet-stream;

    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';

    access_log  /var/log/nginx/access.log  main;

    sendfile        on;
    #tcp_nopush     on;

    keepalive_timeout  65;

    #gzip  on;

    include /etc/nginx/conf.d/*.conf;
}
SHELL
docker run -id --name=c_nginx \
-p 80:80 \
-v $PWD/conf/nginx.conf:/etc/nginx/nginx.conf \
-v $PWD/logs:/var/log/nginx \
-v $PWD/html:/usr/share/nginx/html \
nginx
```

- 参数说明：
  - **-p 80:80**：将容器的 80端口映射到宿主机的 80 端口。
  - **-v $PWD/conf/nginx.conf:/etc/nginx/nginx.conf**：将主机当前目录下的 /conf/nginx.conf 挂载到容器的 :/etc/nginx/nginx.conf。配置目录
  - **-v $PWD/logs:/var/log/nginx**：将主机当前目录下的 logs 目录挂载到容器的/var/log/nginx。日志目录

### 使用外部机器访问nginx

[![1573652396669](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/1573652396669.png)](https://weishao-996.github.io/img/黑马程序员-Docker/1573652396669.png)

## Redis部署

[![image-20221119215440719](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221119215440719.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221119215440719.png)

### 搜索redis镜像

```shell
SHELL
docker search redis
```

### 拉取redis镜像

```shell
SHELL
docker pull redis:5.0
```

### 创建容器，设置端口映射

```shell
SHELL
docker run -id --name=c_redis -p 6379:6379 redis:5.0
```

[![image-20221119221014974](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221119221014974.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221119221014974.png)

### 使用外部机器连接redis

```shell
SHELL
./redis-cli.exe -h 192.168.149.135 -p 6379
```

# Dockerfile

[![image-20221120130715968](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120130715968.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120130715968.png)

## Docker镜像原理

[![image-20221120130749819](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120130749819.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120130749819.png)

[![image-20221120131008869](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120131008869.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120131008869.png)

[![image-20221120131751168](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120131751168.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120131751168.png)

![image-20230317112525780](typora图片/image-20230317112525780.png)

## **镜像制作**

[![image-20221120132440129](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120132440129.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120132440129.png)

演示

[![image-20221120133459889](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120133459889.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120133459889.png)

[![image-20221120133726220](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120133726220.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120133726220.png)

[![image-20221120133948978](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120133948978.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120133948978.png)

[![image-20221120134315829](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120134315829.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120134315829.png)

[![image-20221120134530599](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120134530599.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120134530599.png)

## Dockerfile概念

[![image-20221120134838135](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120134838135.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120134838135.png)

## Dockerfile关键字

| 关键字      | 作用                     | 备注                                                         |
| ----------- | ------------------------ | ------------------------------------------------------------ |
| FROM        | 指定父镜像               | 指定dockerfile基于那个image构建                              |
| MAINTAINER  | 作者信息                 | 用来标明这个dockerfile谁写的                                 |
| LABEL       | 标签                     | 用来标明dockerfile的标签 可以使用Label代替Maintainer 最终都是在docker image基本信息中可以查看 |
| RUN         | 执行命令                 | 执行一段命令 默认是/bin/sh 格式: RUN command 或者 RUN [“command” , “param1”,”param2”] |
| CMD         | 容器启动命令             | 提供启动容器时候的默认命令 和ENTRYPOINT配合使用.格式 CMD command param1 param2 或者 CMD [“command” , “param1”,”param2”] |
| ENTRYPOINT  | 入口                     | 一般在制作一些执行就关闭的容器中会使用                       |
| COPY        | 复制文件                 | build的时候复制文件到image中                                 |
| ADD         | 添加文件                 | build的时候添加文件到image中 不仅仅局限于当前build上下文 可以来源于远程服务 |
| ENV         | 环境变量                 | 指定build时候的环境变量 可以在启动的容器的时候 通过-e覆盖 格式ENV name=value |
| ARG         | 构建参数                 | 构建参数 只在构建的时候使用的参数 如果有ENV 那么ENV的相同名字的值始终覆盖arg的参数 |
| VOLUME      | 定义外部可以挂载的数据卷 | 指定build的image那些目录可以启动的时候挂载到文件系统中 启动容器的时候使用 -v 绑定 格式 VOLUME [“目录”] |
| EXPOSE      | 暴露端口                 | 定义容器运行的时候监听的端口 启动容器的使用-p来绑定暴露端口 格式: EXPOSE 8080 或者 EXPOSE 8080/udp |
| WORKDIR     | 工作目录                 | 指定容器内部的工作目录 如果没有创建则自动创建 如果指定/ 使用的是绝对地址 如果不是/开头那么是在上一条workdir的路径的相对路径 |
| USER        | 指定执行用户             | 指定build或者启动的时候 用户 在RUN CMD ENTRYPONT执行的时候的用户 |
| HEALTHCHECK | 健康检查                 | 指定监测当前容器的健康监测的命令 基本上没用 因为很多时候 应用本身有健康监测机制 |
| ONBUILD     | 触发器                   | 当存在ONBUILD关键字的镜像作为基础镜像的时候 当执行FROM完成之后 会执行 ONBUILD的命令 但是不影响当前镜像 用处也不怎么大 |
| STOPSIGNAL  | 发送信号量到宿主机       | 该STOPSIGNAL指令设置将发送到容器的系统调用信号以退出。       |
| SHELL       | 指定执行脚本的shell      | 指定RUN CMD ENTRYPOINT 执行命令的时候 使用的shell            |

## Dockerfile案例

### 案例1

[![image-20221120163713655](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120163713655.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120163713655.png)

准备好springboot jar包并传至宿主机的根目录

[![image-20221120164903532](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120164903532.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120164903532.png)

创建docker-files目录，并把jar包移动进去

[![image-20221120165116968](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120165116968.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120165116968.png)

创建dockerfile文件并编辑

```shell
SHELL
FROM java:8
MAINTAINER itheima <itheima@itcast.cn>
ADD HelloDocker-0.0.1-SNAPSHOT.jar app.jar
CMD java -jar app.jar
```

根据dockerfile制作镜像

```shell
PLAINTEXT
docker build -f ./springboot_dockerfile -t app .

-f 指定路径
-t 
```

[![image-20221120170212253](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120170212253.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120170212253.png)

启动并做端口映射

```shell
SHELL
docker run -id -p 9000:8080 app
```

[![image-20221120170509684](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120170509684.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120170509684.png)

成功访问

[![image-20221120170920994](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120170920994.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120170920994.png)

### 案例2

[![image-20221120171246537](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120171246537.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120171246537.png)

编辑dockerfile文件

```shell
SHELL
[root@hecs-33111 docker-files]# vim centos_dockerfile
BASH
FROM centos:7
MAINTAINER itheima<itheima@itcast.cn>
RUN yum install -y vim
WORKDIR /usr
CMD /bin/bash
```

构建镜像

```shell
SHELL
[root@hecs-33111 docker-files]# docker build -f centos_dockerfile -t itheima_centos:1 .
```

[![image-20221120174043683](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120174043683.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120174043683.png)

创建容器

```shell
SHELL
docker run -it --name=c5 itheima_centos:1
```

[![image-20221120174230249](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120174230249.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120174230249.png)

[![image-20221120174417280](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120174417280.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120174417280.png)

# Docker服务编排

[![image-20221120174501970](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120174501970.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120174501970.png)

## 服务编排

[![image-20221120174617528](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120174617528.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120174617528.png)

## Docker Compose

[![image-20221120174712386](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120174712386.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120174712386.png)

## Docker Compose 安装使用

### 一、安装Docker Compose

```shell
SHELL
# Compose目前已经完全支持Linux、Mac OS和Windows，在我们安装Compose之前，需要先安装Docker。下面我 们以编译好的二进制包方式安装在Linux系统中。 
curl -L https://github.com/docker/compose/releases/download/1.22.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
# 设置文件可执行权限 
chmod +x /usr/local/bin/docker-compose
# 查看版本信息 
docker-compose -version
```

[![image-20221120181950479](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120181950479.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120181950479.png)

### 二、卸载Docker Compose

```shell
SHELL
# 二进制包方式安装的，删除二进制文件即可
rm /usr/local/bin/docker-compose
```

### 三、 使用docker compose编排nginx+springboot项目

1. 创建docker-compose目录

```shell
SHELL
mkdir ~/docker-compose
cd ~/docker-compose
```

1. 编写 docker-compose.yml 文件

```shell
SHELL
version: '3'
services:
  nginx:
   image: nginx
   ports:
    - 80:80
   links:
    - app
   volumes:
    - ./nginx/conf.d:/etc/nginx/conf.d
  app:
    image: app
    expose:
      - "8080"
```

[![image-20221120182206246](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120182206246.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120182206246.png)

1. 创建./nginx/conf.d目录

```shell
SHELL
mkdir -p ./nginx/conf.d
```

[![image-20221120182309055](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120182309055.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120182309055.png)

1. 在./nginx/conf.d目录下 编写itheima.conf文件

```shell
SHELL
server {
    listen 80;
    access_log off;

    location / {
        proxy_pass http://app:8080;
    }
   
}
```

[![image-20221120182520017](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120182520017.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120182520017.png)

1. 在~/docker-compose 目录下 使用docker-compose 启动容器

```shell
SHELL
docker-compose up
```

[![image-20221120182758615](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120182758615.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120182758615.png)

1. 测试访问

```shell
SHELL
http://192.168.149.135/hello
```

[![image-20221120182940496](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120182940496.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120182940496.png)

# Docker私有仓库

[![image-20221120183215288](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120183215288.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120183215288.png)

[![image-20221120183254474](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120183254474.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120183254474.png)

### 一、私有仓库搭建

```shell
SHELL
# 1、拉取私有仓库镜像 
docker pull registry
# 2、启动私有仓库容器 
docker run -id --name=registry -p 5000:5000 registry
# 3、打开浏览器 输入地址http://私有仓库服务器ip:5000/v2/_catalog，看到{"repositories":[]} 表示私有仓库 搭建成功
# 4、修改daemon.json   
vim /etc/docker/daemon.json    
# 在上述文件中添加一个key，保存退出。此步用于让 docker 信任私有仓库地址；注意将私有仓库服务器ip修改为自己私有仓库服务器真实ip 
{"insecure-registries":["私有仓库服务器ip:5000"]} 
# 5、重启docker 服务 
systemctl restart docker
docker start registry
```

[![image-20221120201936298](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120201936298.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120201936298.png)

[![image-20221120202727139](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120202727139.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120202727139.png)

[![image-20221120203058041](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120203058041.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120203058041.png)

### 二、将镜像上传至私有仓库

```shell
SHELL
# 1、标记镜像为私有仓库的镜像     
docker tag centos:7 私有仓库服务器IP:5000/centos:7
 
# 2、上传标记的镜像     
docker push 私有仓库服务器IP:5000/centos:7
```

[![image-20221120203333919](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120203333919.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120203333919.png)

[![image-20221120204528268](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120204528268.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120204528268.png)

[![image-20221120204549966](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120204549966.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120204549966.png)

### 三、 从私有仓库拉取镜像

```shell
SHELL
#拉取镜像 
docker pull 私有仓库服务器ip:5000/centos:7
```

[![image-20221120204927944](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120204927944.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120204927944.png)

[![image-20221120205000360](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120205000360.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120205000360.png)

# Docker 相关观念

[![image-20221120205102272](https://weishao-996.github.io/img/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98-Docker/image-20221120205102272.png)](https://weishao-996.github.io/img/黑马程序员-Docker/image-20221120205102272.png)

## Docker容器化虚拟化与传统虚拟机比较

![image-20230320194551522](typora图片/image-20230320194551522.png)

![image-20230320194901494](typora图片/image-20230320194901494.png)