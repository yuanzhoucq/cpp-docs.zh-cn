---
title: 在 Visual Studio 中新建 C++ Linux 项目 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2017
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 4d4d11ec459215d81996d1daea420513c21b10b9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="create-a-new-linux-project"></a>新建 Linux 项目
为 Linux 编码时，可以选择创建 Visual Studio 项目还是 CMake 项目。 本主题介绍如何创建 Visual Studio 项目。 有关 CMake 项目的信息，请参阅[配置 Linux CMake 项目](cmake-linux-project.md)。

若要在 Visual Studio 中新建 Linux 项目，请执行以下操作：

1. 在 Visual Studio 中选择“**文件 > 新建项目**”，或按 **Ctrl + Shift + N**。
1. 依次选择“Visual C++ > 跨平台 > Linux”节点，再选择要创建的项目类型，输入名称/位置，再单击“确定”。

   ![新建 Linux 项目](media/newproject.png)

   | 项目类型 | 描述
   | ------------ | ---
   | **Blink (Raspberry)**           | 项目针对 Raspberry Pi 设备，写入示例代码以让 LED 闪烁
   | **控制台应用程序 (Linux)** | 项目针对任何 Linux 计算机，写入示例代码以将文本输出到控制台
   | **空项目 (Linux)**       | 项目针对任何 Linux 计算机，未写入任何示例代码
   | **生成文件项目 (Linux)**    | 项目针对任何 Linux 计算机，使用标准生成文件的生成系统生成

