
### Jupyter Notebook 远程访问设置

- 生成默认配置文件

    ```jupyter notebook --generate-config```

- 生成访问密码(token)

    ```
    $ jupyter notebook password
    Enter password:  ****
    Verify password: ****
    [NotebookPasswordApp] Wrote hashed password to /Users/you/.jupyter/jupyter_notebook_config.json
    ```

- 打开`/Users/you/.jupyter/jupyter_notebook_config.json` 复制密码

    ```
    {
      "NotebookApp": {
        "password": "sha1:2cc0d2f1d446:6f59022c55228054f6f78ecf******************"
      }
    }
    ```

- 修改`./jupyter/jupyter_notebook_config.py`中取消注释如下内容，并修改如下。

    ```
    c.NotebookApp.ip='0.0.0.0'
    c.NotebookApp.password = u'密码'
    c.NotebookApp.open_browser = False
    c.NotebookApp.port =8888 
    ``` 

- 参考内容

    https://jupyter-notebook.readthedocs.io/en/latest/public_server.html#notebook-server-security
    
- 完    