---
title: 在 Visual Studio 中安装 C++ Linux 工作负荷 | Microsoft Docs
description: 介绍如何在 Visual Studio 中下载、安装和设置用于 C++ 的 Linux 工作负荷。
ms.custom: ''
ms.date: 07/20/2018
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: e33b9ac72ca7691ccbb80a9a30349d3a1e31e194
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207554"
---
# <a name="download-install-and-setup-the-linux-workload"></a>下载、安装和设置 Linux 工作负载

若要使用 Visual Studio IDE 创建和调试针对 Linux 的 C++ 项目，必须安装**使用 C++ 的 Linux 开发**工作负荷。

## <a name="visual-studio-setup"></a>Visual Studio 安装程序
1. 启动 Visual Studio 安装程序并选择“**使用 C++ 的 Linux 开发**”工作负载。

   ![用于 Linux 开发的 Visual C++ 扩展](media/linuxworkload.png)

2. 单击“**安装**”以继续进行安装。

## <a name="linux-setup"></a>Linux 安装程序
目标 Linux 计算机必须安装 **openssh-server**、**g++**、**gdb** 和 **gdbserver**，并且必须运行 ssh 守护程序。  如果这些尚不存在，则可以进行安装，如下所示：
 
1. 在 Linux 计算机上的 shell 提示符下，运行：

   `sudo apt-get install openssh-server g++ gdb gdbserver`

   由于 sudo 命令，可能会提示你输入 root 密码。  如果是这样，输入密码然后继续。  完成后，将可以安装这些服务和工具。

1. 通过运行以下命令，确保 ssh 服务在 Linux 计算机上运行：

   `sudo service ssh start`
   
   这将启动该服务并在后台运行它，准备接受连接。
