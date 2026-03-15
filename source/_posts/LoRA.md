---
title: LoRA微调

date: 2026-03-12 23:50:00
cover: https://raw.githubusercontent.com/foreverxiaoyu/my_blog/blob/main/fig/LoRA/show.png
keywords: Stable Diffusion LoRA 
---
使用前提：
1.已安装LoRA_Easy_Training_Scripts,Stable_Diffusion_Webui
2.准备好数据集(我这里准备了6，70张图片)

### 图片预处理

#### 分割
利用SD中的Segment Anything插件，用于提取人物(前景)
Prompt:one girl with full body

![segement](https://raw.githubusercontent.com/foreverxiaoyu/my_blog/main/fig/LoRA/segement.png)

#### 裁剪
提取好人物(前景)后，将图片裁剪成512*512
利用SD自带的Extras->Batch from Directory
![crop](https://raw.githubusercontent.com/foreverxiaoyu/my_blog/main/fig/LoRA/crop.png)


### LoRA训练

### 测试效果

