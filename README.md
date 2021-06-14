# 1、设计目的
为了更加深入的了解Android开发，我最初是打算设计是建立一个相册或视频相关的多媒体的应用，但一次偶然的机会我看到了在github中一个框架，该框架中定义了许多有关图片和视频相关操作的方法，而且能够获取到手机本地的文件，而不像之前的应用需要导入到drawable中或在网上获取，于是本次课程设计我决定利用github
[https://github.com/LuckSiege/PictureSelector](https://github.com/LuckSiege/PictureSelector)的开源框架做一个能够查看手机后台存储数据的应用，这样方便的找出手机中存储在各个位置的图片音乐视频等，比如手机拍摄的图片，本地下载的视频，或者本地下载的音乐等，在选择时进行预览方便选择，类似于手机相册。

# 2、功能描述

 1. 预览查看手机存储的照片，视频和音频，可以通过应用找到手机中存储的各类型照片，视频和音频，包括png，jpg，jpeg等格式
 2. 单选或多选手机本地存储的照片，音频和视频，将选择的照片视频音频返回到首页显示
 3. 拍照，录像或录音，将结果返回到首页展示
 4. 在首页播放选择的照片视频和音频
# 3、详细设计
## 3.1 系统业务逻辑
## 业务逻辑流程图
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210614170042924.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1ODA4NzAw,size_16,color_FFFFFF,t_70)

## 3.2 系统功能模块设计
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021061417005155.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1ODA4NzAw,size_16,color_FFFFFF,t_70)

    

## 3.3 系统界面设计

 1. 首页：显示自己选择的文件。
 2. 操作选项页面，在首页点击后进入操作选择页面，可以选择是添加照片和视频还是音频，亦或者是拍照。
 3. 本地文件展示页面：将手机本地的文件（图片，视频，音频）以类似手机相册的方式显示，可以进行选择和预览
 4. 文件预览页面：点击想要选择的文件，会预览文件




# 4、程序实现

首先由于我用了第三方的集成框架，所以首先要利用gradle导入
allprojects {
   repositories {
      jcenter()
      maven { url 'https://jitpack.io' }
   }
}
然后建立layout中的xml文件，首先首页利用RecyclerView来便于将选择的图片进行排列，在利用相对布局和imageview以及库中的layout将图片视频等展示出来。
在MainActivity中，利用getviewbyid获取到layout中的ui控件，
new一个GridImageAdapter来存放选择的文件，然后判断利用库中集成的函数判断存放的文件的类型，利用switch函数利用集成的不同方法来打开各自对应的文件。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210614170101382.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1ODA4NzAw,size_16,color_FFFFFF,t_70)

而想要获取到手机本地的文件，还要申请到写的权限
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210614170109485.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1ODA4NzAw,size_16,color_FFFFFF,t_70)

然后给ui控件设计点击相应监听器，利用控件的getid判断响应事件，在每个对应的事件中利用库中的函数将手机本地的相册显示并进行相关的操作。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210614170115230.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1ODA4NzAw,size_16,color_FFFFFF,t_70)

# 5.运行结果

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210614170123152.png)![在这里插入图片描述](https://img-blog.csdnimg.cn/20210614170127662.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1ODA4NzAw,size_16,color_FFFFFF,t_70)

选择相册：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210614170136744.png)![在这里插入图片描述](https://img-blog.csdnimg.cn/20210614170139745.png)![在这里插入图片描述](https://img-blog.csdnimg.cn/20210614170149392.png)



         
左边是我的应用的界面，右边是模拟器中自带的图库的界面，可以看到该应用找到了该模拟器中包括图片的所有文件夹，也获取到了手机本地保存的所有图片和视频。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210614170201572.png)![在这里插入图片描述](https://img-blog.csdnimg.cn/20210614170205729.png)![在这里插入图片描述](https://img-blog.csdnimg.cn/2021061417020910.png)



可以点击图片进行预览，也可以左右滑动选择不同的相册。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210614170215310.png)![在这里插入图片描述](https://img-blog.csdnimg.cn/20210614170219150.png)![在这里插入图片描述](https://img-blog.csdnimg.cn/20210614170223137.png)



选择的图片会返回首页进行展示，在首页也能进入查看页面



![在这里插入图片描述](https://img-blog.csdnimg.cn/20210614170229731.png)![在这里插入图片描述](https://img-blog.csdnimg.cn/20210614170233304.png)![在这里插入图片描述](https://img-blog.csdnimg.cn/2021061417023767.png)


当选择音频时，显示本地的所有音频，并在点击后能进行播放
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021061417025487.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1ODA4NzAw,size_16,color_FFFFFF,t_70)![在这里插入图片描述](https://img-blog.csdnimg.cn/20210614170301169.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1ODA4NzAw,size_16,color_FFFFFF,t_70)


在选择视频后也能进行播放和选择到首页
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210614170309269.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1ODA4NzAw,size_16,color_FFFFFF,t_70)![在这里插入图片描述](https://img-blog.csdnimg.cn/20210614170313465.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1ODA4NzAw,size_16,color_FFFFFF,t_70)![在这里插入图片描述](https://img-blog.csdnimg.cn/2021061417031876.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1ODA4NzAw,size_16,color_FFFFFF,t_70)
还能够进行录视频，拍照，录音。

# 6、总结

 - 本次实验我用到了github中的开源库，其中有许多没有在课堂中学过的知识，比如文件操作权限的获取，开源库的导入，对于录像，拍照，录视频等不同拍摄的实现过程。
但也有一些学过的
 -  知识获得了加深，比如layout的页面设计中如何将图片排列整齐，如何学习使用RecyclerView；在为控件添加监听事件时利用view的getid和switch来给不同的控件添加事件；利用adapter适配器来放入照片和视频等不同的文件，并在adapter中为每个图片，视频等添加各自的点击响应事件，来完成在首页选择文件的查看。
 - 这个系统也有许多可以改进的地方，比如在导入库和进行使用时出现很多问题，其中解决了一些问题，但也有一些没有解决，如在开源库中还有可以对图片进行裁剪旋转的功能，但在使用时却会关闭应用，并且在日志中也没有显示报错信息，最后没有解决，于是只有放弃这个功能；在进行选择时无法显示文件的名字，图片可以直接看，但视频和音频则必须要打开播放才能确定文件名字。

