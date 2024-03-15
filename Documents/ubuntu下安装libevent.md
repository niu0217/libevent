# ubuntu下安装libevent

## 参考资料

+ [libevent学习笔记之Ubuntu下搭建编译libevent环境](https://www.cnblogs.com/fortunely/p/15313784.html)

## 环境准备

| 名称     | 版本                          | 下载/安装方式 | 描述                                            |
| -------- | ----------------------------- | ------------- | ----------------------------------------------- |
| Ubuntu   | Ubuntu20.04                   | 官网下载      | ubuntu 官网 https://ubuntu.com/download/desktop |
| perl     | 最新版                        | apt-get       | 脚本解释器，编译openssl用                       |
| g++      | 最新版                        | apt-get       | C++编译器                                       |
| make     | 最新版                        | apt-get       | 用于根据Makefile编译，生成elf目标文件           |
| automake | 最新版                        | apt-get       | 用于生成Makefile                                |
| libtool  | 最新版                        | apt-get       | 库文件工具                                      |
| unzip    | 最新版                        | apt-get       | 解压压缩包                                      |
| zlib     | version 1.3.1                 | 官网下载      | http://www.zlib.net/                            |
| openssl  | openssl-3.2.1.tar.gz          | 官网下载      | https://www.openssl.org/source/                 |
| libevent | libevent-2.1.12-stable.tar.gz | 官网下载      | https://libevent.org/                           |

## 依赖环境安装

```bash
sudo apt-get install perl g++ make automake libtool unzip
```

## 编译zlib

（1）解压

```bash
tar -xvf zlib-1.3.1.tar.gz
```

（2）进入解压后的目录

```bash
cd zlib-1.3.1
```

（3）生成makefile文件

```bash
./configure
```

（4）make命令编译

```bash
make
```

（5）安装库文件

```bash
sudo make install
```

该命令会把库文件（`.a/.so, .h`）安装到`/usr/local/lib和/usr/local/include`目录下；man手册文件安装到`/usr/local/share/man/man3`

## 编译openssl

（1）解压

```bash
tar -xvf openssl-3.2.1.tar.gz
```

（2）进入解压后的目录

```bash
cd openssl-3.2.1
```

（3）生成makefile

```bash
./config
```

（4）编译

```bash
make
```

（5）安装库文件

```bash
sudo make install
```

## 编译libevent

（1）解压

```bash
tar -xvf libevent-2.1.12-stable.tar.gz
```

（2）进入解压后的目录

```bash
cd libevent-2.1.12-stable
```

（3）生成configure文件

```bash
./autogen.sh
```

（4）生成makefile

```bash
./configure --prefix=/usr 
```

（5）编译

```bash
make
```

（6）安装库文件

```bash
sudo make install
```

（7）验证

```bash
ubuntu@niu0217:~/InstallLib/libevent-2.1.12-stable$ ls -al /usr/lib |grep libevent
lrwxrwxrwx   1 root root      21 Mar 15 19:28 libevent-2.1.so.7 -> libevent-2.1.so.7.0.1
-rwxr-xr-x   1 root root 1652192 Mar 15 19:28 libevent-2.1.so.7.0.1
-rw-r--r--   1 root root 2993902 Mar 15 19:28 libevent.a
lrwxrwxrwx   1 root root      26 Mar 15 19:28 libevent_core-2.1.so.7 -> libevent_core-2.1.so.7.0.1
-rwxr-xr-x   1 root root 1076384 Mar 15 19:28 libevent_core-2.1.so.7.0.1
-rw-r--r--   1 root root 1883950 Mar 15 19:28 libevent_core.a
-rwxr-xr-x   1 root root     989 Mar 15 19:28 libevent_core.la
lrwxrwxrwx   1 root root      26 Mar 15 19:28 libevent_core.so -> libevent_core-2.1.so.7.0.1
lrwxrwxrwx   1 root root      27 Mar 15 19:28 libevent_extra-2.1.so.7 -> libevent_extra-2.1.so.7.0.1
-rwxr-xr-x   1 root root  612072 Mar 15 19:28 libevent_extra-2.1.so.7.0.1
-rw-r--r--   1 root root 1110026 Mar 15 19:28 libevent_extra.a
-rwxr-xr-x   1 root root     996 Mar 15 19:28 libevent_extra.la
lrwxrwxrwx   1 root root      27 Mar 15 19:28 libevent_extra.so -> libevent_extra-2.1.so.7.0.1
-rwxr-xr-x   1 root root     954 Mar 15 19:28 libevent.la
lrwxrwxrwx   1 root root      29 Mar 15 19:28 libevent_openssl-2.1.so.7 -> libevent_openssl-2.1.so.7.0.1
-rwxr-xr-x   1 root root  107664 Mar 15 19:28 libevent_openssl-2.1.so.7.0.1
-rw-r--r--   1 root root  202298 Mar 15 19:28 libevent_openssl.a
-rwxr-xr-x   1 root root    1042 Mar 15 19:28 libevent_openssl.la
lrwxrwxrwx   1 root root      29 Mar 15 19:28 libevent_openssl.so -> libevent_openssl-2.1.so.7.0.1
lrwxrwxrwx   1 root root      30 Mar 15 19:28 libevent_pthreads-2.1.so.7 -> libevent_pthreads-2.1.so.7.0.1
-rwxr-xr-x   1 root root   31768 Mar 15 19:28 libevent_pthreads-2.1.so.7.0.1
-rw-r--r--   1 root root   28630 Mar 15 19:28 libevent_pthreads.a
-rwxr-xr-x   1 root root    1017 Mar 15 19:28 libevent_pthreads.la
lrwxrwxrwx   1 root root      30 Mar 15 19:28 libevent_pthreads.so -> libevent_pthreads-2.1.so.7.0.1
lrwxrwxrwx   1 root root      21 Mar 15 19:28 libevent.so -> libevent-2.1.so.7.0.1
```

如果出现上述结果，说明是OK的。
