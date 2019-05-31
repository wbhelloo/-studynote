### linux 程序设置后台运行及查看方法

- linux 程序设置后台运行

    ```
    nohup commond &
    ```
    
- 查看后台进程

    ```
    ps -u frank
    ```
    
- 查看指定端口的占用情况

    ```
    lsof -i:8888
    ```
    
- 终止进程

    ```
    kill 进程号
    ```
