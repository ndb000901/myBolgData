---
title: nginx安装手册
tags:
    - 软件安装
---

## nginx安装手册

**1.实验环境**

>1.manjaro-gnome21
>
>2.nginx-1.19.10 [下载界面](https://nginx.org/en/download.html)
>

<!--more-->

**2.安装**

在/usr/local创建nginx目录

```
cd /usr/local
mkdir nginx
cd nginx
```

下载nginx，解压，进入nginx-1.19.10,执行命令编译。生成的可执行文件在上级目录sbin。

```
wget https://nginx.org/download/nginx-1.19.10.tar.gz
tar -zxvf nginx-1.19.10.tar.gz
cd nginx-1.19.10/ 
./configure
make && make install
```

**3.nginx使用**

启动

启动后，打开浏览器查看127.0.0.1

**成功界面**

![image](https://user-images.githubusercontent.com/48900845/115152209-c1b5df00-a0a2-11eb-8564-e73258255bdd.png)


```
/usr/local/nginx/sbin/nginx
```

停止

```
/usr/local/nginx/sbin/nginx -s stop
```

修改配置文件后重启

```
/usr/local/nginx/sbin/nginx -s reload
```

**4.配置**

配置文件位置

```
/usr/local/nginx/conf/nginx.conf
```

配置虚拟主机

```
server {
        listen       80;
        server_name  mysite.haha;
        location / {
            root   html/mysite;
            index  index.html index.htm;
        }
    }
```

修改/etc/hosts

```
127.0.0.1 mysite.haha
```

>作者info
>
>作者：DebugWuhen
>
>原创公众号：『DebugWuhen』，专注于记录有趣的编程技术和有益的程序人生，期待你的关注。
>
>转载说明：务必注明来源（注明：来源于公众号：DebugWuhen， 作者：DebugWuhen）
>
>![image](https://user-images.githubusercontent.com/48900845/112752163-3b0e6480-9004-11eb-899d-66ddef749c2b.png)


