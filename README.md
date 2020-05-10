# Plate-location-and-recognition-based-on-FasterRCNN-and-CNN
电子科技大学，信通学院，综合课程设计<br>
针对不同的情况，本文综合运用了HSV色彩空间、边缘检测以及Faster-RCNN神经网络等工具，实现了对车牌的定位。利用两个卷积神经网络CNN完成对字符的识别。附带了车牌识别相关数据集，由于文件较大请移步：<br>[百度云链接](https://pan.baidu.com/s/1ugnH5fGQ1ZP2Kyft65wngw)  提取码：shdo<br>
# FasterRCNN实现车牌定位
Faster-RCNN是一种建立在Fast-RCNN基础之上的网络，其克服了后者检测耗时长的缺点，将候选区域生成、分类检测集成在同一个网络之中，实现了端到端的训练。Faster-RCNN的结构主要分为三大部分，第一部分是共享卷积层用于生成共享特征图；第二部分是候选区域生成网络RPN；第三部分是对候选区域进行分类的网络Classifier。如图：![FasterRCNN](./Faster-RCNN/img/FRCNN.jpg)
## RPN网络
RPN网络通过在共享特征图上滑动的窗口为每一个像素点生成面积、比例为预定值的目标框，称之为anchor，通过Softmax层判断每一个anchor是前景还是背景，接着利用bboxreg层对判定为前景的anchor进行坐标修正。（这里是对anchor坐标的第一次修正）。最后输出候选目标区域Proposal。<br>
![RPN](./Faster-RCNN/img/RPN.jpg)
## Classifier
候选目标区域Proposal与共享特征图一同送入Classifier。Classifer的结构与RPN类似，但是多了一个RoI Pooling层。RoI Pooling是一种特殊的池化层用于从共享特征图中提取Proposals的特征，并送入全连接层分类。接着Softmax层判断Proposal具体为哪一类别的事物。bboxreg对anchor坐标的第二次修正。最后输出图片上目标的种类（Category）和坐标(Coordinats)。<br>
![classifier](./Faster-RCNN/img/classifier.jpg)
## Faster-RCNN处理图片的完整流程
![process](./Faster-RCNN/img/process.jpg)
## 最终定位效果
可以对易受环境颜色干扰的车牌和新能源车牌粗略定位<br>
![result1](./Faster-RCNN/img/result1.jpg) ![result2](./Faster-RCNN/img/result2.jpg)<br>
由于网络文件较大，获取请移步：[百度云链接](https://pan.baidu.com/s/1ivUqZC3dtqKCw75f2MkFPw)  提取码：q83s<br>
