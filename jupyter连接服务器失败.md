#  jupyter连接服务器失败

### 问题：

jupyter notebook一直显示连接服务器，随后报错    **连接失败**：**到后台服务的连接没能建立, 我们会继续尝试重连, 请检出网络连接...还有服务配置.**

### 解决方案：

在命令行anaconda prompt中运行jupyter notebook，发现报错内核在不断重新启动最终出现 KernelRestarter: restart failed 内核重启失败

`pip install --upgrade ipykerne`

其他方法：

使用anaconda内生插件nb_conda `conda install nb_conda`





