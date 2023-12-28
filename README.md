# Install-YOLOT
安装的是基于Detectron2版本的YOLOT，代码仓库：[`YOLOT-detectorn2`](https://github.com/chensnathan/YOLOF/)
## 安装Detectorn2
安装步骤可以参考：[detectorn2安装指南](https://github.com/facebookresearch/detectron2/blob/master/INSTALL.md).
### 需求
- 系统：Windows 10或以上
- Python ≥ 3.7 （我用的是Python 3.9.7）
- PyTorch ≥ 1.8 和相应版本的torchvision+cuda，
- gcc & g++ ≥ 5.4
- Microsoft C++ ≥ 14.0
- OpenVC和ninjia是可选（我没有安装）

### 安装PyTorch
1. 查看CUDA版本
<br/>按下windows键盘，敲入cmd进入命令提示符窗口
<br/>![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/a49bf82f-173d-4398-bd9b-a0bf424210b6)
<br/>敲入nvidia-smi命令，查看CUDA版本（我的是CUDA 12.3）
<br/>![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/039c6c84-572b-4015-bad5-93df980c3d94)
2. 查找Pytorch安装命令
<br/>参考[pytorch.org](https://pytorch.org)安装配套的PyTorch+torchvision+cuda
<br/>我的CUDA是12.3,而pytorch官网最高的是CUDA=12.1，所以只能安装最高版本的CUDA 12.1对应的Pytorch，用pip安装
<br/>![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/85eb2d46-e0ff-4bed-bf54-11786bd82311)
<br/>如果想查看更多版本的Pytorch，可以点击“previous versions of PyTorch”
<br/>![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/38d0bf52-dc90-420d-9f70-aad446c11e76)
<br/>找到对应的CUDA版本和对应的系统，获取相应的安装命令，建议使用pip安装。注意不能安装CPU版本，必须是CUDA版本，并且Pytorch≥1.8
<br/>![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/992c8a13-4c24-40c5-90a9-bf0863865b05)
4. 安装Pytorch
<br/>回到提示符窗口，键入上一步获取的安装命令，比如我的是：
   ```
   pip install torch==2.1.1 torchvision==0.16.1 torchaudio==2.1.1 --index-url https://download.pytorch.org/whl/cu121
   ```

### 安装gcc和g++
1. 获取MinGW的安装工具，下载的压缩包放在：[mingw-w64-install.zip](https://github.com/PandaTofu/Install-YOLOT/blob/main/tools/mingw-w64-install.zip)
2. 解压并双击exe的安装工具，按照提示逐步安装
<br/>注意安装的时候截图中的两项要根据系统调整：
   - Architecture：32位选i686；64位选x86_64
   - Threads：windows选择win32
<br/>![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/17a69015-f368-4790-9613-0bef60f8969b)
3. 安装时请记下安装路径，后续设置环境变量的时候需要用到
4. 启动MinGW Installation Manager
5. 左边选择All Packages->MinGW->MinGW Base System
<br/>![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/13a01fb9-8c30-4af7-ba52-9fae997202ed)
6. 右边勾选mingw32-gcc-bin/dev/lib + mingw32-gcc-g++-bin/dev，勾选时候点击“Mark for installation”，依赖包会自动勾选
<br/>![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/d219cfa2-964a-4f8e-94a6-c390e9824983)
7. 上方工具栏选择Intallation->Apply Changes，过程比较漫长，如果有安装失败的包，等完成之后继续“Apply Changes”直到所有包安装完成
<br/>![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/cfbd4be0-7b25-44db-8118-412bbfeece55)
8. 启动命令提示符窗口，敲入下面的命令确认安装是否成功，并查看gcc和g++版本
<br/>`gcc -v`
<br/>![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/9214a077-b6a0-4762-a5f1-62f13cb1d11b)
<br/>`g++ -v`
<br/>![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/665e512e-3ae0-4e7e-8440-1797ceea4afc)

### 安装Microsoft C++
1. 先安装Microsoft C++ build tools，下载地址：[Build Tools](https://visualstudio.microsoft.com/zh-hant/visual-cpp-build-tools/?wd&eqid=ab927a7c0000230c00000004654439dc)
2. 双击vs_BuildTools.exe安装包进行安装
3. 安装完成后，启动VS Installer
4. 点击“可用”，建议选择“VS Community”，并点击“安装”
<br/>![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/53a25477-3c7e-456f-b7ee-00b91333f50c)
5. 在弹出的窗口里选择“通用Windows平台开发”，右侧追加选择“C++”和“Wind10/11 SDK”
<br/>![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/a90d37d6-d420-4d17-8cc5-3e5033363e3b)
6. 右下角点击“安装”，如需安装前可以更改安装路径

### 安装Detetron2
可以远程安装，也可以下载源码到本地进行安装，安装命令如下：
```
# 远程安装：
python -m pip install 'git+https://github.com/facebookresearch/detectron2.git'
# （如果没有权限，请添加--user参数）

# 或者下载源码到本地进行安装
git clone https://github.com/facebookresearch/detectron2.git
python -m pip install -e detectron2
```

### 安装mish-cuda和YOLOT
1. 下载YOLOT源码
   ```
   git clone https://github.com/chensnathan/YOLOF
   ```
2. 进入YOLOT目录，下载mish-cuda源码并安装
   ```
   git clone https://github.com/thomasbrandon/mish-cuda
   cd mish-cuda
   python setup.py build install
   cd ..
   ```
   注意：如果安装过程出现mish.h的语法错误（如void前面应有;），可以尝试将mish-cuda/csrc目录的mish.h文件替换
   替换文件在：[mish.h](https://github.com/PandaTofu/Install-YOLOT/blob/main/tools/mish.h)
3. 执行如下命令，安装YOLOT
   ```
   python setup.py develop
   ```

### 准备预训练模型
1. 在YOLOT目录下，创建`pretrained_models`文件夹
2. 下载预训练模型，下载地址：[OneDrive](https://1drv.ms/u/s!AgM0VtBH3kV9imGxZX3n_TMQGtbP?e=YMgpGJ) 或者 [Baidu Cloud](https://pan.baidu.com/s/1BSOncRYq6HeCQ8q2hrWowA) （提取码是`qr6o`）
3. 将下载的预训练模型文件拷贝到`pretrained_models`文件夹

### 准备COCO数据集
1. 在YOLOT目录下，创建`datasets`文件夹
2. 进入`datasets`文件夹，创建`coco`文件夹
3. 下载COCO数据集，下载地址可在[各类图像数据下载地址](https://bendfunction.gitbook.io/dataset-download/)找到，我用的是2017的COCO数据，
   - 图片数据（Image）：下载2017 Train/Val/Test图片数据
     ```
     # 2017 Train images [118K/18GB]:
     http://images.cocodataset.org/zips/train2017.zip

     # 2017 Val images [5K/1GB]:
     http://images.cocodataset.org/zips/val2017.zip

     # 2017 Test images [41K/6GB]:
     http://images.cocodataset.org/zips/test2017.zip
     ```
   - 注解文件（Annotations）：下载Train/Val数据集的注解文件：
     ```
     # 2017 Train/Val annotations [241MB]:
     http://images.cocodataset.org/annotations/annotations_trainval2017.zip
     ```
4. 解压数据集并分别拷贝`train2017`，`val2017`和`annotations`目录到`coco`文件夹里，目录结构如下：
   ![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/4015447b-dcf5-46e2-bad4-cf68f99af605)

### 基于YOLOT进行训练或测试
回到YOLOT目录，执行以下命令进行训练和测试
- 训练
  ```
  python ./tools/train_net.py --num-gpus 8 --config-file ./configs/yolof_R_50_C5_1x.yaml
  ```
  注意：参数`--num-gpus`指定所用GPU数量，不能比运行环境的GPU数量多，所以执行前建议使用Python的torch库查看电脑的GPU数量：
  ```
  import torch
  torch.cuda.device_count()
  ```
  ![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/4d4b5812-c094-4d7d-8a42-b78c6d23d04b)
  例如，我的环境上只有1个GPU，运行命令时要指定GPU数量为1
  ```
  python ./tools/train_net.py --num-gpus 1 --config-file ./configs/yolof_R_50_C5_1x.yaml
  ```
- 测试
  ```
  python ./tools/train_net.py --num-gpus 8 --config-file ./configs/yolof_R_50_C5_1x.yaml --eval-only MODEL.WEIGHTS /path/to/checkpoint_file
  ```
  同理，`--num-gpus`参数根据实际情况设置
