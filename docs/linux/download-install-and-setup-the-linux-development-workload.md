---
title: "下载、安装和设置 Linux 工作负载 | Microsoft 文档"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
author: BrianPeek
ms.author: brpeek
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: dff1e9e03911f65dfcffcd078e0739224f73f4aa
ms.openlocfilehash: 09ce0024b7a98729b28968fff081ed105b5463e1

---

# <a name="download-install-and-setup-the-linux-workload"></a>下载、安装和设置 Linux 工作负载

## <a name="visual-studio-setup"></a>Visual Studio 安装
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



<!--HONumber=Feb17_HO4-->


