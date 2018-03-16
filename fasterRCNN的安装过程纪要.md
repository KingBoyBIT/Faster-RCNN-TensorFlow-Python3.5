# fasterRCNN的安装过程纪要

## 安装anaconda3

- 官网下载安装，注意不要取消添加环境变量的选项

- 打开prompt,默认conda是安装了的，之后将conda添加清华的镜像，注意https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/直接在这里找添加的方式

- `conda update conda`

- `conda update anaconda`

- `conda update --all`

## 安装TensorFlow

- 用`conda create -n tensorflow python=3.5` 来建立TensorFlow的环境
- `pip install tensorflow-gpu` 安装TensorFlow的GPU版
- 添加Spyder
- 安装cudnn6，CUDA8
- cudnn6要拷贝到cuda8的目录下面，bin,lib,include
- 使用测试代码测试安装结果

## 安装fasterRCNN

- `https://github.com/dBeker/Faster-RCNN-TensorFlow-Python3.5` 中的说明来安装TensorFlow版的fasterRCNN
- 准备安装：Cpython,python-opencv,easydict
- 激活TensorFlow的prompt`activate tensorflow`
- `pip install Cython --install-option="--no-cython-compile"` 来安装Cpython
- `pip3 install opencv-python` 来安装opencv-python
- `pip3 install easydict` 来安装easydict
- 将GitHub上的代码解压缩到C:
- 切换目录 `C:\Faster-RCNN-TensorFlow-Python3.5-master\data\coco\PythonAPI` 运行`python setup.py build_ext --inplace` 和`python setup.py build_ext install`
- 日了狗了，运行train.py会爆出import PIL错误，PIL只在py27下有，安装pillow代替
- ​


# 替代思路

在https://github.com/delftrobotics/keras-retinanet中下载Keras，通过readme来配置，目前来看没有报错，但是缺少数据。



# 新尝试

- 安装anaconda，TensorFlow后，到https://github.com/dBeker/Faster-RCNN-TensorFlow-Python3.5这里clone一个
- `conda install cython` 
- `conda install opencv`
- `pip install easydict`
- 一路CD到./data/coco/PythonAPI，运行：
- `python setup.py build_ext --inplace`
- `python setup.py build_ext install`
- 这里可能会出现VS的编译错误，更新为2015 update3后问题解决
- 下载VOC2007devkit，目录为data/VOCDevkit2007/VOC2007，将VOC2007直接放在data目录下面新建的VOCDevkit2007这个目录里面
- 下载tf的VGG16模型到data\imagenet_weights\vgg16.ckpt，注意这里名字是vgg16没有下划线
- 编译
- cd到fasterRCNN的目录，运行activate tensorflow
- pip install pyqt5
- 运行python train.py
- 修改lib\config.py中的30行，将其改为30可以简单的循环几轮，看demo是否运行成功