# Yolov8-Drillbit-Detection

A task for drillbit detection using Yolov8 models

本仓库的任务是刀具检测与计数。刀具有两种，**刀头（S形）**和**刀尾（圆形平面）**分别以**tool_b**和**tool**为标签。每张图片大小约为$5000*5000$，约有上千个刀具，每个刀具大小约为$30*30$。


本仓库主要分为三个部分：

1. Preprocessing 预处理
2. Train 训练
3. Predict 预测

### 1. Preprocessing 预处理

将原先大图切片成$640*640$的小图。

Slicing_txt2txt.py ： 可将有标签（txt格式，其他自己改）或无标签的图像切片，转换成VOC格式并保留标签的相对位置。

Show_VOC_tags.py ： 将转换完成的图片和标签可视化。


已将未标注的图片切片并上传至Roboflow。


### 2. Train 训练

用Yolov8模型进行训练。

train_yolov8_object_detection_on_custom_dataset.ipynb ： 使用此Jupyter Notebook，可以直接用Roboflow导出的数据进行训练并将训练得到的权重上传。记得修改把Roboflow的api_key修改成自己的，那一段代码可以直接在Roboflow导出数据集时复制得到。


第一版： Yolov8s $batchsize=4~epoch=100~~~~~mAP=79.2\%~Precision=97.7\%~Recall=74.2\%$

已部署到Roboflow上进行自动标注。


### 3. Predict 预测

将需要进行预测的图片切分，用小图预测，再将结果映射回大图并去重。

Predict.ipynb ：使用此Jupyter Notebook进行预测。


已实现初步结果。
