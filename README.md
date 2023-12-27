# Install-YOLOT
安装的是基于Detectron2版本的YOLOT，代码仓库：[`YOLOT-detectorn2`](https://github.com/chensnathan/YOLOF/)
## 安装Detectorn2
安装步骤可以参考：[detectorn2安装指南](https://github.com/facebookresearch/detectron2/blob/master/INSTALL.md).
### 需求
- 系统：Windows 10或以上
- Python ≥ 3.7 （我用的是Python 3.9.7）
- PyTorch ≥ 1.8 和相应版本的torchvision+cuda，
- gcc & g++ ≥ 5.4

### 安装PyTorch
1. 查看CUDA版本
   按下windows键盘，敲入cmd进入命令提示符窗口
   ![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/a49bf82f-173d-4398-bd9b-a0bf424210b6)
   敲入nvidia-smi命令，查看CUDA版本（我的是CUDA 12.3）
   ![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/039c6c84-572b-4015-bad5-93df980c3d94)
2. 查找Pytorch安装命令
   参考[pytorch.org](https://pytorch.org)安装配套的PyTorch+torchvision+cuda
   我的CUDA是12.3,而pytorch官网最高的是CUDA=12.1，所以只能安装最高版本的CUDA 12.1对应的Pytorch，用pip安装
    ![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/85eb2d46-e0ff-4bed-bf54-11786bd82311)
   如果想查看更多版本的Pytorch，可以点击“previous versions of PyTorch”
   ![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/38d0bf52-dc90-420d-9f70-aad446c11e76)
   找到对应的CUDA版本和对应的系统，获取相应的安装命令，建议使用pip安装。注意不能安装CPU版本，必须是CUDA版本，并且Pytorch≥1.8
    ![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/992c8a13-4c24-40c5-90a9-bf0863865b05)
3. 安装Pytorch
   回到提示符窗口，键入上一步获取的安装命令，比如我的是：
   ```
   pip install torch==2.1.1 torchvision==0.16.1 torchaudio==2.1.1 --index-url https://download.pytorch.org/whl/cu121
   ```

### 安装gcc和g++
1. 获取MinGW的安装工具，我将我下载的压缩包放在：
2. 
