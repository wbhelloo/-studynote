## Linux常用命令: tar、zip 压缩和解压缩命令

### ```zip```的用法

### 基本用法是：

    zip [参数] [打包后的文件名] [打包的目录路径]

### 常用参数：

```-a``` 将文件转成ASCII模式

```-F``` 尝试修复损坏的压缩文件

```-h``` 显示帮助界面

```-m``` 将文件压缩之后，删除源文件

```-n``` 特定字符串    不压缩具有特定字尾字符串的文件

```-o``` 将压缩文件内的所有文件的最新变动时间设为压缩时候的时间

```-q``` 安静模式，在压缩的时候不显示指令的执行过程

```-r``` 将指定的目录下的所有子目录以及文件一起处理

```-S``` 包含系统文件和隐含文件（S是大写）

例如：

- 将指定目录/tmp压缩成test.zip文件

        zip -r test.zip tmb/


## ```unzip```的用法

### 基本用法是：

    unzip [参数] [待解压缩文件]

在linux下解压zip文件，最简单的方式就是unzip命令直接跟上要解压的zip文件。

    unzip [待解压缩文件]

### 常用参数：

```-n``` 解压缩时不要覆盖原有的文件；

```-o``` 不必先询问用户，unzip执行后覆盖原有的文件；

```-P [密码]``` 使用zip的密码选项；

```-q``` 执行时不显示任何信息；

```-d [目录]``` 指定文件解压缩后所要存储的目录；

例如：

- 将压缩文件text.zip在当前目录下解压缩。

         unzip test.zip

- 将压缩文件test.zip在指定目录/tmp下解压缩，如果已有相同的文件存在，要求unzip命令覆盖原先的文件。

        unzip -o test.zip -d tmp/


## `tar` 的用法

- ### 将所有 `.jpg` 的文件打成一个名为 `all.tar` 的包
Linux: `tar -cf all.tar *.jpg`
> `-c` 是表示产生新的包，`-f` 指定包的文件名。

- ### 将所有 `.gif` 的文件增加到 `all.tar` 的包里面去
Linux: `tar -rf all.tar *.gif`
> `-r` 是表示增加文件

- ### 更新原来 `tar` 包 `all.tar` 中 `logo.gif` 文件
Linux: `tar -uf all.tar logo.gif`
> `-u` 是表示更新文件

- ### 列出 `all.tar` 包中所有文件
Linux: `tar -tf all.tar`
> `-t`是列出文件的意思

- ### 将所有 `.jpg` 的文件打成一个 `tar` 包，并且将其用 `gzip` 压缩，生成一个 `gzip` 压缩过的包，包名为 `all.tar.gz`
Linux: `tar -czf all.tar.gz *.jpg`

- ### 解压缩 `all.tar.gz`
Linux: `tar -xzf all.tar.gz`

- ### 解压举例

        `tar –xvf file.tar`         // 解压 tar 包 
        `tar -xzvf file.tar.gz`     // 解压 tar.gz 
        `tar -xjvf file.tar.bz2`    // 解压 tar.bz2 
        `tar –xZvf file.tar.Z`      // 解压 tar.Z 
        `unrar e file.rar`          // 解压 rar 
        `unzip file.zip`            // 解压 zip 

- ### 总结

        `*.tar` 用 `tar –xvf` 解压 
        `*.gz` 用 `gzip -d`或者`gunzip` 解压 
        `*.tar.gz`和`*.tgz` 用 `tar –xzf` 解压 
        `*.bz2` 用 `bzip2 -d`或者用`bunzip2` 解压 
        `*.tar.bz2`用`tar –xjf` 解压 
        `*.Z` 用 `uncompress` 解压 
        `*.tar.Z` 用`tar –xZf` 解压 
        `*.rar` 用 `unrar e`解压 
        `*.zip` 用 `unzip` 解压
