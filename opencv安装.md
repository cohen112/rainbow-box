#  opencv安装

版本信息：opencv 3.3.1.11 + python3.6 + numpy 1.16[注意在tensorflow安装中有可能要求numpy版本不能太高，但太低又会导致opencv异常]



### 1.下载对应版本的opencv_python whl文件（方便安装到anaconda的虚拟环境中）

[网址1](https://pypi.org/project/opencv-python/3.3.1.11/#files) [可以下载到老版本的opencv 3.1.0-4.1.0]

[网址2](https://www.lfd.uci.edu/~gohlke/pythonlibs/) [可以下载2.4, 3.4 ,4.1+contrib版本]

###  2.再anaconda prompt中activate tensorflow-gpu虚拟环境  ,在指令行中打开whl文件目录，进行安装

`activate tensorflow-gpu`

`pip install opencv_python-3.3.1.11-cp36-cp36m-win_amd64.whl`

###  3.测试代码（在jupyter notebook中可能会不正常）



```python 
import cv2
img = cv2.imread('F:/1.jpg')  #注意1.绝对路径不能有中文字符 2.路径的最后一个斜线应该是/，前面的应该是\
cv2.namedWindow("w")  
cv2.imshow('w',img)
cv2.waitKey(0)
```



#  opencv常见异常

###  1.ModuleNotFoundError: No module named 'numpy.core._multiarray_umath' 错误（20190201）

原因：numpy版本问题

解决方法：

```python
conda list numpy #查看numpy版本
#或 
pip show numpy
pip install --upgrade numpy  #更新numpy版本
#或
pip  install -i https://pypi.tuna.tsinghua.edu.cn/simple --upgrade numpy
#如果受限于tensorflow版本，numpy需要安装特定版本才行
pip install numpy==1.16.4
```

###  2.cv2.error: C:\projects\opencv-python\opencv\modules\highgui\ src\window.cpp:331: error: (-215) size.width>0 && size.height>0 in function cv::imshow
imread时出现的问题  error: (-215) size.width>0 && size.height>0

原因：图片路径出现问题

解决方法：检查路径

```python
#1.F:/1.jpg       错:F:\1.jpg
#2.F:\ad/1.jpg    错:F:/ad/1.jpg
#3.F:\图片/1.jpg   错:F:\tupian/1.jpg
```

