---
title: "Pytorch的某些点"
date: 2024-07-11T16:37:21+08:00
lastmod: 2024-07-11T16:37:21+08:00
author: ["jceltics"]
keywords: 
- 
categories: # 没有分类界面可以不填写
- 
tags: # 标签
- 
description: ""
weight:
slug: ""
draft: false # 是否为草稿
comments: true # 本页面是否显示评论
reward: false # 打赏
mermaid: true #是否开启mermaid
showToc: true # 显示目录
TocOpen: true # 自动展开目录
hidemeta: false # 是否隐藏文章的元信息，如发布日期、作者等
disableShare: true # 底部不显示分享栏
showbreadcrumbs: true #顶部显示路径
cover:
    image: "" #图片路径例如：posts/tech/123/123.png
    zoom: # 图片大小，例如填写 50% 表示原图像的一半大小
    caption: "" #图片底部描述
    alt: ""
    relative: false
---

## Pytorch里的register_parameter和register_buffer是干什么的？

* **register_parameter**：
  
  * 等价于直接调用nn.Parameter，注册一个可以训练的参数
  
  * 会被放入模型的state_dict中
  
  * 当调用to时会跟随着一起转移到相应的设备上

* **register_buffer**
  
  * 在模型中定义常量或者是不需要训练的变量
  
  * 会写入state_dict，可以被保存
  
  * 当调用to时会跟随着一起转移到相应的设备上

|                   | register_parameter | register_buffer |
| ----------------- |:------------------:|:---------------:|
| 加入模型的parameters列表 | 会                  | 不会              |
| 加入模型的state_dict   | 会                  | 会               |
| 随模型一起进行设备转移       | 会                  | 会               |
