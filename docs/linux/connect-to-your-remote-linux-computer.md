---
title: "连接到远程 Linux 计算机 | Microsoft 文档"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-linux
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
author: BrianPeek
ms.author: brpeek
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: dd817a7d9fad4946cd0aa9f641f9e8f495f1be9a
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---

# <a name="connect-to-your-remote-linux-computer"></a>连接到远程 Linux 计算机

进行生成时，将 Linux 代码复制到远程 Linux 计算机，然后根据在 Visual Studio 中选择的设置在该系统上进行编译。  若要设置此远程连接：

1. 首次生成项目或手动创建新条目的方法：选择“**工具 > 选项**”，然后打开“**跨平台 > 连接管理器**”节点，单击“**添加**”按钮。

   ![连接管理器](media/settings_connectionmanager.png)

   在任一方案中，均将显示“**连接到远程系统**”窗口。
   
   ![连接到远程系统](media/connect.png)

1. 输入以下信息：

   | 条目 | 说明
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
