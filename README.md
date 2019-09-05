# Hope you love Linux.
这个软件是一个命令行远程连接脚本。学生装在自己的Centos 7上，当他们有问题的时候，可以启动这个程序，我就可以远程登陆他们的电脑，共享shell，trouble shooting了。

# How To Use
学生：
```bash
$ yum install screen # 安装依赖screen
$ cd remote-terminal-share && ./start # 运行共享命令行
```
老师：
```bash
$ ssh user@0.tcp.ngrok.io -p12345 && screen -x shared # 登陆
$ ps -C ngrok # 查看pid
$ kill xxxx && exit # 退出登陆，同时断掉连接
```

# 原理
.  
|-- ngrok  
|-- ngrok.yml  
|-- README.md  
|-- start  

start脚本就两句，一个是用ngrok内网穿透，另一个是用screen启动一个共享shell。当然默认是学生电脑上启动了sshd。然后我通过ngrok.com登陆我的帐号，查看url和port，就能远程登陆到学生电脑了。
