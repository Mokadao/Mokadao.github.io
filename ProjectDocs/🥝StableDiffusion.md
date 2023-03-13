## 关于
Stable Diffusion是一款功能异常强大的AI图片生成器。它不仅支持生成图片，使用各种各样的模型来达到你想要的效果，还能训练你自己的专属模型。


## table Diffusion WebUI
### 安装

WebUI使得Stable Diffusion有了一个更直观的用户界面，更适合新手用户。

以下内容只涉及Win环境下的安装。



#### 安装Git

安装GIt的目的：需要通过Git，克隆相关的程序库。

在https://registry.npmmirror.com/-/binary/git-for-windows/v2.38.1.windows.1/Git-2.38.1-64-bit.exe下载（实际Git版本并不影响使用，这里使用的是Git 2.38）下载之后安装。

#### 安装Python

安装Python的目的：运行的语言环境。

需要安装Python 3.10。这是官方文档上指定的版本，Windows的安装程序在https://mirrors.huaweicloud.com/python/3.10.9/python-3.10.9-amd64.exe下载（Python 3.10.9）。

PS：
- - **Windows下安装Python时，请务必勾选“Add Python to PATH”，以后我们调度Python时会方便很多。**
- 如果你选择的是自定义安装，**请务必在安装组件选择中勾选PIP**（Python的包管理工具，无论是在接下来的安装中还是后续的使用中，我们都需要用到它）。

**安装Nvidia CUDA（N卡）**

Nvidia CUDA是什么：几乎所有的AI在Nvidia显卡上都需要的东西。

如果使用的是A卡，则需要使用Ort。

在安装CUDA之前，请确保你已安装Nvidia显卡驱动。不同的驱动版本固定搭配不同的CUDA版本。（下面的步骤我使用的是Nvidia Driver 516.94+CUDA 11.7.1）。当然，如果你想使用更新的驱动，你也可以自行搜索其搭配的CUDA版本。

Windows下，在这里下载安装：https://developer.download.nvidia.cn/compute/cuda/11.7.1/local_installers/cuda_11.7.1_516.94_windows.exe（版本11.7.1，搭配Nvidia驱动516.94）进行下载安装。

PS：
- 在Windows下，安装CUDA一般只用根据安装程序的提示就可以安装了。如果你不想安装太多冗余的东西，则可以只在安装选项中勾选Runtime和Development

**PyTorch**

PyTorch也是Stable Diffusion不可缺少的依赖包，它主要用于拓展CUDA的功能。

就像不同的Nvidia驱动版本固定搭配不同的CUDA版本一样，不同的Torch版本也固定搭配不同的CUDA版本使用（下面的步骤中我使用PyTorch-1.13.1+CUDA11.7）。

在Python窗口中进行安装：

`pip install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu117`



