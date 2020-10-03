# 安装NGINX

本文描述如何安装NGINX。

## 编译安装（推荐）

如果你之前有过安装NGINX的经验，你可能会在第一时间想到使用包管理器安装，但是使用`apt`或`yum`安装的NGINX不能自己选择需要添加的模块，且很多时候并不包含最新版本。

所以，这里我推荐使用编译安装的方法安装NGINX。这样你可以安装自己想要的版本，也可以方便地选择需要的模块。

### 安装相关依赖

编译安装需要自行安装相关依赖。

安装编译所需的工具（以CentOS为例）：

```shell
yum -y install gcc make
```

安装NGINX所需的相关依赖：

```shell
yum -y install pcre pcre-devel zlib zlib-devel openssl openssl-devel
```

上面的示例中使用包管理器安装了`pcre` `zlib` `openssl`，其中，`pcre`使得NGINX支持正则表达式，`zlib`使得NGINX支持`gzip`，而`openssl`是使用TLS的必需库。

**注意：某些Linux发行版安装的OpenSSL版本过低，OpenSSL版本在1.1.1及以上才能支持TLS1.3。**

### 下载NGINX源码

前往NGINX官方[下载页](https://nginx.org/en/docs/)可以查看到NGINX各个版本及其下载链接。

这里下载最新稳定版：

```shell
wget https://nginx.org/download/nginx-1.18.0.tar.gz
```

解压：

```shell
tar -zxvf nginx-1.18.0.tar.gz
```

### 编译安装

进入NGINX源码目录：

```shell
cd nginx-1.18.0
```

Configure：

```shell
./configure \
--prefix=/usr/local/nginx \
--with-http_ssl_module \
--with-http_v2_module
```

configure步骤可以指定需要安装的模块，这里指定的`prefix`为安装目录，同时指定安装了`http_ssl_module`和`http_v2_module`，是支持HTTP模块中启用TLS和HTTP/2的常用模块。

编译和安装：

```shell
make && make install
```

`make`编译源码，`make install`将编译后的文件安装到指定目录。

## 包管理器安装（不推荐）

以CentOS为例：

```shell
yum -y install nginx
```

上面也已经提到过了，这种方法安装有安装版本不新、无法指定模块的缺点。