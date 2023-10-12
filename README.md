[搭建路由器梯子](https://www.cnblogs.com/Jimmy1988/p/17015604.html)

# 0. 准备工作
## 0.1. 购买VPS
> 参见：https://www.cnblogs.com/Jimmy1988/p/9169183.html

## 0.2 购买域名
`注意，如果要架梯子，国内大网站（比如阿里、腾讯等）购买的域名，是作不了梯子域名的`

建议去 [name silo](https://www.namesilo.com/) 上购买

购买后，请`务必将域名和你的VPS服务器公网IP地址绑定`，后续每次更换服务器，都要重复上面的操作，具体如何更换IP，请参考该blog：https://www.ldhost.cn/jc/do/8031.html

#1. 服务器安装trojan

### 1) 使用xshell或其他登录VPS
```
ssh root@[your-server-ip]
```

### 2) 安装wget
```
 sudo yum install wget        #for centos
 sudo apt-get install wget    #for ubuntu
```

### 3) 下载并安装文件
```
mkdir -p /usr/local/trojan
cd /usr/local/trojan
wget -N --no-check-certificate -q -O trojan\_mult.sh "https://raw.githubusercontent.com/Jimmy-Nie/trojan_mult/main/trojan_mult.sh"  #下载安装脚本
```

###4) 根据提示进行安装
```
chmod +x trojan_install.sh
./trojan_install.sh
```

![](https://img2023.cnblogs.com/blog/1151054/202304/1151054-20230413100349077-507635848.png)

**安装成功时，显示如下**：
![](https://img2023.cnblogs.com/blog/1151054/202304/1151054-20230419141829503-2029647517.png)

# 2. v（To）ray客户端

**1) 下载客户端文件**
下载：
> [地址1](https://wwa.lanzoui.com/i1uS4kx1rub)
> [地址2](https://www.linuxv2ray.com/client/)

**2) 打开v（To）rayN.exe**

**3) 添加trojan server**

**4) 启动http代理**

**Notice：请选择\[PAC]模式**

#3. 刷路由器

> 使用【斐讯k2p】路由器
> 固件下载地址：https://opt.cn2qq.com  （已失效，留言单发）

# 4. 问题
## 1）获取证书一直失败
![](https://img2023.cnblogs.com/blog/1151054/202304/1151054-20230419112545319-1150852583.png)


**解决方案**：

参考 github：`https://github.com/acmesh-official/acme.sh`

总结命令如下：
```
wget -O -  https://get.acme.sh | sh -s email=my@example.com    #下载acme.sh
acme.sh  --register-account  -m [youremail] --server zerossl    #注意，acme.sh有可能安装到了 /root/.acme.sh/acme.sh
#执行该指令，注意修改邮箱名称，[详细请见此处](https://github.com/acmesh-official/acme.sh/wiki/ZeroSSL.com-CA)
```
 
![](https://img2023.cnblogs.com/blog/1151054/202304/1151054-20230419140413788-813314368.png)


## 2) 域名解析地址与本VPS IP地址不一致

> 进入你的[域名申请网站](https://www.namesilo.com/account_domain_manage_dns.php)，将你要搭建的VPS服务器的公网地址加到对应域名的支持列表中。
>
> *   注意：IP增加以后，需要等几个小时，让全球同步后，方可以去搭建VPS的trojan
