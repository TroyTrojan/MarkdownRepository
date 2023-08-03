# 一键搭建代理面板教程(X-UI,Trojan,Trojan Panel三选一即可)

# 一键搭建X-UI面板(最流行的个人面板)

## 一.准备工作

- 1、域名一个，托管到 Cloudflare 
- 2、VPS 一台，例如：Debian/Ubuntu/CentOS
- 3、下载并安装 FinalShell SSH 工具
- Windows 版本下载地址: http://www.hostbuf.com/downloads/finalshell_install.exe

## 二.更新安装系统

1、Debian/Ubuntu 系统执行以下命令：

```
apt update -y         
apt install -y curl    
apt install -y socat    
```

2、CentOS 系统执行以下命令：

```
yum update -y         
yum install -y curl   
yum install -y socat   
```



## 三.安装BBR加速

本脚本建议在Debian≥9或是CentOS≥8以上的系统中使用

```
wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh" && chmod +x tcp.sh && ./tcp.sh
```



## 四.一键安装面板并放行端口

安装面板

```
bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)
```

放行端口，需要放行443端口和设置的端口如54321

```
iptables -I INPUT -p tcp --dport 443 -j ACCEPT
iptables -I INPUT -p tcp --dport 54321 -j ACCEPT
```

完成 X-ui 安装以后，我们可以输入 VPS IP:端口（如1.1.1.1:12345） 登录 X-ui 的管理面板（可以登录代表安装成功）

## 五.利用DNS申请证书

在 VPS 输入` x-ui` 命令，进入 X-ui 的命令菜单 选择 16，申请 SSL 的证书。（申请需要有 Cloudflare API）

申请的时候是申请的泛域名证书，所以，填写域名的时候，只填入域名也就好了，例如`  xxx.com` 的格式。

申请成功以后，证书和密钥文件在 VPS 目录的` /root/cert `文件夹里面

## 六.访问并设置Xray管理面板

在浏览器中输入刚才解析的域名xxxxx.xyz ，用户名 admin ，密码 admin

修改必要的面板参数 SSL证书以及密钥（绝对地址）、面板端口、登录标题 等，其他若是你不清楚，请保持默认

- 重要：若是设置了 SSL证书以及密钥 ，再次登录需要输入 https://xxxxx.xyz:54321 访问，注意，是 https

## 七.关于x-ui节点电脑V2ray能连接上，扫描导入手机V2rayNG连接不了

在 X-ui面板设置中，“面板证书公钥文件路径”，不要用带自己域名的证书，输入` /root/cert/fullchain.cer` （这是标准的CA证书集的文件之一）的路径。然后重启面板。在创建的节点时候，公钥文件路径同样填入 ` /root/cert/fullchain.cer` 。

# 一键搭建Trojan及Trojan-Go面板(保护IP并实现科学上网)

## 一.准备工作

1、VPS一台重置好主流的操作系统（例：Debian10 64,Ubuntu 20 64）

[Racknerd购买地址]: https://racknerd.com/

2、域名一个（已经解析的域名，Win+R输入CMD 回车：键入ping 空格输入你的域名，检查一下是否可以ping通）

如果要使用Trojan-Go开启CND隐藏IP功能，需要将域名托管到CDN。

3、下载并安装FinalShell SSH工具

Windows版下载地址:

[点此下载]: http://www.hostbuf.com/downloads/finalshell_install.exe

## 二.搭建Trojan-Go面板

### 1.开启系统自带的BBR加速

脚本如下，可以一起复制运行，或分四行代码一条一条运行。

```
echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf  
echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf
sysctl -p
lsmod | grep bbr
```

如何检测BBR是否开启可执行以下代码:

```
sysctl net.ipv4.tcp_available_congestion_control
```

如果返回值中带有bbr则为成功开启,例如:

```
net.ipv4.tcp_available_congestion_control = reno cubic bbr
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

3.jrohy的一键Trojan脚本

### #安装/更新

```
source <(curl -sL https://git.io/trojan-install)
```

### #卸载

```
source <(curl -sL https://git.io/trojan-install) --remove
```

### 4.安装过程中，会出现3次提示，请根据以下选项进行：

- 1、第一次需要选择1. Let’s Encrypt证书 请输入申请证书的域名：xxxxx.xyz
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

1.Trojan-Qt5

[下载地址]: https://github.com/KEJIXIAOLU/Trojan/releases/tag/Trojan-Qt5

![image-20230414161353303](https://raw.githubusercontent.com/TroyTrojan/PictureBed/main/image-20230414161353303.png)

2.QV2RAY（支持WIN/MACOS）

QV2RAY 下载地址：https://github.com/Qv2ray/Qv2ray/releases/

QV2RAY 内核下载地址：https://github.com/v2ray/v2ray-core/releases

![image-20230416191914108](https://raw.githubusercontent.com/TroyTrojan/PictureBed/main/image-20230416191914108.png)

# 一键搭建Trojan Panel面板(可以实现分布式部署)

## 一.准备工作

1、VPS一台重置好主流的操作系统（例：Debian10 64,Ubuntu 20 64）

[Racknerd购买地址]: https://racknerd.com/

2、域名一个（已经解析的域名，Win+R输入CMD 回车：键入ping 空格输入你的域名，检查一下是否可以ping通）

3、下载并安装FinalShell SSH工具

Windows版下载地址:

[点此下载]: http://www.hostbuf.com/downloads/finalshell_install.exe

## 二.搭建Trojan Panel面板

### 1.开启系统自带的BBR加速

脚本如下，可以一起复制运行，或分四行代码一条一条运行。

```
echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf  
echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf
sysctl -p
lsmod | grep bbr
```

如何检测BBR是否开启可执行以下代码:

```
sysctl net.ipv4.tcp_available_congestion_control
```

如果返回值中带有bbr则为成功开启,例如:

```
net.ipv4.tcp_available_congestion_control = reno cubic bbr
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

3.Trojan panel一键脚本

### 联机版

```
source <(curl -L https://github.com/trojanpanel/install-script/raw/main/install_script.sh)
```

### 单机版

```
source <(curl -L https://github.com/trojanpanel/install-script/raw/main/install_script_standalone.sh)
```

4.根据脚本依次执行即可。

# 端口放行

## 一.Debian/Ubuntu 放行端口

例如放行80端口

```
iptables -I INPUT -p tcp --dport 80 -j ACCEPT
```

然后保存放行规则

```
iptables-save
```



## 二.Centos 放行端口

例如放行80端口

```
firewall-cmd --zone=public --add-port=80/tcp --permanent
```

然后重启防火墙

```
firewall-cmd --reload
```



## 三.查看防火墙规则

```
iptables -L
```

# WARP的安装与使用

## 一.作用

安装warp可以隐藏自己的ip，拯救被墙的服务器、谷歌频繁的人机验证以及解锁奈飞，油管，ChatGPT等。

## 二.安装

初次安装只需输入以下代码:

```
wget -N https://raw.githubusercontent.com/fscarmen/warp/main/menu.sh && bash menu.sh [option] [lisence]
```

安装后只需选择为ipv4添加warp即可，一般为选项1.

另外需要注意的是，在选择warp账户时，要选择warp+账户，留空即可，选择免费帐户无法达到隐藏IP的目的。