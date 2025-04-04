# Docker学习笔记

参考视频：[黑马程序员Docker快速入门到项目部署，MySQL部署+Nginx部署+docker自定义镜像+DockerCompose项目实战一套搞定_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1HP4118797/?spm_id_from=333.337.search-card.all.click&vd_source=f3cb3ea986b26c6910b4df6d37acd60d)



以下学习使用的系统为CentOS7

## 前置知识

需要先配置以下CentOS7系统

### 如何在局域网中访问虚拟机

首先参考教程[访问局域网中的虚拟机（详细教程！）_vm虚拟机加入局域网-CSDN博客](https://blog.csdn.net/weixin_42340926/article/details/104972208) 对虚拟机网路进行设置。

使用MobaXterm控制终端建立与虚拟机的连接

1.获取虚拟机的ip地址

```
ip addr
```

![image-20250403173255084](./pictures/image-20250403173255084.png)



2.使用MobaXterm建立连接

点击MobaXterm左上角的Session，进入SSH连接，按下图设置即可完成连接

![image-20250403173355925](./pictures/image-20250403173355925.png)

完成连接即可通过终端操控虚拟机

![image-20250403173432083](./pictures/image-20250403173432083.png)





## Docker安装

#### 1.卸载旧版Docker

```
yum remove docker \
    docker-client \
    docker-client-latest \
    docker-common \
    docker-latest \
    docker-latest-logrotate \
    docker-logrotate \
    docker-engine \
    docker-selinux 
```









