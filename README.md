## 仓库说明：

本仓库是yolov5实现行人车辆检测。

## 环境说明：

python version >= 3.6

pytorch version >= 1.7

onnx verison >= 1.11

## 准备数据
VisDrone2019数据集：通过网盘分享的文件：visdrone2019.zip
链接: https://pan.baidu.com/s/1lMtNKyDI8pFi9q4kG6yeCA?pwd=1112 提取码: 1112 

数据集解压后放在datasets文件夹下。
更改修改配置文件VisDrone.yaml文件：
打开yolov5/yolov5-master/data文件夹下的VisDrone.yaml文件，将其中path参数修改为VisDrone2019文件夹所在的路径。
修改yolov5m.yaml文件（若训练其他yolo网络修改相应的yaml文件即可），打开yolov5/yolov5-master/models文件夹下的yolov5m.yaml文件，将其中nc参数修改为VisDrone2019数据集训练的类别，即nc：10。


## 训练模型
修改train.py文件：在yolov5/yolov5-master下的train.py文件，需要修改几个default参数
我主要更改了–weights、–cfg、–data、–epoch以及–batch-size的默认参数
训练脚本如下所示：
```python
python train.py --data mask.yaml --cfg yolov5m.yaml --weights "" --batch-size 64
                                       yolov5s                               64
                                       yolov5l                                24
                                       yolov5x                                16
```
训练完成后，过程文件及训练模型，会保存在runs/文件夹中。

## 模型预测
测试训练好的模型：修改detect.py中的–weights参数，运行detect.py文件，即可看到检测效果。
主要修改detect.py中的配置文件如下：
 parser.add_argument('--weights', nargs='+', type=str, default=ROOT / 'weights/yolov5m.pt', help='model path(s)')

```python
python detect.py --source data/images --weights ./runs/train/exp/weights/best.pt --conf 0.5
```
测试结果会在"runs/detect"生成：
<img src="./photo/image.jpg">



## 参考库：

https://github.com/ultralytics/yolov5

https://github.com/soloIife/yolov5_for_rknn


## 技术交流群：

QQ群：810456486



