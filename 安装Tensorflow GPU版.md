#         安装Tensorflow GPU版

##  1.打开Anaconda Prompt,，进入anaconda指令行界面，切换清华镜像：

`conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/`

`conda config --set show_channel_urls yes`

##  2.创建虚拟运行环境

`conda create -n tensorflow-gpu python=3.6`

新建一个名字叫“tensorflow-gpu”，python版本为3.6的运行环境，此环境与Anaconda中其它环境隔离。红框中的软件包也会随之安装，输入“y“和回车后开始安装。

（注意最好不要使用py3.7，否则可能会报错）

然后会出现一些软件安装包的提示（问你是否确认安装）：输入 y 按回车

##  3.激活并进入所创建tensorflow-gpu环境中

`activate tensorflow-gpu`

##  4.升级到pip最新版，防止出错

`python -m pip install --upgrade pip`

## 5.安装tensorflow 1.7.0版本和依赖

`pip install --ignore-installed --upgrade tensorflow-gpu==1.7.0`

备用1：`pip3 install -i https://pypi.tuna.tsinghua.edu.cn/simple/ --upgrade tensorflow-gpu==1.7.0 `

备用2：`pip install --upgrade tensorflow-gpu-1.4.1-cp35-cp35m-manylinux1_x86_64.whl`(离线安装)

安装完毕

## 6.测试 tensorflow

```
import tensorflow as tf
hello = tf.constant(‘Hello, TensorFlow!’)
sess = tf.Session()
print(sess.run(hello))
```

输出：b’ Hello, TensorFlow!

版本信息:

```
import tensorflow as tf
tf.__version__
```

卸载：`pip uninstall tensorflow-gpu`



# 安装问题总结(WIN10+CUDA9.0+TF1.7.0)

## 1.安装镜像问题

### 清华镜像

```python
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/conda config --set show_channel_urls yes
```

###  中科大镜像

修改C://Users/用户名下 .condarc文件(我的电脑未找到)，一般首次执行conda config会自行创建

```python
channels:
  - https://mirrors.ustc.edu.cn/anaconda/pkgs/free/
ssl_verify: true
show_channel_urls: true
```

## 2.FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy

![01](E:\5 技术文档\01.png)

numpy版本过高，需要降级

`pip uninstall unmpy`

`pip install numpy==1.13.3`





