# deepstream-trt
模型设计与量化分析

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
n -s /usr/local/cuda-11.1 /usr/local/cuda

步骤3：
添加makefile文件的cuda版本参数：CUDA_VER?=11.1
CUDA_VER?=11.1
ifeq ($(CUDA_VER),)
  $(error "CUDA_VER is not set")
endif

```


