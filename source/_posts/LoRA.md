---
title: LoRA微调

date: 2026-03-12 23:50:00
cover: https://raw.githubusercontent.com/foreverxiaoyu/my_blog/main/fig/LoRA/fenmian.png
keywords: Stable Diffusion LoRA 
---
使用前提：
1.已安装LoRA_Easy_Training_Scripts,Stable_Diffusion_Webui
2.准备好数据集(我这里准备了6，70张图片)

### 图片预处理

#### 分割
利用SD中的Segment Anything插件，用于提取人物(前景)
SAM model download link(2.56GB sam_vit_h,2.56GB):
https://dl.fbaipublicfiles.com/segment_anything/sam_vit_h_4b8939.pth
GroundingDINO Detection Prompt:
``` bash
$ one girl with full body
```
![segement](https://raw.githubusercontent.com/foreverxiaoyu/my_blog/main/fig/LoRA/segement.png)

#### 裁剪
提取好人物(前景)后，将图片裁剪成512*512
利用SD自带的Extras->Batch from Directory
按下图配置好后再点击右上角的Generate
![crop](https://raw.githubusercontent.com/foreverxiaoyu/my_blog/main/fig/LoRA/crop.png)


### LoRA训练
Base Model 为基座模型,配置好数据路径以及输入尺寸512*512、SDXL Based后，点击右下角START TRAINING
不知道为什么不选SDXL，以及选择SD2.X会报错，之后研究下区别
![LoRA_gui](https://raw.githubusercontent.com/foreverxiaoyu/my_blog/main/fig/LoRA/LoRA_gui.png)

### 测试效果
以下分别为相同种子不用LoRA，利用LoRA微调后的结果
<table>
  <thead>
    <tr>
      <th style="width: 30px;">对比</th>
      <th>Seed 1648956789</th>
      <th>Seed 2465806440</th>
      <th>Seed 1296960879</th>
      <th>Seed 3824867931</th>
      <th>Seed 1196201394</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="width: 70px; white-space: nowrap;"><strong>无 LoRA</strong></td>
      <td><img src="https://raw.githubusercontent.com/foreverxiaoyu/my_blog/main/fig/LoRA/disable_lora/show/00003-1648956789.png" width="180"></td>
      <td><img src="https://raw.githubusercontent.com/foreverxiaoyu/my_blog/main/fig/LoRA/disable_lora/show/00005-2465806440.png" width="180"></td>
      <td><img src="https://raw.githubusercontent.com/foreverxiaoyu/my_blog/main/fig/LoRA/disable_lora/show/00010-1296960879.png" width="180"></td>
      <td><img src="https://raw.githubusercontent.com/foreverxiaoyu/my_blog/main/fig/LoRA/disable_lora/show/00011-3824867931.png" width="180"></td>
      <td><img src="https://raw.githubusercontent.com/foreverxiaoyu/my_blog/main/fig/LoRA/disable_lora/show/00014-1196201394.png" width="180"></td>
    </tr>
    <tr>
      <td style="width: 70px; white-space: nowrap;"><strong>有 LoRA</strong></td>
      <td><img src="https://raw.githubusercontent.com/foreverxiaoyu/my_blog/main/fig/LoRA/enable_lora/show/00002-1648956789.png" width="180"></td>
      <td><img src="https://raw.githubusercontent.com/foreverxiaoyu/my_blog/main/fig/LoRA/enable_lora/show/00004-2465806440.png" width="180"></td>
      <td><img src="https://raw.githubusercontent.com/foreverxiaoyu/my_blog/main/fig/LoRA/enable_lora/show/00008-1296960879.png" width="180"></td>
      <td><img src="https://raw.githubusercontent.com/foreverxiaoyu/my_blog/main/fig/LoRA/enable_lora/show/00012-3824867931.png" width="180"></td>
      <td><img src="https://raw.githubusercontent.com/foreverxiaoyu/my_blog/main/fig/LoRA/enable_lora/show/00013-1196201394.png" width="180"></td>
    </tr>
  </tbody>
</table>
能够看的出来没微调之前生成的图片中的人物角色脖子部分上的装饰物是星星，微调之后变成了遐蝶的紫色花花

![firefly](https://raw.githubusercontent.com/foreverxiaoyu/my_blog/main/fig/LoRA/firefly.jpg)