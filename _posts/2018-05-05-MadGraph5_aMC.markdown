---
layout: post
title: MadGraph5_aMC 教程
author: ResonHou
categories: 学术软件教程
tags:
 - SoftWare
---

* content
{:toc}

理论物理高能唯象学的分析流程是一个繁锁的过程，但大体上分为理论的程序化、从理论中预言可观测量、数据分析并与实验数据对比。
本文主要立足从理论中预言可观测量部分，解说计算工具包：MadGraph5_aMC
<!--more-->
## 安装

### 环境要求
- Ubuntu 系统（或者其他Linux发行版）
- 可连网
- 最好有界面（主要用于使用浏览器下载安装包）

### 下载安装
> 资源下载：[MadGraph5_aMC@NLO](https://launchpad.net/mg5amcnlo) in Launchpad.  
> 点击页面右侧的绿色版本下载安装包（ ubuntu默认下载到目录：~/Downloads/ ）  

然后运行下面的命令:  

```
cd ~/Downloads                  # 进入下载的压缩包所在的目录
tar -xzvf MG5_aMC_v***.tar.gz   # 解压 "***"代表版本号
cd ./MG5_aMC_v***               # 进入 MG5 所在的目录
./bin/mg5_aMC                     # 运行 MG5 ，命令行提示符变为：MG5_aMC>
```

### 使用 Pythia 和 Delphes
MadGraph5_aMC 可实现除计算散射截面、产生事例之外更多的功能，通过使用内置的下载脚本下载插件实现。可下载用于实现**强子化**的工具 Pythia ，用于实现快速探测器模拟的工具 Delphes 或者 PGS ， 用于事例分析的工具 MadAnalysis 等。
```
MG5_aMC>install pythia8         # MG5_aMC>只是提示符，代表 MG5 开启，不用输到命令行，其后面的才是命令
MG5_aMC>install Delphes         # 注意区分大小写，在输入 install 后，可点击两次 Tab 键，显示所有的选项。
```
其他的选项可自行查阅[ MG5 说明书](https://arxiv.org/abs/1405.0301v2)。

## 使用说明
MadGraph5_aMC 可用于实现指定模型下的任意过程计算，最终给出过程的散射截面，并且产生用于后期分析的事例文件。  
### 初级操作

#### 产生代码并运算代码
> 技巧：单击 `Tab` 键补全命令，双击 `Tab` 键显示所有可选项
```
MG5_aMC>import model sm         # 导入模型文件
MG5_aMC>generate p p > t t~     # 产生pp到tt的过程（仅为举例），语法参考 MG5 说明书附录
MG5_aMC>display diagrams        # 显示过程费曼图
MG5_aMC>output ./process/pptt   # 生成代码，存储在当前目录下的 ./process/pptt/ 目录中
MG5_aMC>launch                  # 运行代码，计算过程的截面，且产生事例
```
launch 命令可以不运行，只是生成代码，不运算。当要运算时，先进入代码目录（例：./process/pptt/），再执行 `generate_events` 命令开始计算。这种方式等价于直接运行 `launch` 命令，不同之处在于这样可以多次运算代码，产生多个事例文件。
```
cd ~/Downloads/MG5_aMC_***/process/pptt/    # 以实际路径为准
./bin/generate_events           # 开始计算
```
#### 运算代码前的设置（很重要）
> 强调：这部分很重要，可详细阅读界面内容。

当开始运算代码的之后，会出现如下图的交互界面：![jiaohu.png](https://i.loli.net/2018/05/05/5aedc3746933d.png)  
这是让你设置是否使用 Pythia 和 Delphes 的，若使用 Pythia ，可以输入 1 ，点击`Enter`键。可以详细阅读这部分内容，根据需要设置好之后，输入 0 ,点击`Enter`键。  
之后会出现一个类似的界面，用于编辑参数卡片。输入 1 ，可编辑 param_card.dat 文件。

所有卡片文件都存放在代码目录的 ./process/pptt/Cards/ 目录中，可以在运算代码之前更改相关卡片文件。

### 高级操作
这部分主要是想要说明使用 proc_card.dat 文件，来将上面的命令集成到一个批处理文件中。并没有什么高级的命令。

## MG5_aMC 目录结构及意义
鉴于现在的程序学习过程操作大于意义的实际情况，我将详细的物理意义放在操作之后进行说明。  
.  
├── bin  
├── Delphes  
├── HEPTools  
├── input  
├── madgraph  
├── models  
├── process  
└── README  
以上为 MG5_aMC_*** 目录中的主要文件目录。下面针对第一个目录说明其作用。

* 
