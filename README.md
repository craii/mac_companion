# mac_companion
copilot for mac, a pale imitation of windows copilot

 
# 简介
在学习pyqt的过程中，经常向gpt提问，提高学习进度。但复制-->打开浏览器-->切换标签-->填入输入框并提问的过程重复多次后，变成了恼人的操作。于是，就有了本项目。

mac_companion常驻 mac 顶部菜单栏。可以让我在绝大多数 app 中，快速将选中的文字作为 prompt 提交给 Chatglm 并得到答复，当然如果你不想使用chatglm也可以在修改少量代码的情况下，替换为其他支持 openai-like api的模型，或者直接改为调用openai的api。 

本项目有两个版本：
**mac_companion**: 本仓库，你可以在参照下述安装说明完成 Setup 即可使用；
**mac_companion【直接运行版】**：如果的 ```mac 使用的是M系列芯片``` ，可转至[此仓库](https://github.com/craii/mac_companion_for_M_Chip_mac) ，参照对应文档下载安装即可。也可以直接下载整合包：
> [整合包](https://pan.quark.cn/s/1e23a679b846) ， 提取码：dTK1

整合包已经集成了本项目的虚拟环境、chatglm 所需的虚拟环境 以及 chatglm 模型。下载完成后只需要切换到解压目录下，运行 ```python run.py```即可运行（我已在两台m-chip的mac上测试可行）。

# Setup
## **Python版本：**
- **mac_companion**: 3.11.5;
- **chatglm-6b**: 3.8.18;
