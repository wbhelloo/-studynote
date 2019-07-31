## 批量修改·文件夹内文件夹·内文件的名字

### 此代码时候修改以下目录结构

    ├── test
    │     ├── 001                  
    │          ├── Img_0001.jpg
    |          ├── Img_0002.jpg
    |     |── 002
    │          ├── Img_2001.jpg
    |          ├── Img_2002.jpg     

```python
# 待修改文件的路径信息
Original_image_path = "../Dataset/Dataset_ZYL_21/test"
if not os.path.isdir(Original_image_path):
    print("Please change the Original_image_path")

# 设置要修改文件名的后缀
list = ['jpg','JPG' ]

# 设置新文件名的开始编号
count_dir = 100
count_file = 1000

# 遍历当前文件夹下的所有文件夹(即001,002文件夹)
for root, dirs, files in os.walk(Original_image_path, topdown=True):
    for dir in dirs:
        Ori_image_dir_path = Original_image_path + "/" + dir

        # 修改文件夹名字
        # New_image_dir_path = Original_image_path + "/" + str(count_dir)
        # os.rename(Ori_image_dir_path, New_image_dir_path)
        # count_dir += 1
        # print(New_image_dir_path)
        
        #  遍历当前文件夹内图片文件(即Img_0001.jpg)
        for root, dirs, files in os.walk(Ori_image_dir_path, topdown=True):
            for file in files:
                if not file[-3:] in list:
                    continue
                Ori_image_path = Ori_image_dir_path + "/" + file
                New_image_path = Ori_image_dir_path + "/" + str(count) + '.jpg'

                os.rename(Ori_image_path, New_image_path)
                count_file += 1

                print(New_image_path)
``` 