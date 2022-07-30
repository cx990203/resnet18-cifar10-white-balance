# resnet18-cifar10
最基础的resnet18进行cifar10数据集分类处理。</br>
工程文件说明：</br>
resnet.py--resnet18模型存放文件</br>
train.py--训练脚本，默认导入cifar-10数据集</br>
utils.py--工具函数存放脚本</br>
white_balance_val.py--白平衡测试脚本（应付作业用的），用于测试图像在经过色调调整后的推理准确率，以及再加上白平衡处理之后的准确率。当然由于cifar-10数据集图像像素较小，有一定效果但并不是很好。</br>
模型工程百度云（内含上述测试的模型参数文件）：链接：https://pan.baidu.com/s/1NHMFLojHWHT56NxQA0Oh9Q </br>
提取码：eazm </br>

## white_balance_val.py文档说明
图像色调调整主要在HSV空间当中进行。</br>
共使用五种常见白平衡方法对图像进行处理：均值、完美反射、灰度世界假设、基于图像分析的偏色检测及颜色校正、动态阈值法。</br>
白平衡源码放置于utils.py文件当中。</br>
算法源码摘自博客（如有侵权，请联系删除）：https://blog.csdn.net/weixin_34910922/article/details/109106029</br>
算法测试结果：</br>
<div align="center">
  <img src=https://user-images.githubusercontent.com/77096562/181867027-2c16f7ad-ba0d-4174-901c-15ef40fedb9f.png>
  
  |   图像调整操作        | 调整后原图推理准确率 |      mean      |  perfect reflective   |  grey world  | image analysis  | dynamic threshold |
  | :---                 |  :---:             |     :---:      |          :---:        |     :---:    |       :---:     |        :---:      |
  |无任何操作             |81.77%              |      ---       |           ---         |      ---     |        ---      |         ---       |
  |H=(H-100)%360(色调调整)|70.88%              |73.83%          |70.22%                 |73.80%        |72.60%           |69.71%             |
  |S=S/2(减小饱和度)      |72.36%              |74.16%          |72.46%                 |74.16%        |74.11%           |69.86%             |
  |V=V/2(减小亮度)        |58.28%              |60.83%          |61.09%                 |60.22%        |61.29%           |62.91%             |
  |S=S+(1-S)/2(增大饱和度)|48.60%              |55.88%          |48.72%                 |55.96%        |55.68%           |52.61%             |
  |V=V+(1-V)/2(增大亮度)  |43.58%              |46.85%          |42.46%                 |47.03%        |47.71%           |43.15%             |
</div>

