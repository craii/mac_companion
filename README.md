# mac_companion
copilot for mac, a pale imitation of windows copilot
<br>
 
# 简介
在学习pyqt的过程中，经常向gpt提问，提高学习进度。但复制-->打开浏览器-->切换标签-->填入输入框并提问的过程重复多次后，变成了恼人的操作。于是，就有了本项目。
<br>
mac_companion常驻 mac 顶部菜单栏。可以让我在绝大多数 app 中，可通过鼠标右键的服务菜单，快速将选中的文字作为 prompt 提交给 Chatglm 并得到答复，当然如果你不想使用chatglm也可以在修改少量代码的情况下，替换为其他支持 openai-like api的模型，或者直接改为调用openai的api。 
<br>
**本项目有两个版本**：<br>
- **mac_companion**: 本仓库，你可以在参照下述安装说明完成 Setup 即可使用；<br>
- **mac_companion【直接运行版】**：如果你的 ```mac 使用的是M系列芯片``` ，可转至[此仓库](https://github.com/craii/mac_companion_for_M_Chip_mac) ，参照对应文档下载安装即可。也可以直接下载整合包：
> [整合包](https://pan.quark.cn/s/1e23a679b846) ， 提取码：dTK1
<br>
整合包已经集成了本项目的虚拟环境、chatglm 所需的虚拟环境 以及 chatglm 模型。下载完成后只需要切换到解压目录下，运行 ```python run.py``` 即可运行（我已在两台m-chip的mac上测试可行）。 ```INTEL芯片``` 的mac未经测试，但应该是不能运行的，因为本项目使用的 chatglm 在进行cpp编译时采用的参数中指定了arm平台。
<br>

# Setup
## **所需Python版本：**
- **mac_companion**: 3.11.5;
- **chatglm-6b**: 3.8.18;
<br>

## Step 1<br>
**下载本仓库**<br>

```git clone https://github.com/craii/mac_companion.git && cd mac_companion```

## Step 2<br>
**创建虚拟环境**  <br>
```python -m venv venv``` <br>
```source ./venv/bin/activate``` <br>
```pip install -r requirements.txt``` <br>
>注意此时创建了虚拟环境 ```venv```之后，需要记录 ```venv``` 中的 ```python_executable``` 路径， 假设你运行 ```Step 1```的命令时，是将 ```documents``` 路径下， 则 ```python_executable``` 路径为：```/documents/mac_companion/venv/bin/python```

## Step 3 <br>
**安装 chatglm**: 
   - 如果你倾向于使用完全版的 chatglm：请参照 [https://github.com/THUDM/ChatGLM3](https://github.com/THUDM/ChatGLM3) ；
   - 如果你倾向于使用量化加速后的 chatglm：请参照 [https://github.com/li-plus/chatglm.cpp?tab=readme-ov-file](https://github.com/li-plus/chatglm.cpp?tab=readme-ov-file)
   - 
<br>

安装完成后请务必先验证其是否被正确安装，并且能够启动 ```OpenAI_API``` ，如果正常启动，那么你应该能够在终端看到类似下图的文字：<br>
<img width="584" alt="image" src="https://github.com/craii/mac_companion/assets/10702100/6411921c-1925-438a-806a-562d2606318b">
<br>
注意：<br>

 - 记录上图中地址 ```127.0.0.1:8001``` 中的端口号：```8001``` ； <br>
 - 记录启动 ```OpenAI_API``` 服务时使输入的命令：本项目使用的是量化加速后的 chatglm， 启动命令为： <br>
```cd /Users/YOURNAME/Documents/chatglm.cpp-chatglm3/chatglm_cpp && MODEL=../chatglm3-ggml.bin /Users/YOURNAME/anaconda3/envs/chatglmcpp/bin/uvicorn chatglm_cpp.openai_api:app --host 127.0.0.1 --port 8001```

<br>

## Step 4 <br>
修改本项目中的 ```config.py``` 文件: <br>
 - 修改 ```port``` 的值为：你看到的端口号 (如以上图为例，则将其修改为8001)；<br>
 - 修改 ```aiserver_command``` ： ```cd /Users/YOURNAME/Documents/chatglm.cpp-chatglm3/chatglm_cpp && MODEL=../chatglm3-ggml.bin /Users/YOURNAME/anaconda3/envs/chatglmcpp/bin/uvicorn chatglm_cpp.openai_api:app --host 127.0.0.1 --port 8001```（根据你的实际情况修改）<br>
 - 修改 ```python_executable``` 的值为：```/documents/mac_companion/venv/bin/python```(参考Step 2)
<br>

修改后的 ```config.py``` 可能如下：<br>

![image](https://github.com/craii/mac_companion/assets/10702100/cf995a72-3b76-4256-b58a-19b08b5d9e7e)

## Step 5 <br>
1. 双击 ```copilot.workflow``` ，会自动安装 ```copilot.workflow```，然后在打开的页面里，将下图中 ```红框``` 和 ```篮框```部分为 ```mac_companion``` 的项目路径；<br>
<img width="1512" alt="image" src="https://github.com/craii/mac_companion/assets/10702100/41a6a1ad-6980-49e1-a960-536ed4f2ad50">

<br>

> 双击后， ```copilot.workflow``` 如果没有自动打开，则在 **启动台** 中找到 **自动操作** 并用其打开copilot.workflow， 按照要求修改
<img width="181" alt="image" src="https://github.com/craii/mac_companion/assets/10702100/ca20d237-04a1-4209-807e-02f6d6735d22">



## Step 6 <br>
回到 ```mac_companion``` 文件夹， 运行 ```python App.py```


