## Conda常用命令

- ### 检查更新当前conda
    Linux: `conda update conda`

- ### 创建虚拟环境
    Linux: `conda create -n your_env_name python==x.x(2.7、3.6)`
    > your_env_name: 虚拟环境的名称， python==3.6指定python版本

- ### 激活虚拟环境
    Linux: `source activate your_env_name` or `conda activate your_env_name`

- ### 安装包到虚拟环境
    Linux: `conda install -n your_env_name package_name`

- ### 删除虚拟环境中指定的包
    Linux: `conda remove -n your_env_name  package_name`

- ### 退出虚拟环境
    Linux: `source deactivate` or `conda deactivate`

- ### 删除虚拟环境
    Linux: `conda remove -n your_env_name --all`

- ### 查看虚拟环境安装了哪些包
    Linux: `conda list`

- ### 查看系统存在的虚拟环境
    Linux: `conda env list`

- ### 更改 jupyter notebook kernel 路径(虚拟环境下运行)：
    Linux: `pip install ipykernel`  
    Linux: `python -m ipykernel install --user --name env_name`

- ### pip升级所有的包：
    Linux: `pip freeze --local | grep -v '^-e' | cut -d = -f 1 | xargs -n1 pip install -U`

- ### 清除安裝下载的原始安装文件
    Linux: `conda clean -tp`

- ### 导出Conda虚拟环境
    Linux: `conda env export -n my-environment -f my-environment.yml`
    > `my-environment`为要导出的虚拟环境的名字

- ### 根据`Environment.yml`安装新的虚拟环境
    Linux: `conda env create -f my-environment.yml`
    > `my-environment`为从其他电脑导出的虚拟环境包

- ### 上传项目到 Anaconda Cloud

    linux: `anaconda-project upload`

- ### 分享`jupyter notebook` 到 Anaconda Cloud

    Linux: `anaconda upload my-notebook.ipynb`

    > 查看：`http://notebooks.anaconda.org/<USERNAME>/my-notebook`   
    
- ### 下载他人分享在Anaconda Cloud的`Jupyter notebook`

    Linux: `anaconda download username/my-notebook`





- ### 安全地移除 Anaconda

    ```linux
    # Uninstall anaconda
    $ conda install anaconda-clean
    $ anaconda-clean
    $ rm -rf ~/anaconda3          # removes the entire anaconda directory
    $ rm -rf ~/.anaconda_backup   # anaconda clean creates a back_up of files/dirs, remove it
    ```
