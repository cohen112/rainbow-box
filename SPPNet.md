# SPPNet

Spatial Pyramid Pooling

空间金字塔池化：

​				1.CNN不同尺寸输入

​				2.仅仅对原图提取一次卷积特征

![img](https://upload-images.jianshu.io/upload_images/9389734-3707bfd126b9d417.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/975/format/webp)

原始的RCNN中需要对输入的图像进行裁剪/变形操作（Crop/Warp）进行候选区域的提取也就是进行了抠图和resize，这就会导致原始图像的损失和变形。将大小统一的经过预处理的图像作为卷积层的输入，也就和传统CNN模型比较接近了。

![img](https://upload-images.jianshu.io/upload_images/9389734-03e1aea9357d38c2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/990/format/webp)

在SPPnet中加入了SPP层，目的在于把不同大小规格图像产生的feature map进行一次结果统一的特殊pooling操作。

![img](https://upload-images.jianshu.io/upload_images/9389734-27d55911c18c1eee.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/653/format/webp)

由于FC层的存在，普通的CNN通过固定输入图片的大小来使得全连接层输入固定。作者不这样思考，既然卷积层可以适应任何尺寸，那么只需要在卷积层的最后加入某种结构，使得后面全连接层得到的输入为固定长度就可以了。在最后的卷积层和全连接层之间加入SPP层。具体做法是，在conv5层得到的特征图是256层，每层都做一次spatial pyramid pooling。先把每个特征图分割成多个不同尺寸的网格，比如网格分别为4*4、2*2、1*1,然后每个网格做max pooling，这样256层特征图就形成了16*256，4*256，1*256维特征，他们连起来就形成了一个固定长度的特征向量，将这个向量输入到后面的全连接层。



缺点：CNN中的conv层在微调时是不能继续训练的。它仍然是R-CNN的框架，离我们需要的端到端的检测还差很多。既然端到端如此困难，那就先统一后面的几个模块吧，把SVM和边框回归去掉，由CNN直接得到类别和边框可不可以？于是就有了Fast R-CNN。



参考来源 https://www.cnblogs.com/chaofn/p/9305374.html