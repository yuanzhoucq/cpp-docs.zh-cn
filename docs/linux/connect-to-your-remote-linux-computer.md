---
title: "连接到远程 Linux 计算机 | Microsoft Docs"
ms.custom: 
ms.date: 11/06/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-linux
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 4ff19875064302e891236c931f28ebef630904e4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="connect-to-your-remote-linux-computer"></a>连接到远程 Linux 计算机

进行生成时，将 Linux 代码复制到远程 Linux 计算机，然后根据在 Visual Studio 中选择的设置在该系统上进行编译。  若要设置此远程连接：

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
   | **私钥文件**    | 为 ssh 连接创建的私钥
   | **密码**          | 与上面选择的私钥一起使用的密码

1. 单击“**连接**”按钮，尝试连接到远程计算机。  如果连接失败，则需要更改的输入框将以红色标出。

   ![连接管理器错误](media/settings_connectionmanagererror.png)