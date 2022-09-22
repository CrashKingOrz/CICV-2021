# CICV-2021

### 简介

- 赛事链接：[CICV2021-任务大厅](https://developer.china-icv.cn/homePage#/cicvAlgo)
- 赛事简介：本任务基于虚拟仿真场景下的图像数据，评价高速公路场景种低速异型机动车进检测性能，异型车辆如图1所示，遮挡或截断比例小于70%、长边像素大于20的上述异型机动车辆均需要识别，并输出车辆的二维边界框（BoundingBox）。当目标被遮挡时，边界框需要包含目标被遮挡的部分，当目标被截断时（目标的一部分在镜头外），边界框只需包含目标在图像内可见部分即可。
- 任务排名：**1**/50

- 技术方案：
  - YOLO v5目标检测：基于YOLOv5 X
  - 数据集：bdd15k

### 如何运行

#### Docker

- Docker镜像下载：链接：https://pan.baidu.com/s/1eZRAL8lcO6dmFKi9tNtB9w?pwd=jack  提取码：jack 

- 加载Docker镜像

```shell
docker load -i crashking.tar
```

- 运⾏并进⼊docker容器，并建⽴⽂件⽬录映射：注意替换下⾯的提⽰为测试数据路径！

```shell
docker run -it --name="crashking" -v 【该位置替换为宿主机测试机路径】:/challenge_1/task7 update/crashking /bin/bash
```

- 进入工作目录

```shell
cd /workspace/CrashKing
```

- 进⼊CrashKing⽬录并执⾏代码： 
  - 注意若没有GPU，则把下述命令参数 --device 0, 1 删除再运⾏，即CPU运⾏ 
  - 若GPU数量很多，可以更改 --device 后⾯的参数太增减使⽤的GPU

```shell
python3 detect.py --source /challenge_1/task7 --project /challenge_1/task7_res
ult --device 0, 1
```

- 运⾏结果 `/challenge_1/task7_result/CrashKing` ⽬录下