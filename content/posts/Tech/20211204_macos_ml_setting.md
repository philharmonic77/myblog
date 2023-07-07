---
author: "philharmonic77"
title: "MacOS机器学习环境搭建"
date: "2024-12-04"
description: ""
tags: ["python","安装教程"]
hideMeta: false
searchHidden: false
ShowBreadCrumbs: false
---
背景：介绍如何在mac上搭建机器学习环境。

## 1. 安装brew

brew是mac上常用的软件包管理工具，有了它安装或者卸载软件会比较方便。它的官方安装地址是这个：<https://docs.brew.sh/Installation>。 但因为某些大家都知道的原因，我按照上面的命令安装多次多失败了，最后才找到下面这个靠谱的安装方式：

``` shell
/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"
```

## 2. 安装anaconda

这个比较简单，在它的官网上选择合适的版本，按照指引一步一步安装就可以啦。官网是：<https://www.anaconda.com/products/individual>。

## 3. 安装tensorflow

> 如果还希望可以在自己的mac上跑深度学习模型，可以看下这部分。目前，要想在macbook上用gpu训练模型还是不太现实的。但如果你想本地写好代码，在小样本上调试好，再放到服务器上跑，那么还是可以安装一下。

直接通过conda或者pip安装最新版本的tensorflow在安装完之后并无法运行，在导入的时候会报错：
``` shell
zsh: illegal hardware instruction python
```

这是因为没有安装适合M1芯片的版本，可以在这里查看如何安装：<https://github.com/apple/tensorflow_macos>，目前最新的适合M1的版本是v2.5。

我安装的是网友分享的适合mac的tensorflow2.4.1版本，具体步骤是：

### a. 下载wheel文件（放到Downloads文件夹）
<https://drive.google.com/drive/folders/1oSipZLnoeQB0Awz8U68KYeCPsULy_dQ7>

### b. 利用conda创建虚拟环境并安装
虽然也可以在默认的python环境上安装，但进行环境隔离今后可以避免各种冲突，所以我采用的是这种方式。
``` shell
## 创建python版本为3.8.5的python环境，name是tf38
conda create -n tf38 python=3.8.5
## 查看
conda info --envs
## 激活该环境
conda activate tf38
## 安装
pip install ～/Downloads/tensorflow-2.4.1-py3-none-any.whl
## 关闭该环境
conda deactivate
## 如果未来想删除该环境
conda remove -n tf38 -all
```

## 4. 配置jupyter notebook

这部分主要包括如何在jupyter里找到刚才安装的tf环境，以及安装一些常用的notebook插件。

### a. 找到刚安装的虚拟环境

安装完anaconda之后，在terminal里输入jupyter notebook就可以打开了。但还需要完成以下几步才可以在“新建”菜单里找到tf38这个环境。
```shell
conda activate tf38
conda install ipykernel
python -m ipykernel install-- user --name tf38
```

### b. 安装插件

我用起来必不可少的notebook插件主要是代码自动补全和目录插件。可以通过执行下面的命令来安装：
``` shell 
## 防止安装失败，先修改下超时配置
pip install —-default-timeout=1000 jupyter_contrib_nbextensions
jupyter contrib nbextentions install —user —skip-running-check
```
之后，启动notebook，点击nbextensions，在众多可选择的插件中勾选就可以。如果需要自动目录，选择"table of content"，代码补全是"Hinterland"。

## 5. 安装graphviz

有可视化决策树，神经网络结构需求的小伙伴们还可以安装下graphviz，这个在安装了brew之后，只需要一个命令就可以完成啦！
``` shell 
brew install graphviz
```

