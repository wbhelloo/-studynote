## `pipreqs`查找python项目依赖包并生成`requirements.txt`

#### `pipreqs`安装

    pip install pipreqs


#### pipreqs的使用

在项目的根目录下 运行 ```pipreqs ./``` 命令即可, 如：

    pipreqs ./

> 运行时有可能会报如下错误：   
UnicodeDecodeError: 'cp949' codec can't decode byte 0xe5 in position 672: illegal multibyte sequence

这是由于编码问题所导致的，运行时加上encoding参数即可，如下

     pipreqs ./ --encoding=utf8

运行结果

    (cv) E:\Pycharm\iDetector>pipreqs ./ --encoding=utf8
    INFO: Successfully saved requirements file in ./requirements.txt


#### 详细用法：

    pipreqs [options] <path>

- ```use-local``` 仅使用本地包信息而不是查询PyPI

- ```pypi-server <url>``` 使用自定义PyPi服务器

- ```proxy <url>``` 使用Proxy，参数将传递给请求库

    > 你也可以设置终端中的环境参数，如：   
    ```$ export HTTP_PROXY="http://10.10.1.10:3128"```   
    ```$ export HTTPS_PROXY="https://10.10.1.10:1080"```

- ```debug``` 打印调试信息

- ```ignore <dirs>...``` 忽略额外的目录

- ```encoding <charset>``` 使用编码参数打开文件

- ```savepath <file>``` 保存给定文件中的需求列表

- ```print``` 输出标准输出中的需求列表

- ```force``` 覆盖现有的 ```requirements.txt```

- ```diff <file>``` 将requirements.txt中的模块与项目导入进行比较

- ```clean <file>``` 通过删除未在项目中导入的模块来清理requirements.txt


本节内容参考了：[https://pypi.org/project/pipreqs/](https://pypi.org/project/pipreqs/)
 </file></file></file></charset></dirs></url></url></path>
