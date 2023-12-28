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

### 安装PyTorch
1. 查看CUDA版本
   - 按下windows键盘，敲入cmd进入命令提示符窗口
     ![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/a49bf82f-173d-4398-bd9b-a0bf424210b6)
   - 敲入nvidia-smi命令，查看CUDA版本（我的是CUDA 12.3）
     ![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/039c6c84-572b-4015-bad5-93df980c3d94)
2. 查找Pytorch安装命令
   - 参考[pytorch.org](https://pytorch.org)安装配套的PyTorch+torchvision+cuda
   - 我的CUDA是12.3,而pytorch官网最高的是CUDA=12.1，所以只能安装最高版本的CUDA 12.1对应的Pytorch，用pip安装
     ![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/85eb2d46-e0ff-4bed-bf54-11786bd82311)
   - 如果想查看更多版本的Pytorch，可以点击“previous versions of PyTorch”
     ![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/38d0bf52-dc90-420d-9f70-aad446c11e76)
   - 找到对应的CUDA版本和对应的系统，获取相应的安装命令，建议使用pip安装。注意不能安装CPU版本，必须是CUDA版本，并且Pytorch≥1.8
     ![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/992c8a13-4c24-40c5-90a9-bf0863865b05)
3. 安装Pytorch
   - 回到提示符窗口，键入上一步获取的安装命令，比如我的是：
   ```
   pip install torch==2.1.1 torchvision==0.16.1 torchaudio==2.1.1 --index-url https://download.pytorch.org/whl/cu121
   ```

### 安装gcc和g++
1. 获取MinGW的安装工具，下载的压缩包放在：[mingw-w64-install.zip](https://github.com/PandaTofu/Install-YOLOT/blob/main/tools/mingw-w64-install.zip)
2. 解压并双击exe的安装工具，按照提示逐步安装
   - 注意安装的时候截图中的两项要根据系统调整：
   - ![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/17a69015-f368-4790-9613-0bef60f8969b)
     - Architecture：32位选i686/64位选x86_64
     - Threads：windows选择win32
3. 安装时请记下安装路径，后续设置环境变量需要
4. 启动MinGW Installation Manager
5. 左边选择All Packages->MinGW->MinGW Base System
   ![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/13a01fb9-8c30-4af7-ba52-9fae997202ed)
6. 右边勾选mingw32-gcc-bin/dev/lib + mingw32-gcc-g++-bin/dev，勾选时候点击“Mark for installation”，依赖包会自动勾选
   ![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/d219cfa2-964a-4f8e-94a6-c390e9824983)
7. 上方工具栏选择Intallation->Apply Changes，过程比较漫长，如果有安装失败的包，等完成之后继续“Apply Changes”直到所有包安装完成
   ![image](https://github.com/PandaTofu/Install-YOLOT/assets/22908364/cfbd4be0-7b25-44db-8118-412bbfeece55)


