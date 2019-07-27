## linux 程序设置后台运行及查看方法

- ### linux 程序设置后台运行
Linux: `nohup commond &`
> commond 为要运行的命令。

- ### Linux 查看用户进程
Linux: `ps -u frank`

- ### Linux 查看端口占用情况
Linux: `lsof -i`

```linux
(cv) frank@gpu-server:~/work$ lsof -i
COMMAND   PID  USER   FD   TYPE   DEVICE SIZE/OFF NODE NAME
jupyter-n 911 frank    6u  IPv4 16350869      0t0  TCP *:8888 (LISTEN)
jupyter-n 911 frank   10u  IPv4 16381138      0t0  TCP 114.70.**.**:8888->210.117.**.**:49161 (ESTABLISHED)
```

- ### Linux 查看8080端口占用
Linux: `lsof -i:8080` 

- ### Linux 查看指定的程序
Linux: `ps -ef|grep jupyter `   jupyter为指定的程序

- ### Linux 杀掉(kill)对应的进程
Linux: `kill -9 911`    911为PID号。