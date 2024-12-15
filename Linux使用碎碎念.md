# Linux使用碎碎念

## 如何安装桌面环境

如果安装好系统后进去是一片黑的命令行咋办，

![Screenshot 2024-10-18 151752](C:\Users\Aurora\Pictures\Screenshots\Screenshot 2024-10-18 151752.png)

这可头大了，我之前已经安装了几次桌面了，这次又来，很难受，虽然安了几遍，但仍然没记住方法（哭），所以想着这次就这么边安边把方法记录下来吧，再开一个学习Linux的笔记，用来记录使用Linux时遇到的的各种问题和解决方法。



### 参考文章

[RHEL/Centos7 安装图形化桌面 - Linux就该这么学 - 博客园 (cnblogs.com)](https://www.cnblogs.com/linuxprobe/p/5724537.html)

我当时用RHEL装图形化桌面就是看这个，如果我写的笔记看不懂就去看这个吧，我以后回来看我的笔记我也不知道能不能看懂......



#### 第一步：配置仓库

Linux很操蛋的一点就是安装各种东西需要先配置仓库，不然分分钟连不上，安不上，我在第一次用linux的时候就很烦这一点，因为我不会配置（虽然在学会后发现也不难）



##### 有两种方式：

1.挂载系统光盘来创建本地yum仓库

2.配置远程yum仓库



##### 第一种：

1.先挂载镜像，在vm中进入虚拟机设置界面，将系统镜像先连接

![Screenshot 2024-10-18 152814](C:\Users\Aurora\Pictures\Screenshots\Screenshot 2024-10-18 152814.png)

然后进入系统输入命令

`#mount /dev/sr0 /mnt`   这个命令是将光盘挂载到“/mnt”上

2.接着就创建本地yum仓库

使用命令`vim /etc/yum.repos.d/linuxprobe.repo   `来创建编辑仓库配置文件

```
//仓库配置文件像这样写
[linuxprobe]
name=linuxprobe
baseurl=file:///mnt
enabled=1
gpgcheck=0


//仓库创建好后可以用下面几个命令来管理和检查仓库
yum clean all //清楚yum仓库缓存
yum makecache //创建yum仓库缓存
yum repolist 	//列出可用yum仓库
yum grouplist	//列出程序组
```

#### 第二步：安装桌面组件包了

输入命令`yum -y groupinstall "Server with GUI"`

![Screenshot 2024-10-18 160938](C:\Users\Aurora\Pictures\Screenshots\Screenshot 2024-10-18 160938.png)

#### 第三步：输入命令启动图形化界面

`startx`启动图形化界面

#### 第四步：设置默认运行级别为图形化

```
systemctl get-default  //查看默认运行级别
如果是graphical.target则为图形化界面


systemctl set-default graphical.target //设置默认运行图形化界面
```

![{9765C4B8-2526-465C-B4C2-1DCAC65603EE}](C:\Users\Aurora\AppData\Local\Packages\MicrosoftWindows.Client.CBS_cw5n1h2txyewy\TempState\ScreenClip\{9765C4B8-2526-465C-B4C2-1DCAC65603EE}.png)

## 如何配置yum仓库

该死的CentOS，自己自带的仓库根本没法用，必须要自己配置国内镜像仓库

### 参考文章

[2024年最新：配置CentOS 7阿里yum源_centos7阿里云yum源-CSDN博客](https://blog.csdn.net/m0_53167220/article/details/141263109)

#### 第一步：先备份yum源配置文件

使用命令`mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo_bak`来备份

#### 第二步：修改或新建仓库配置文件

```
vi /etc/yum.repos.d/CentOS-Base.repo	//修改仓库配置文件
```

```
//将一下配置信息复制到配置文件中

# CentOS-Base.repo
#
# The mirror system uses the connecting IP address of the client and the
# update status of each mirror to pick mirrors that are updated to and
# geographically close to the client.  You should use this for CentOS updates
# unless you are manually picking other mirrors.
#
# If the mirrorlist= does not work for you, as a fall back you can try the 
# remarked out baseurl= line instead.
#
#
 
[base]
name=CentOS-$releasever - Base - mirrors.aliyun.com
failovermethod=priority
baseurl=https://mirrors.aliyun.com/centos-vault/7.9.2009/os/$basearch/
gpgcheck=1
gpgkey=https://mirrors.aliyun.com/centos-vault/RPM-GPG-KEY-CentOS-7
 
#released updates 
[updates]
name=CentOS-$releasever - Updates - mirrors.aliyun.com
failovermethod=priority
baseurl=https://mirrors.aliyun.com/centos-vault/7.9.2009/updates/$basearch/
gpgcheck=1
gpgkey=https://mirrors.aliyun.com/centos-vault/RPM-GPG-KEY-CentOS-7
 
#additional packages that may be useful
[extras]
name=CentOS-$releasever - Extras - mirrors.aliyun.com
failovermethod=priority
baseurl=https://mirrors.aliyun.com/centos-vault/7.9.2009/extras/$basearch/
gpgcheck=1
gpgkey=https://mirrors.aliyun.com/centos-vault/RPM-GPG-KEY-CentOS-7
 
#additional packages that extend functionality of existing packages
[centosplus]
name=CentOS-$releasever - Plus - mirrors.aliyun.com
failovermethod=priority
baseurl=https://mirrors.aliyun.com/centos-vault/7.9.2009/centosplus/$basearch/
gpgcheck=1
enabled=0
gpgkey=https://mirrors.aliyun.com/centos-vault/RPM-GPG-KEY-CentOS-7
 
#contrib - packages by Centos Users
[contrib]
name=CentOS-$releasever - Contrib - mirrors.aliyun.com
failovermethod=priority
baseurl=https://mirrors.aliyun.com/centos-vault/7.9.2009/contrib/$basearch/
gpgcheck=1
enabled=0
gpgkey=https://mirrors.aliyun.com/centos-vault/RPM-GPG-KEY-CentOS-7

```

#### 第三步：清除缓存并重建云数据缓存

```
yum clean all	//清除缓存
yum makecache	//重建缓存
```

