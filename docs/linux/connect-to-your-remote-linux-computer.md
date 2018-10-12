---
title: 在 Visual Studio 中连接到远程 Linux 计算机 | Microsoft Docs
description: 如何从 Visual Studio C++ 项目内连接到远程 Linux 计算机。
ms.custom: ''
ms.date: 07/20/2018
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: bba17549abc9f747d93299cf22c39ae7c3e8f4d6
ms.sourcegitcommit: 87d317ac62620c606464d860aaa9e375a91f4c99
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2018
ms.locfileid: "45601439"
---
# <a name="connect-to-your-remote-linux-computer"></a>连接到远程 Linux 计算机

在 Visual Studio 中生成 C++ Linux 项目时，将 Linux 代码复制到远程 Linux 计算机，然后基于 Visual Studio 设置进行编译。 若要设置此远程连接，请执行以下操作：

1. 首次生成项目或手动创建新条目的方法：选择“**工具 > 选项**”，然后打开“**跨平台 > 连接管理器**”节点，单击“**添加**”按钮。

   ![连接管理器](media/settings_connectionmanager.png)

   在任一方案中，均将显示“**连接到远程系统**”窗口。
   
   ![连接到远程系统](media/connect.png)

1. 输入以下信息：

   | 条目 | 描述
   | ----- | ---
   | **主机名**           | 目标设备的名称或 IP 地址
   | **端口**                | 运行 SSH 服务的端口，通常为 22
   | **用户名**           | 要进行身份验证的用户
   | **身份验证类型** | 同时支持密码或私钥
   | **密码**            | 输入的用户名的密码
   | **私钥文件**    | 为 ssh 连接创建的私钥文件
   | **密码**          | 与上面选择的私钥一起使用的密码

1. 单击“**连接**”按钮，尝试连接到远程计算机。  如果连接失败，则需要更改的输入框将以红色标出。

   ![连接管理器错误](media/settings_connectionmanagererror.png)