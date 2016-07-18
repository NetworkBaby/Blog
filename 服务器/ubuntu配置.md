# Ubuntu配置

### 1、命令提示符

修改 ~/.bashrc文件 PS1参数

#### 主要信息
- /u 当前登录用户名
- /h 当前计算机名称（譬如ubuntu）
- /H 当前计算机的域名全程，譬如（ubuntu.ubuntu.com）
- /w 当前目录的完整路径。家目录会以~代替
- /W 利用basename取得工作目录名称，所以只会列出最后一个目录
- /$ 一般用户为$，root用户为》
　　
#### 时间显示
- /t 当前时间（24小时制，HH:MM:SS 分别代表 小时：分钟：秒）
- /T 当前时间（12小时制）
- /@ 当前时间（AM/PM显示）
- /d 当前日期


### 2、安装jdk

#### 2.1、Installing default JRE/JDK
```
- sudo apt-get update
- sudo apt-get install default-jre
- sudo apt-get install default-jdk
```

#### 2.2、环境配置

vim /etc/profile

```
export JAVA_HOME=/usr/lib/jvm/java-1.7.0-openjdk-amd64

export PATH=$PATH:$JAVA_HOME/bin:$JAVA_HOME/jre/bin

export CLASSPATH=.:$JAVA_HOME/lib:$JAVA_HOME/lib/tools.jar

export JRE_HOME=$JAVA_HOME/jre
```

### 3、安装apache2

`apt-get install apache2`

### 4、安装mysql

`apt-get install mysql-client mysql-server`

### 5、安装php5

`apt-get install php5 libapache2-mod-php5`

### 6、安装tomcat

#### 6.1、下载 Tomcat

[http://tomcat.apache.org/download-70.cgi](http://tomcat.apache.org/download-70.cgi)

#### 6.2、解压 Tomcat

`tar -zxvf `

#### 6.3、配置 Tomcat

`vim /etc/profile`

`export TOMCAT_HOME=`

#### 6.4、启动tomcat

`./startup.sh`

### 7、安装svn

#### 7.1、安装包

`apt-get install subversion`

#### 7.2、创建项目目录

- `$ sudo mkdir /home/svn`
- `$ cd /home/svn/`
- `$ sudo mkdir project`

#### 7.3、创建svn文件仓库

svnadmin create /home/svn/project

#### 7.4、访问权限设置 

修改 `/home/xiaozhe/svn/mypro/conf`目录下： 
`svnserve.conf` 、`passwd` 个文件，行最前端不允许有空格 

编辑`svnserve.conf`文件，把如下面行取消注释，并需要顶格

`anon-access = read`
`auth-access = write`

`password-db = passwd `


编辑passwd  如下: 

[users] 

`andy = andy `

#### 7.5、开启svnserve,以SVN根目录开启： 

`$ svnserve -d -r /home/xiaozhe/svn`

可以看到有一个端口为3690的地址，表示启动成功

#### 7.6、局域网访问，checkout出来SVN库的文件

`svn checkout svn://svnIp地址/project`

或者简写为： 

`svn co svn://svnIp地址/project`

### 8、安装node

#### 8.1、下载

[https://nodejs.org/en/download/](https://nodejs.org/en/download/)

Linux Binaries (.tar.xz)

解压：xz -d >  tar -xvf

#### 8.2、软链接方式

`ln -s /software/node-v4.4.7-linux-x64/bin/node /usr/local/bin/node`
`ln -s /software/node-v4.4.7-linux-x64/bin/npm /usr/local/bin/npm`

### 9、安装mongo

`apt-get install mongodb-clients mongodb-server mongodb mongodb-dev`

#### 9.1、权限控制

`vim /etc/mongodb.conf`

auth=true

#bind_ip = 127.0.0.1

#port = 27017

### 9.2、创建用户

`use admin`

`db.addUser`

`db.createUser`

 