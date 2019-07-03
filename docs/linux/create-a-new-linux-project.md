---
title: 在 Visual Studio 中新建 C++ Linux 项目
ms.date: 06/11/2019
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: 0377e21177b29d998fc3e66bb1863dbc127c1fbe
ms.sourcegitcommit: fde637f823494532314790602c2819f889706ff6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/13/2019
ms.locfileid: "67042706"
---
# <a name="create-a-new-linux-project"></a>新建 Linux 项目

::: moniker range="vs-2015"

Linux 项目在 Visual Studio 2017 及更高版本中提供。

::: moniker-end

首先，请确保已安装用于 Visual Studio 的 Linux 开发工作负荷  。 有关详细信息，请参阅[下载、安装和设置 Linux 工作负荷](download-install-and-setup-the-linux-development-workload.md)。

在 Visual Studio 中创建适用于 Linux 的新 C++ 项目时，可以选择创建 Visual Studio 项目或 CMake 项目。 本文介绍如何创建 Visual Studio 项目。 有关如何创建和使用现有 CMake 项目的信息，请参阅[创建并配置 Linux CMake 项目](cmake-linux-project.md)。

## <a name="to-create-a-new-linux-project"></a>新建 Linux 项目

要在 Visual Studio 中新建 Linux 项目，请按以下步骤进行操作：

::: moniker range="vs-2019"

1. 在 Visual Studio 中选择“**文件 > 新建项目**”，或按 **Ctrl + Shift + N**。
1. 将“语言”设置为“C++”，然后搜索“Linux”   。 选择要创建的项目类型，然后选择“下一步”  。 输入“名称”和“位置”，然后选择“创建”    。

   ![新建 Linux 项目](media/newproject-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

1. 在 Visual Studio 中选择“**文件 > 新建项目**”，或按 **Ctrl + Shift + N**。
1. 依次选择“Visual C++”>“跨平台”>“Linux”节点，然后选择要创建的项目类型  。 输入“名称”和“位置”，然后选择“确定”    。

   ![新建 Linux 项目](media/newproject.png)

::: moniker-end

   | 项目类型 | 说明 |
   | ------------ | --- |
   | **Blink (Raspberry)**           | 面向 Raspberry Pi 设备的项目，附带让 LED 闪烁的示例代码 |
   | **控制台应用程序 (Linux)** | 面向任何 Linux 计算机的项目，附带将文本输出到控制台的示例代码 |
   | **空项目 (Linux)**       | 面向任何 Linux 计算机的项目，不带任何示例代码 |
   | **生成文件项目 (Linux)**    | 面向任何 Linux 计算机的项目，使用标准生成文件生成系统生成 |

   ::: moniker range="vs-2019"

   借助 Visual Studio 2019，可以创建一个新的 CMake 项目。 有关详细信息，请参阅[创建并配置 Linux CMake 项目](cmake-linux-project.md)。
   
   ::: moniker-end

## <a name="next-steps"></a>后续步骤

[配置 Linux 项目](configure-a-linux-project.md)
