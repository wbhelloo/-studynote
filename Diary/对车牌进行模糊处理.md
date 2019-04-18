## 对车牌进行模糊处理

> 本程序基于HyperLPR的开源包: [https://github.com/zeusees/HyperLPR](https://github.com/zeusees/HyperLPR)

### 运行前请确认安装了以下的包：

- 1: python == 3.6.8

- 2: openCV2 

- 3: hyperlpr    

    一键安装：`pip install hyperlpr`

### 完整代码：

```python
# 导入需要的包
from hyperlpr import *
import cv2
import os

# 待处理照片路径
Original_image_path = "Z:/vehicle/Released Vehicle Data/Vehicle Subset Data"
if not os.path.isdir(Original_image_path):
    print("Please change the Original_image_path")

# 设置要保存文件的路径
main_save_path = "Z:/vehicle/Released Vehicle Data"
save_path = main_save_path + "/Mask_Subset_Data_test"
if not os.path.isdir(save_path):
    os.mkdir(save_path)

# 遍历所有文件夹
count = 0
for root, dirs, files in os.walk(Original_image_path, topdown=True):
    for dir in dirs:
        Ori_image_dir_path = Original_image_path + "/" + dir
        # print(Ori_image_dir_path)
        # break

        output_image_path = save_path + "/" + dir
        if not os.path.isdir(output_image_path):
            os.mkdir(output_image_path)

        # 遍历所有文件夹内图片文件
        for root, dirs, files in os.walk(Ori_image_dir_path, topdown=True):
            for name in files:
                if not name[-3:] == 'jpg':
                    continue

                # ID = name.split('_')
                # 原始图片路径
                ori_img_path = Ori_image_dir_path + '/' + name

                # 读入图片
                ori_img = cv2.imread(ori_img_path)

                # 识别图片
                num = []
                num = HyperLPR_PlateRecogntion(ori_img)
                print(num)
                if num != []:
                    # 中值模糊
                    # cv2.medianBlur(ori_img[num_xy[1]:num_xy[3],num_xy[0]:num_xy[2]], 15)
                    num_xy = num[0][2]
                    media_img = cv2.medianBlur(ori_img[num_xy[1]:num_xy[3], num_xy[0]:num_xy[2]], 15)

                    # 修改原图像
                    ori_img[num_xy[1]:num_xy[3], num_xy[0]:num_xy[2]] = media_img
                    # plt.imshow(ori_img)
                    # break;

                    # 保存图片到指定文件夹并命名
                    output_image_path_name = output_image_path + "/" + name
                    cv2.imwrite(output_image_path_name, ori_img)
                    print(output_image_path_name)

                    # 计数器-1
                    count += 1
                    print("Oouput iamge count: %s" % count)
```
