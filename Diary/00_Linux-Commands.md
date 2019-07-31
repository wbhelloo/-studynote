## Linux常用命令

- ### 查看CUDA版本

    ```Linux
    Linux: `cat /usr/local/cuda/version.txt`  
    ```

- ### 显示文件系统的磁盘使用情况统计
    Linux： `df -h`

    ```Linux
    frank@312LabW:~/work$ df -h  
    Filesystem      Size  Used Avail Use% Mounted on  
    udev            7.8G     0  7.8G   0% /dev  
    tmpfs           1.6G  162M  1.4G  11% /run  
    /dev/sda6        95G   33G   57G  37% /  
    tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup    
    /dev/sdb5       1.8T  605G  1.2T  35% /home  
    /dev/sda1       931M  445M  423M  52% /boot  
    ```

- ### 显示指定文件夹的磁盘使用情况统计
    Linux: `df /home/ -h`

    ```Linux
    frank@312LabW:~/work$ df /home/ -h  
    Filesystem      Size  Used Avail Use% Mounted on  
    /dev/sdb5       1.8T  605G  1.2T  35% /home  
    ```

- ### 显示指定文件夹的磁盘使用情况统计
    Linux: `du -h --max-depth=1 /home/` 

    ```linux
    (cv) frank@itrc:/$ du -h --max-depth=1 /home/
    31G     /home/hahmed
    1.4T    /home/thai
    82G     /home/frank
    1.8T    /home/
    ```

- ### 统计当前目录下文件的个数（不包括目录）

    Linux: `ls -l | grep "^-" | wc -l`


- ### 统计当前目录下文件的个数（包括子目录）

    Linux:  `ls -lR| grep "^-" | wc -l`


- ### 查看某目录下文件夹(目录)的个数（包括子目录）

    Linux: `ls -lR | grep "^d" | wc -l`


- ### 更改用户名密码
    Linux: `passwd 当前用户名`

    ```Linux
    frank@itrc:~$ passwd frank  
    Changing password for frank.  
    (current) UNIX password:  
    Enter new UNIX password:  
    Retype new UNIX password:
    ```

- ### 查看GPU运行状态：
    Linux:`nvidia-smi`

    ```Linux
    (keras) frank@312LabW:~$ nvidia-smi
    Sat Nov 17 09:18:55 2018
    +-----------------------------------------------------------------------------+
    | NVIDIA-SMI 384.130                Driver Version: 384.130                   |
    |-------------------------------+----------------------+----------------------+
    | GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
    | Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
    |===============================+======================+======================|
    |   0  GeForce GTX TIT...  Off  | 00000000:01:00.0  On |                  N/A |
    | 22%   33C    P8    16W / 250W |  11928MiB / 12205MiB |      0%      Default |
    +-------------------------------+----------------------+----------------------+

    +-----------------------------------------------------------------------------+
    | Processes:                                                       GPU Memory |
    |  GPU       PID   Type   Process name                             Usage      |
    |=============================================================================|
    |    0      1627      G   /usr/lib/xorg/Xorg                           199MiB |
    |    0      3403      G   compiz                                        95MiB |
    |    0      7491      C   /home/wwg/.virtualenvs/cv/bin/python3      11511MiB |
    |    0     22641      C   .../frank/miniconda3/envs/keras/bin/python   106MiB |
    +-----------------------------------------------------------------------------+
    ```

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
    Linux: `ps -ef|grep jupyter `   
    > jupyter为指定的程序

- ### Linux 杀掉(kill)对应的进程
    Linux: `kill -9 911`    
    > 911为PID号。