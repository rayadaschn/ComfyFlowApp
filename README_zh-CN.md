# ComfyFlowApp
快速将你的ComfyUI工作流开发成一个Web应用，并分享给其他用户使用。

## ComfyFlowApp 是什么？
ComfyFlowApp 是一个ComfyUI的扩展工具， 可以轻松从ComfyUI的工作流开发出一个简单易用的应用，降低ComfyUI的使用门槛。
如下图所示，将一个人像修复的工作流开发成一个ComfyFlowApp应用。
![图1](docs/images/demo-workflow.png)
![图2](docs/images/demo-webapp.png)

### ComfyFlowApp 有什么用？
如果你想通过AI工具来生成一张图片，可以选择的MidJourney、DALL-E3、Fairfly（Adobe），使用这些工具任何人都可以通过提示词来生成一幅精美的图片，如果你想进一步控制生成的结果，如让模特穿上指定的衣服，这些工具可能都无法实现，或者你所在的场景对图片版权有特殊的要求，你可以使用开源的Stable Diffusion来构建AI图片处理应用，可以选择Stable-Diffusion-WebUI或者ComfyUI，其中WebUI简单易用，插件生态丰富，可以满足很多场景的处理需求，而ComfyUI使用门槛较高，但支持更灵活的工作流定制，开发出满足各种场景需求的工作流。

如果你需要将ComfyUI中开发的工作流分享给其他用户使用，ComfyFlowApp可以显著降低其他用户使用你的工作流的门槛。
- 用户不需要懂AI生成模型的原理；
- 用户不需要懂各种AI模型的调优参数；
- 用户不需要懂模型从哪里下载；
- 用户不需要懂如何搭建ComfyUI工作流；
- 用户不需要懂Python安装环境；

ComfyFlowApp 帮助应用开发者将这些复杂度对用户透明，用户只需要像普通应用一样使用即可。

**总结，如果你需要将ComfyUI开发的工作流分享给其他用户使用，选择ComfyFlowApp就对了。**

### ComfyFlowApp 如何工作？
ComfyFlowApp 支持两种模式Creator 和 Studio，用户可以灵活切换使用模式。
Creator模式，用户将ComfyUI工作流转换为一个Web应用，本地运行应用，或者发布到comfyflow.app，分享给其他用户使用。
Studio模式，用户在本地运行ComfyFlowApp，从comfyflow.app安装应用并在本地运行。
如下图所示：
![How-it-works](./docs/images/how-it-works.png)

### 典型使用场景

**1）工作室或企业内部的分工协作**

工作室或企业内部处于分工协作的需求，并不要求每个人都懂AI，懂各种模型，懂工作流搭建，典型的协作场景：一个人或几个人来构建AI应用，其他用户直接使用。
1. 开发者在ComfyUI中开发工作流，测试出满意的效果，保存工作流；
2. 开发者使用ComfyFlowApp工具Creator，从工作流转换为一个Web应用，隐藏无关的细节参数，让应用简单易用；
3. 开发者启动应用，并将地址分享给工作室或企业内部的用户使用；
4. 其他用户通过分享的应用地址访问开发者部署的应用；

**2）专业创造者或团队，开发并将应用分享给更多人使用**

通过ComfyUI工具，专业的创作者或团队可以开发出很有价值的应用，但ComfyUI对普通来说使用门槛太高；使用ComfyFlowApp将工作流开发成一个面向更大众用户的应用，可以创造更大的价值。
1. 开发者在ComfyUI中开发工作流，测试出满意的效果，保存工作流；
2. 开发者使用ComfyFlowApp工具Creator，从工作流转换为一个Web应用，隐藏无关的细节参数，让应用简单易用；
3. 开发者将应用发布的应用市场；
4. 其他用户从应用市场发现并下载应用，本地运行应用；

关注本项目，获取最新动态。

[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/comfyflow)

### 快速开始
```bash
# 下载项目
git clone https://github.com/xingren23/ComfyFlowApp

# 更新comfyui依赖
cd ComfyFlowApp
git submodule update --init --recursive

# 使用Conda创建并管理python环境
# Note: pytorch does not support python 3.12 yet so make sure your python version is 3.11 or earlier.
conda create -n comfyflowapp python=3.11
conda activate comfyflowapp

# 安装comfyui依赖, Nvidia users should install pytorch using this command:
pip install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu121
pip install -r .\repositories\ComfyUI\requirements.txt

# 安装ComfyFlowApp依赖
pip install -r requirements.txt

# 启动
# linux 
sh bin/creator_run.sh 
sh bin/studio_run.sh
sh bin/explore_run.sh
# windows
.\bin\creator_run.bat
.\bin\studio_run.bat
.\bin\explore_run.bat
```

环境变量, 在启动脚本中可以修改相关变量
```
:: ComfyflowApp 地址，默认：https://api.comfyflow.app
set COMFYFLOW_API_URL=https://api.comfyflow.app

:: 开发联调外部ComfyUI地址，可以连接局域网内其他服务器地址，默认：http://localhost:8188
set COMFYUI_SERVER_ADDR=http://localhost:8188

:: ComfyFlowApp内置ComfyUI地址，只能使用本机地址，默认：http://localhost:9188
set INNER_COMFYUI_SERVER_ADDR=http://localhost:9188

:: 设置web应用启动地址，让局域网内其他用户可以访问你的应用，默认：localhost
set STREAMLIT_SERVER_ADDRESS=192.168.1.100
```

### 相关视频
- [ComfyFlowApp 入门: 安装并开发第一个应用](https://www.youtube.com/watch?v=glRO1q4IAI0&t=6s&ab_channel=ZhiguoWang)

## 相关项目
- [ComfyUI](https://github.com/comfyanonymous/ComfyUI)

## 联系我们
ComfyWorkflowApp 项目还处于早期阶段，如果您有任何问题或建议，欢迎通过以下方式联系我们：

- [GitHub Issues](https://github.com/xingren23/ComfyWorkflowApp/issues)

- WeChat: 如果微信群二维码过期，请添加我的微信号：xingren23，备注“ComfyFlowApp”，我拉你进群。

![alt-text-1](docs/images/WechatGroup.jpg "title-1") ![alt-text-2](docs/images/wechat-xingren23.jpg "title-2")