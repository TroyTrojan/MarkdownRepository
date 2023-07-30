# 一键搭建Trojan及Trojan-Go面板，保护IP并实现科学上网

## 一.准备工作

1、VPS一台重置好主流的操作系统（例：Debian10 64）

[Racknerd购买地址]: https://racknerd.com/

2、域名一个（已经解析的域名，Win+R输入CMD 回车：键入ping 空格输入你的域名，检查一下是否可以ping通）

如果要使用Trojan-Go开启CND隐藏IP功能，需要将域名托管到CDN。

3、下载并安装FinalShell SSH工具

Windows版下载地址:

[点此下载]: http://www.hostbuf.com/downloads/finalshell_install.exe

## 二.搭建Trojan-Go面板

### 1.开启Debian10自带的BBR加速

脚本如下，可以一起复制运行，或分四行代码一条一条运行。

```
echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf
   
echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf

sysctl -p

lsmod | grep bbr
```

### 2.更新系统安装环境

1、Debian/Ubuntu系统执行以下命令：。

```
apt update -y && apt install -y curl
```

2、CentOS系统执行以下命令：

```
yum update -y && yum install -y curl 
```

### 3.jrohy的一键Trojan脚本

### #安装/更新

```
source <(curl -sL https://git.io/trojan-install)
```

### #卸载

```
source <(curl -sL https://git.io/trojan-install) --remove
```

### 4.安装过程中，会出现3次提示，请根据以下选项进行：

- 1、第一次需要选择1. Let’s Encrypt证书 请输入申请证书的域名：host.kjxlu.com
- 2、选择‘1. 安装docker版mysql’ 回车或手动输入用户名

注：跑完以上代码后，最后会出现一个选择菜单，不用理会，直接回车退出即可，即回到#提示符的状态下。至此，Trojan-Go面板搭建完成。

### 5.安装完后输入'trojan'可进入管理程序

浏览器访问[https://域名，可在线web页面管理用户]

第一次登陆面板时，会让您输入登陆密码，输入完后请使用用户名‘admin’及您设置的密码登陆。

## 三.Trojan-Go设置

### 1.登陆面板，修改Trojan类型为Trojan-Go

![image-20230414161547942](https://raw.githubusercontent.com/TroyTrojan/PictureBed/main/image-20230414161547942.png)

### 2.更改Trojan-Go配置文件

找到VPS目录文件 /usr/local/etc/trojan/config.json ，备份一份（若是把类型切换回来可以恢复使用Trojan）。

对着config.json文件按鼠标右键，选择‘用记事本编辑’。

### 3.更改配置参数：

### *注意：要在mysql的大括号}后加一个英文的逗号。路径和域名需要在客户端匹配。

```
     "websocket": {
    "enabled": true,
    "path": "/DFE4545DFDED/",
    "host": "你的域名"
   },
    "mux": {
    "enabled": true,
    "concurrency": 8,
    "idle_timeout": 60
    }
```

![image-20230414161502169](https://raw.githubusercontent.com/TroyTrojan/PictureBed/main/image-20230414161502169.png)

1、/DFE4545DFDED/为路径，随意填写。 2、host后 填上你的域名

### 保存后，在Trojan-Go面板重启服务。

## 四.下载Trojan-Go客户端

### 1.Trojan-Qt5

[下载地址]: https://github.com/KEJIXIAOLU/Trojan/releases/tag/Trojan-Qt5

![image-20230414161353303](https://raw.githubusercontent.com/TroyTrojan/PictureBed/main/image-20230414161353303.png)

2.QV2RAY（支持WIN/MACOS）

QV2RAY 下载地址：https://github.com/Qv2ray/Qv2ray/releases/

QV2RAY 内核下载地址：https://github.com/v2ray/v2ray-core/releases

![image-20230416191914108](https://raw.githubusercontent.com/TroyTrojan/PictureBed/main/image-20230416191914108.png)