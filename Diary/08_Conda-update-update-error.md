## conda update conda 时报错

- ### conda update conda 无法更新

    Linux: `conda update conda` 时报下面的错误

    ```linux
    ~$ conda update conda
    Solving environment: done

    ## Package Plan ##https://stackoverflow.com/questions/49181799/conda-update-conda-permission-error

    environment location: /home/david/anaconda3

    added / updated specs: 
        - conda


    The following packages will be UPDATED:

        conda: 4.4.10-py36_0 --> 4.4.11-py36_0

    Proceed ([y]/n)? y

    Preparing transaction: done
    Verifying transaction: done
    Executing transaction: failed
    ERROR conda.core.link:_execute(481): An error occurred while uninstalling package 'defaults::conda-4.4.10-py36_0'.
    PermissionError(13, 'Permission denied')
    Attempting to roll back.

    Rolling back transaction: done

    PermissionError(13, 'Permission denied')
    ```

    > Executing transaction: failed


- ### 解决办法

    Linux: `sudo env "PATH=$PATH" conda update conda`


- ### 参考链接

    [https://stackoverflow.com/questions/49181799/conda-update-conda-permission-error](https://stackoverflow.com/questions/49181799/conda-update-conda-permission-error)