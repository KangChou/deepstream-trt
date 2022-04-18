# deepstream-trt
模型设计与量化分析

DeepStream应用程序将深度神经网络和其他复杂的处理任务引入到流处理管道中，以实现对视频和其他传感器数据的近实时分析。从这些传感器中提取有意义的见解为提高运营效率和安全性创造了机会。例如，摄像头是当前使用最多的物联网传感器。在我们的家中，街道上，停车场，大型购物中心，仓库，工厂中都可以找到相机–无处不在。视频分析的潜在用途是巨大的：访问控制，防止丢失，自动结帐，监视，安全，自动检查（QA），包裹分类（智能物流），交通控制/工程，工业自动化等。

![image](https://user-images.githubusercontent.com/36963108/163709028-64901c72-aa40-4286-bd03-99b7a975af29.png)



NVIDIA DeepStream SDK 开发人员指南教程学习文档:https://docs.nvidia.com/metropolis/deepstream/dev-guide/index.html
```
docker pull nvcr.io/nvidia/deepstream:5.1-21.02-devel
```
NVIDIA Jetson Xavier NX-deepstream-Test编译测试 \
https://isning.top/index.php/2021/02/02/nvidia-jetson-xavier-nx-deepstream-test%e7%bc%96%e8%af%91%e6%b5%8b%e8%af%95/

安装cuda 11.3和TensorRT 8:http://zhangshiyu.com/post/30015.html

Deepstream5.1运行环境搭建并成功运行demo:https://blog.csdn.net/weixin_47250364/article/details/121031634?spm=1001.2014.3001.5506

DeepStream5.0系列之环境安装：https://blog.csdn.net/zong596568821xp/article/details/105966383


# 常见问题
```
fatal error: cuda_runtime.h: No such file or directory
```

解决方法：

```
步骤1：
export CUDA_HOME=/usr/local/cuda-11.1
export LD_LIBRARY_PATH=/usr/local/cuda-11.1/lib64:$LD_LIBRARY_PATH
export PATH=/usr/local/cuda-11.1/bin:${PATH}

步骤2：
ln -s /usr/local/cuda-11.1 /usr/local/cuda

步骤3：
添加makefile文件的cuda版本参数：CUDA_VER?=11.1
CUDA_VER?=11.1
ifeq ($(CUDA_VER),)
  $(error "CUDA_VER is not set")
endif

```
DeepStream SDK Python 绑定和示例应用程序:https://github.com/NVIDIA-AI-IOT/deepstream_python_apps

使用 Deepstream SDK 和迁移学习工具包的人数统计应用程序:https://github.com/NVIDIA-AI-IOT/deepstream-occupancy-analytics

NVIDIA Jetson Xavier NX-deepstream-Test编译测试: https://isning.top/index.php/2021/02/02/nvidia-jetson-xavier-nx-deepstream-test%e7%bc%96%e8%af%91%e6%b5%8b%e8%af%95/

deepstream5.0 pdf:https://cdn-prod.scdn6.secure.raxcdn.com/static/media/DAM_496c8e1e-c1ac-431f-914c-75dc29ad3168.pdf


How to run the sample:
Start the docker container image
```bash
$ sudo docker run --gpus all --rm -it --shm-size=1g --ulimit memlock=-1 --ulimit stack=67108864
-v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=$DISPLAY -w /root nvcr.io/nvidia/deepstream:5.0-
dp-20.04-samples
$ cd /opt/nvidia/deepstream/deepstream-5.0/sources/apps/sample_apps/deepstream-app
Edit the configuration file and enable sink1 type 3=File
$ vim /opt/nvidia/deepstream/deepstream-5.0/samples/configs/deepstreamapp/source30_1080p_dec_infer-resnet_tiled_display_int8.txt
$ make
$ deepstream-app -c /opt/nvidia/deepstream/deepstream-5.0/samples/configs/deepstreamapp/source30_1080p_dec_infer-resnet_tiled_display_int8.txt

```

TX2 /Xavier /deepstream:https://blog.csdn.net/mao_hui_fei/category_10877877.html

DeepStream初步学习：https://blog.csdn.net/Tosonw/article/details/104154090

DeepStream 场景应用：https://www.forecr.io/blogs/ai-algorithms/preparing-a-deepstream-application-on-dsbox-nx

人工智能算法应用场景技术博客教程：https://www.forecr.io/blogs/ai-algorithms


