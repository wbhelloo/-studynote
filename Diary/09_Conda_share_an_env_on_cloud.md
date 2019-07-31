## 导出虚拟环境安装文件并在另一台电脑安装

1. ### 导出Conda虚拟环境

    Linux: `conda env export -n my-environment -f my-environment.yml`
    > `my-environment`为要导出的虚拟环境的名字，   
    并拷贝此安装文件到其他要创建虚拟环境的电脑。

2. ### 根据`Environment.yml`安装新的虚拟环境

    Linux: `conda env create -f my-environment.yml`
    > `my-environment`为从其他电脑导出的虚拟环境包


## 分享虚拟环境到Anaconda Cloud.

1. ### 安装Anaconda 客户端
    
    Linux: `conda install anaconda-client`

2. ### 登陆 Cloud 账户

    Linux: `anaconda login`

    > 需要首先在 [https://anaconda.org/](https://anaconda.org/) 创建个人账户。

3. ### 导出虚拟环境包

    Linux: `conda env export -n my-environment -f my-environment.yml`
    > `my-environment`为虚拟环境的名字.

4. ### 上次虚拟环境安装文件到Cloud
    
    Linux: `anaconda upload my-environment.yml`

    ```
    (cv) frank@gpu-server:~/work$ anaconda upload torch-re-id.yml
    Using Anaconda API: https://api.anaconda.org
    Using "zjcao" as upload username
    Processing 'torch-re-id.yml'
    Detecting file type...
    File type is "env"
    Extracting environment attributes for upload
    Creating package "torch-test"
    Creating release "2019.07.31.105612"
    Uploading file "zjcao/torch-test/2019.07.31.105612/torch-re-id.yml"
    uploaded 7 of 7Kb: 100.00% ETA: 0.0 minutes
    Upload complete

    environment located at:
    https://anaconda.org/zjcao/torch-test
    ```

    > Cloud查看: `http://envs.anaconda.org/<USERNAME>`

5. ### 其他用户根据云端的虚拟环境安装文件创建新的虚拟环境

    Linux: `conda env create user/my-environment`

    ```linux
    (cv) frank@gpu-server:~/work$ conda env create zjcao/torch-test
    Collecting package metadata (repodata.json): done
    Solving environment: done
    Preparing transaction: done
    Verifying transaction: done
    Executing transaction: done
    #
    # To activate this environment, use
    #
    #     $ conda activate torch-test
    #
    # To deactivate an active environment, use
    #
    #     $ conda deactivate

    (cv) frank@gpu-server:~/work$ conda env list
    # conda environments:
    #
    base                     /home/frank/anaconda3
    cv                    *  /home/frank/anaconda3/envs/cv
    tf                       /home/frank/anaconda3/envs/tf
    torch                    /home/frank/anaconda3/envs/torch
    torch-test               /home/frank/anaconda3/envs/torch-test
    ```

    > 注意：没有`.yml`

6. ### 激活虚拟环境

    Linux: `source activate my-environment`


> 参考源文档：  

[http://docs.anaconda.com/anaconda-cloud/user-guide/getting-started/#sharing-environments](http://docs.anaconda.com/anaconda-cloud/user-guide/getting-started/#sharing-environments)