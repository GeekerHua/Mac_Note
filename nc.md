# nc——netcat
- server: nc -l `part` < `document`
- client: nc -n `ip` `port` > `document`

## 用nc聊天
- server: nc -l `ip`
- nc `ip` `port`

---

## nc (netCat)

`nc -l [-u] 9090`: 在9090端口开启tcp服务器 
`[-v] [-u] 127.0.0.1 9090`: 连接本地ip的9090端口tcp服务器

`-l`: 启动监听, 启动服务器必须 
`-v`: 显示连接进度 
`-u`: 使用udp通信, 默认是tcp, 使用udp连接可以保持一直监听状态 
`-w2`: 设置超时2秒 
`-z`: 检测端口

### tcp聊天

`nc -l 9090`: tcp监听9090端口 
`nc 127.0.0.1 9090`: tcp连接9090端口 
可以用重定向 '<'/'>', 指定传输内容, 只能响应一个客户端, 客户端断开, 服务器端也会断开

### udp聊天

`nc -lu 9090`: udp监听9090端口 
`nc -u 127.0.0.1 9090`: udp连接9090端口 
可以用重定向 '<'/'>', 指定传输内容, 只能响应一个客户端, 客户端断开, 服务器端不会断开

### 检查端口

`nc -z 127.0.0.1 1-100`: 查看指定ip tcp 连接 的 1-100端口 
`nc -z -u 127.0.0.1 1-100`: 查看指定ip udp 连接 的 1-100端口

### 远程传输文件

`nc -l 9090 > test.tmp`: 监听 9090 端口 并把信息输出到指定文件 
`nc 127.0.0.1 9090 < test.tmp`: 连接服务, 并把文件输出


--

wget
远程访问

# scp
> 远程拷贝文件,scp -r 的常用方法：

1.使用该命令的前提条件要求目标主机已经成功安装openssh-server

如没有安装使用 sudo apt-get install openssh-server 来安装
2.使用格式：

scp -r 目标用户名@目标主机IP地址：/目标文件的绝对路径  /保存到本机的绝对/相对路径

举例：
scp -r itcast@192.168.1.100:/home/itcast/QQ_dir/ ./mytest/lisi

在后续会提示输入“yes”此时，只能输“yes”而不能简单输入“Y”
拷贝单个文件可以不加 -r参数，拷贝目录必须要加。

本地文件复制到远程：

scp FileName RemoteUserName@RemoteHostIp:RemoteFile
scp FileName RemoteHostIp:RemoteFolder
scp FileName RemoteHostIp:RemoteFile
本地目录复制到远程：

scp -r FolderName RemoteUserName@RemoteHostIp:RemoteFolder
scp -r FolderName RemoteHostIp:RemoteFolder
远程文件复制到本地：

scp RemoteUserName@RemoteHostIp:RemoteFile FileName
scp RemoteHostIp:RemoteFolder FileName
scp RemoteHostIp:RemoteFile FileName
远程目录复制到本地：

scp -r RemoteUserName@RemoteHostIp:RemoteFolder FolderName
scp -r RemoteHostIp:RemoteFolder FolderName

