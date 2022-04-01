# XLPNet：一个基于纯卷积神经网络的轻量化车牌检测与识别算法

<div align=center>
<img src="./examples/XLPNet_600×300.png"/>
</div>

## 1 详细介绍见CSDN
[XLPNet车牌识别算法详解系列文章](https://blog.csdn.net/qq_42891019/category_11691340.html?spm=1001.2014.3001.5482)
欢迎点赞收藏！

## 2 项目简介
- 一个诞生于2022年，基于纯卷积神经网络结构的**车牌检测与识别系统**
- XLPNet分为车牌检测与车牌字符识别两部分，具备**轻量化**、**运行高效**的特点
- 算法上具备一些新颖的设计与思考，并非现有方案的简单集成
- 基于**pytorch**构建完整的网络结构与训练体系，支持GPU/多GPU训练
- 提供完整的**opencv调用程序**（包括python版本和C++版本），可以完全摆脱深度学习框架的限制，便于在多种不同平台和系统（Windows/Linux/Raspbian）直接或间接部署使用

很多细节上参考了我之前的工作SLPNet：[https://github.com/JackEasson/SLPNet_pytorch](https://github.com/JackEasson/SLPNet_pytorch)

XLPNet可视为SLPNet的改进版
<div align=center>
<img src="./examples/SLPNet.JPG"/>
</div>

## 3 目前完成度
- [x] 车牌检测（pytorch模型训练与opencv调用）
- [ ] 车牌识别
- [ ] 完整系统整合

## 4 示例
<div align=center>
<img src="./examples/detection_show.jpg" width=800/>
</div>

## 5 使用
详见博客：(https://blog.csdn.net/qq_42891019/article/details/123797612)[https://blog.csdn.net/qq_42891019/article/details/123797612]
### 5.1 环境要求
pytorch >= 1.6.0<br>
opencv >= 4.2.0<br>
tqdm<br>
numpy<br>
### 5.2 使用
#### 5.2.1 训练
可以提前修改``config.py``中的内容，大部分超参数可以通过此文件修改
- CPU / 单GPU训练：
``python train.py --device 'cpu' / 0 / 1/ ... --epoch xxx --batch_size xxx --savedir xxx``
- CPU / 单GPU / 多GPU并行训练：
``python train_multi_gpu.py --device 'cpu' / 0 / 1/ ... --epoch xxx --batch_size xxx --savedir xxx``
注意：这里多GPU训练所得的模型需要转换保存为普通模型，使用``trans_tools.py``中的
``multi_gpu2normal_model()``函数处理。
