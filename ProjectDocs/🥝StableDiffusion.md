## 关于
Stable Diffusion是一款功能异常强大的AI图片生成器。它不仅支持生成图片，使用各种各样的模型来达到你想要的效果，还能训练你自己的专属模型。



## 插件

checkpoint merge：放在stable diffusion根目录\models\Stable-diffusion
Lora存放目录：stable diffusion根目录\models\Lora
### Lora
lora：放在stable diffusion根目录\models\Lora

### ControlNet
controlnet存放目录：stable diffusion根目录\extensions\sd-webui-controlnet\models
ControlNet是一种神经网络结构，通过添加额外的条件来控制扩散模型。它将神经网络块的权重复制到“锁定”副本和“可训练”副本中。可训练的副本学习您的条件。

**安装**
- 需要下载预训练基础模型
- 下载后放到webUI目录下的extensions\sd-webui-controlnet\mods下

基础功能


#### OpenPose编辑器

#### seg语义分割

### DreamBooth


## 脚本

### Face Editor
[ototadana/sd-face-editor: Face editor for Stable Diffusion (github.com)](https://github.com/ototadana/sd-face-editor#step-1)
Face Editor存放目录：stable diffusion根目录\scripts

## Stable Diffusion WebUI
### 安装

WebUI使得Stable Diffusion有了一个更直观的用户界面，更适合新手用户。

以下内容只涉及Win环境下的安装。

---

#### 安装Git

安装GIt的目的：需要通过Git，克隆相关的程序库。

在https://registry.npmmirror.com/-/binary/git-for-windows/v2.38.1.windows.1/Git-2.38.1-64-bit.exe下载（实际Git版本并不影响使用，这里使用的是Git 2.38）下载之后安装。

#### 安装Python  

安装Python的目的：运行的语言环境。

需要安装Python 3.10。这是官方文档上指定的版本，Windows的安装程序在https://mirrors.huaweicloud.com/python/3.10.9/python-3.10.9-amd64.exe下载（Python 3.10.9）。

PS：
- - **Windows下安装Python时，请务必勾选“Add Python to PATH”，以后我们调度Python时会方便很多。**
- 如果你选择的是自定义安装，**请务必在安装组件选择中勾选PIP**（Python的包管理工具，无论是在接下来的安装中还是后续的使用中，我们都需要用到它）。

#### 安装Nvidia CUDA（N卡）

Nvidia CUDA是什么：几乎所有的AI在Nvidia显卡上都需要的东西。

如果使用的是A卡，则需要使用Ort。

在安装CUDA之前，请确保你已安装Nvidia显卡驱动。不同的驱动版本固定搭配不同的CUDA版本。（下面的步骤我使用的是Nvidia Driver 516.94+CUDA 11.7.1）。当然，如果你想使用更新的驱动，你也可以自行搜索其搭配的CUDA版本。

Windows下，在这里下载安装：https://developer.download.nvidia.cn/compute/cuda/11.7.1/local_installers/cuda_11.7.1_516.94_windows.exe（版本11.7.1，搭配Nvidia驱动516.94）进行下载安装。

PS：
- 在Windows下，安装CUDA一般只用根据安装程序的提示就可以安装了。如果你不想安装太多冗余的东西，则可以只在安装选项中勾选Runtime和Development

#### PyTorch

PyTorch也是Stable Diffusion不可缺少的依赖包，它主要用于拓展CUDA的功能。

就像不同的Nvidia驱动版本固定搭配不同的CUDA版本一样，不同的Torch版本也固定搭配不同的CUDA版本使用（下面的步骤中我使用PyTorch-1.13.1+CUDA11.7）。

在Python窗口中进行安装：

`pip install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu117`

---

#### 克隆Stable Diffusion+WebUI

打开Windows终端（Powershell，不是CMD）。首先，检查磁盘的剩余空间（一个完整的Stable Diffusion大概需要占用30~40GB的剩余空间），然后进到你选好的磁盘或目录下

`git clone https://ghproxy.com/https://github.com/AUTOMATIC1111/stable-diffusion-webui.git`

等待完成克隆，进入文件夹

`cd .\stable-diffusion-webui`

---

#### 编辑launch.py

用编辑器打开launch.py，替换所有的`https://github.com`为`https://ghproxy.com/https://github.com` 。

在菜单中依次选择`编辑`->`替换`，在弹出的小窗里的”查找”框里填上`https://github.com`，“替换”框里填上`https://ghproxy.com/<https://github.com`>，再按10下回车键即可（

替换完成后注意保存。


#### 创建并配置Venv虚拟环境和安装PIP包

编辑完之后，我们需要进入Stable Diffusion自带的Venv虚拟Python环境以进行配置和安装依赖。由于刚克隆下来的Stabe Diffusion没有附带Venv，所以我们得先执行一遍如下命令，以创建一个Venv环境。

`python -m venv .\\venv`

创建完成以后，我们进入到venv目录中的Scripts文件夹（Linux下是venv目录中的bin目录）：

`cd .\\venv\\Scripts`

执行其中的“activate.bat”。

`.\\activate.bat`

如果你使用的是Linux，则需要执行这个命令。

`$ source activate`

执行完成后，Windows命令行会自动清屏（之前执行的所有命令及输出结果清空），Linux的句首会出现“(venv)”的字样。此时，我们就成功进入到Venv环境中了。

成功进入Venv

Venv可以视作一个简化版的“虚拟Python”。新生成的Venv相当于删去了预置PIP包的Python，基本原理和完整Python无二异。所以，进入Venv后我们第一步要做的就是更换PIP源，以方便之后的PIP包的安装。这里我选择的是阿里的PIP源，在全国范围内都较快。

`pip config set global.index-url <https://mirrors.aliyun.com/pypi/simple/> # 这里你也可以选择其它的PIP源进行更换`

接着，我们需要安装Stable Diffusion和WebUI所需的PIP包。执行下列命令后耐心等待安装完成。

`cd ../..`

`pip install -r requirements_versions.txt # 执行此条命令前，请检查你的剩余磁盘空间`

然后我们执行“webui-user.bat”（Linux下是webui.bat）。

`.\\webui-user.bat`


#### 根据配置优化Stable Diffusion

直至目前，Stable Diffusion的基本框架已经被我们安装好了。但是根据我们配置的不同，还需要做一些简单的设置。

在Windows下，打开webui-user.bat（[Linux下是webui.sh](http://xn--Linuxwebui-bj2pq13u.sh)）:

`cd .. code .\\webui-user.bat`

将全部内容替换为：

`@echo off`

`set PYTHON=C:\\python\\python.exe`

`set GIT=set VENV_DIR=venv`

`set COMMANDLINE_ARGS=--medvram --autolaunch --deepdanbooru --xformers`

`call webui.bat`

Linux下，找到`#export COMMANDLINE_ARGS=""`这一行，去掉行首的“#”，并在两个双引号之间添加`--medvram --autolaunch --xformers`。

注：此处的“--medvram”是针对6GB及以上显存的显卡优化的，根据显卡配置的不同，你还可以更改为“--lowvram”（4GB以上）、“--lowram”（16GB以上）或者删除此项（无优化）。此外，此处的“--xformers”选项可以**开启Xformers**。加上此选项后，显卡的VRAM占用率就会相较原来减少一半，能大幅提升图片生成效率。

其实，除了在此列出的选项外，还有很多其它的选项来实现其它的一些功能。如果你感兴趣，可以查看官方文档或者自行在网上搜索。

#### 配置Stable Diffusion WebUI

模型配置完成后，重新回到克隆目录中。

`cd D:\\stable-diffusion-webui`

运行webui-user.bat（[Linux下是webui-user.sh](http://xn--Linuxwebui-user-5j3xz511a.sh)）。

`.\\webui-user.bat`

如果你的终端显示的内容与下图相符，那么恭喜你，Stable Diffusion WebUI的基本框架安装成功了！

大功告成。

注：在此，虽然我们在前面已安装过Stable Diffusion以及WebUI所需的PIP包，但PIP可能还会安装一些其它需要用到的包，静等其安装完成即可。由于我们在之前的步骤中已经修改过launch.py中的下载源，下载应该不会很慢。

#### 中文补丁

接着，我们会发现WebUI显示的并不是中文。此时，我们需要将其调整为简体中文。这里，我用百度网盘分享了一些语言的补丁。

-   链接：[https://pan.baidu.com/s/1X7R4nQfAxHKdoXRWyknSxg](https://pan.baidu.com/s/1X7R4nQfAxHKdoXRWyknSxg)
-   提取码：annx

下载我分享的“localizations.zip”并解压到**克隆文件夹的“localizations”目录中**。之后在Settings -> User interface -> Localization (requires restart)设置语言（在下拉菜单中选择zh_CN）。然后重新启动WebUI之后，你就会发现语言变成了简体中文。

备注：目前的语言补丁还没有完全翻译。任然有些地方（特别是扩展）没有完全翻译。如果有新的语言补丁放出，我会尽快更新。

如果你愿意，还可以安装一些扩展来实现其它功能（如创建美术风格）。转到`Extensions`选项卡以安装扩展。

#### 可能出现的问题



### 插件使用

在extensions搜索安装



## DiffusionBee for MAC