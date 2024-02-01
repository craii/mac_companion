# mac_companion
copilot for mac, a pale imitation of windows copilot
<br>
 
# 简介
在学习pyqt的过程中，经常向gpt提问，提高学习进度。但复制-->打开浏览器-->切换标签-->填入输入框并提问的过程重复多次后，变成了恼人的操作。于是，就有了本项目。
<br>
mac_companion常驻 mac 顶部菜单栏。可以让我在绝大多数 app 中，可通过鼠标右键的服务菜单，快速将选中的文字作为 prompt 提交给 Chatglm 并得到答复，当然如果你不想使用chatglm也可以在修改少量代码的情况下，替换为其他支持 openai-like api的模型，或者直接改为调用openai的api。 
<br>
**本项目有两个版本**：<br>
<br>
- **mac_companion**: 本仓库，你可以在参照下述安装说明完成 Setup 即可使用；<br>
- **mac_companion【直接运行版】**：如果的 ```mac 使用的是M系列芯片``` ，可转至[此仓库](https://github.com/craii/mac_companion_for_M_Chip_mac) ，参照对应文档下载安装即可。也可以直接下载整合包：
> [整合包](https://pan.quark.cn/s/1e23a679b846) ， 提取码：dTK1
<br>
整合包已经集成了本项目的虚拟环境、chatglm 所需的虚拟环境 以及 chatglm 模型。下载完成后只需要切换到解压目录下，运行 ```python run.py```即可运行（我已在两台m-chip的mac上测试可行）。```INTEL芯片```的mac未经测试，但应该是不能运行的，因为本项目使用的 chatglm 在进行cpp编译时采用的参数中指定了arm平台。
<br>
# Setup
## **所需Python版本：**
- **mac_companion**: 3.11.5;
- **chatglm-6b**: 3.8.18;
<br>
## step 1
1. **安装 chatglm**:
   - 如果你倾向于使用完全版的 chatglm：请参照 [https://github.com/THUDM/ChatGLM3](https://github.com/THUDM/ChatGLM3) ；
   - 如果你倾向于使用量化加速后的 chatglm：请参照 [https://github.com/li-plus/chatglm.cpp?tab=readme-ov-file](https://github.com/li-plus/chatglm.cpp?tab=readme-ov-file)
<br>
安装完成后请务必先验证其是否被正确安装，并且能够启动 ```OpenAI API``` ，如果正常启动，那么你应该能够在终端看到类似下图的文字：<br>
<img width="584" alt="image" src="https://github.com/craii/mac_companion/assets/10702100/6411921c-1925-438a-806a-562d2606318b">
<br>
注意：
 - 记录上图中地址```http://127.0.0.1:8001```中的端口号：```8001```；
 - 记录启动```OpenAI API```服务时使输入的命令：本项目使用的是量化加速后的 chatglm， 启动命令为：<br>```"cd /Users/YOURNAME/Documents/chatglm.cpp-chatglm3/chatglm_cpp && MODEL=../chatglm3-ggml.bin /Users/YOURNAME/anaconda3/envs/chatglmcpp/bin/uvicorn chatglm_cpp.openai_api:app --host 127.0.0.1 --port 8001" ```；

<br>
2. 修改本项目中的```config.py```文件:
 - 修改```port```的值为：你看到的端口号 (如以上图为例，则将其修改为8001)；
 - 修改```aiserver_command```：```"cd /Users/YOURNAME/Documents/chatglm.cpp-chatglm3/chatglm_cpp && MODEL=../chatglm3-ggml.bin /Users/YOURNAME/anaconda3/envs/chatglmcpp/bin/uvicorn chatglm_cpp.openai_api:app --host 127.0.0.1 --port 8001" ```（根据你的实际情况修改）
<br>
修改后的```config.py```可能如下：
![image](https://github.com/craii/mac_companion/assets/10702100/cf995a72-3b76-4256-b58a-19b08b5d9e7e)


