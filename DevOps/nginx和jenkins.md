## DevOps - nginx 和 jenkins 服务搭建

### 当前环境

--os        linux 1核2GB
--pcre      8.37
--nginx     1.20.1
--jenkins   2.346.3

nginx web服务：http://123.60.83.127:80/
jenkins服务：http://123.60.83.127:8080/

### 需准备的环境和工具

说明：按照以下顺序进行配置

- linux 云服务器一台

- XShell（链接远程服务器）

[下载链接](https://www.xshell.com/zh/all-downloads/)

- fileZilla（上传文件到远程服务器）

[下载链接](https://filezilla-project.org/download.php?type=client)

- vscode => Remote-SSH 插件

[使用方法](https://blog.csdn.net/jackailson/article/details/125341008)

- 新建目录
    $ cd /usr/local
    $ mkdir nginx jenkins nvm

- make

1. 安装依赖

$ yum -y install gcc gcc-c++ autoconf automake zlib zlib-devel openssl openssl-devel pcre pcre-devel

2. 执行命令

$ ./configure
$ make && make install

- pcre（nginx依赖，放在新建的 `jenkins` 目录里面）

1. 下载

$ wget http://downloads.sourceforge.net/project/pcre/pcre/8.37/pcre-8.37.tar.gz

2. 解压

$ tar -xzpvf pcre-8.37.tar.gz

3. 执行命令

$ ./configure

4. 编译

$ make && make install

5. 查看版本是否安装成功

$ pcre-config --version


- nginx 安装 (放在新建的 `jenkins` 目录里面)

1. 下载 nginx

$ wget http://nginx.org/download/nginx-1.20.1.tar.gz

2. 解压 nginx

$ tar -zxvf nginx-1.20.1.tar.gz

3. 执行命令

$ ./configure

4. 编译

$ make && make install

5. 启动

$ ./nginx

6. 查看是否启起

$ ps -ef | grep nginx

7. 访问 nginx 

服务器公网IP + 80端口

说明：如果无法访问，检查服务器安全组规则中80端口是否开放

这里可以尝试部署一个简单的前端静态页面，按照以下步骤后访问 `服务器公网IP + 80端口` 即可

1. 新建一个 `vue` 或者 `react` 项目打包构建 `dist` 文件夹
2. 使用 `fileZilla` 拖动上传 `dist` 文件夹放入 nginx 编译好的 html 文档里面
3. vim nginx.conf 或者只有 vscode => Remote-SSH 插件修改配置
```conf => nginx.conf
localtion: {
    root: html/dist
    index: index.html index.html
}
```
4. 重启 nginx

$ nginx -s reload


- jenkins 安装

1. 检查是否安装 java-sdk

$ rpm -q | grep java

2. 搜索 jdk 安装报

yum search java|grep jdk

3. 安装 java-jdk（这里 jenkins-2.346.3 启动需依赖 11 或者 14 的版本）

$ yum install 版本号
$ yum list installed |grep java

4. 查看版本号是否安装成功

$ java -version

5. 下载 jenkins，在线下载或者本地上传

[下载链接](https://www.jenkins.io/zh/download/)

$ wget https://mirrors.jenkins.io/war-stable/latest/jenkins.war

6. 启动 jenkins

java -jar /usr/isTester/jenkins.war --httpPort=8080

说明：成功后有等下需要登录jenkins的密钥及jenkins存放的文件路劲

如果在后台运行
新建一个jenkins.sh脚本
```
nohup java -jar jenkins.war --httpPort=8080 &
```

7. 访问`服务器公网IP + 80端口`

说明：无法访问，检查一下 jenkins 是否启动成功或者检查下服务器安全组规则中8080端口是否开放

### 命令补充

1. 提升文件权限

$ chmod -R +x 当前文件夹

2. 查看进程

$ ps -ef|grep jenkins(运行的程序)

3.关闭进程

$ kill -g 进程id
