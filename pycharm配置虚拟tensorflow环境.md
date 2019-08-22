##  pycharm配置虚拟tensorflow环境

###  1. ModuleNotFoundError: No module named 'PIL'

![1564898863080](C:\Users\msi-pc\AppData\Roaming\Typora\typora-user-images\1564898863080.png)

解决方法:

​    运行命令:pip install pillow

##  2.ImportError: cannot import name imread

python使用scipy import imread报错，需要用pip3安装pillow或者进行降级

降级操作：

`pip install scipy==1.2.1`

##  3.出现ModuleNotFoundError: No module named 'matplotlib'

使用`pip install matplotlib`进行安装，如果安装不成功需要到[官网](https://pypi.org/project/matplotlib/#files)下载whl安装包进行安装（一次不行可多试几次）

在安装包目录下进行安装

`pip install  matplotlib-3.1.1-cp36-cp36m-win_amd64.whl`