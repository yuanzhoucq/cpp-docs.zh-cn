---
title: 在 Visual Studio 中新建 C++ Linux 项目
ms.date: 09/12/2018
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: 394fc5727035dd5a65b67ebf26a925fd3484582e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623023"
---
# <a name="create-a-new-linux-project"></a>新建 Linux 项目

首先，请确保已安装用于 Visual Studio 的 Linux 开发工作负荷。 有关详细信息，请参阅[下载、安装和设置 Linux 工作负荷](download-install-and-setup-the-linux-development-workload.md)。

在 Visual Studio for Linux 中创建新的 C++ 项目时，可以选择创建 Visual Studio 项目还是 CMake 项目。 本主题介绍如何创建 Visual Studio 项目。 有关创建和使用现有 CMake 项目的信息，请参阅[配置 Linux CMake 项目](cmake-linux-project.md)。

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

