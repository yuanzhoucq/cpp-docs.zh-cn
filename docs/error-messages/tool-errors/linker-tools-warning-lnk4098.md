---
title: 链接器工具警告 LNK4098
description: 介绍不兼容库如何导致链接器工具警告 LNK4098，以及如何使用/NODEFAULTLIB 修复此问题。
ms.date: 12/02/2019
f1_keywords:
- LNK4098
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
ms.openlocfilehash: 9d0c7da0614651a98d5ed4f3bd3676c7d837ce67
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74682941"
---
# <a name="linker-tools-warning-lnk4098"></a>链接器工具警告 LNK4098

> defaultlib "*library*" 与其他库的使用冲突;使用/NODEFAULTLIB：*库*

你正在尝试链接不兼容的库。

> [!NOTE]
> 运行时库现在包含用于防止混合不同类型的指令。 如果尝试在同一程序中使用不同类型或调试和非调试版本的运行时库，则会收到此警告。 例如，如果将一个文件编译为使用一种运行时库，而另一个文件使用另一种类型（例如，"调试" 和 "零售"）并尝试链接它们，则将收到此警告。 应将所有源文件编译为使用相同的运行时库。 有关详细信息，请参阅[/md、/mt、/ld （使用运行时库）](../../build/reference/md-mt-ld-use-run-time-library.md)编译器选项。

可以使用链接器的[/verbose： LIB](../../build/reference/verbose-print-progress-messages.md)开关来确定链接器搜索的库。 例如，如果可执行文件使用多线程非调试运行时库，则报告的列表应包括 LIBCMT.LIB，而不是 LIBCMTD.LIB、MSVCRT.LIB 或 MSVCRTD.LIB。 您可以通过对每个要忽略的库使用[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) ，告知链接器忽略不正确的运行时库。

下表显示了应忽略哪些库，具体取决于要使用的运行时库。 在命令行上，为每个要忽略的库使用一个 **/NODEFAULTLIB**选项。 在 Visual Studio IDE 中，在 "**忽略特定默认库**" 属性中用分号分隔要忽略的库。

| 使用此运行时库 | 忽略这些库 |
|-----------------------------------|----------------------------|
| 多线程（libcmt.lib） | msvcrt.lib;libcmtd.lib;msvcrtd.lib |
| 使用 DLL 的多线程（msvcrt.lib） | libcmt.lib;libcmtd.lib;msvcrtd.lib |
| 调试多线程（libcmtd.lib） | libcmt.lib;msvcrt.lib;msvcrtd.lib |
| 使用 DLL 调试多线程（msvcrtd.lib） | libcmt.lib;msvcrt.lib;libcmtd.lib |

例如，如果您收到此警告，而您想要创建一个使用非调试 DLL 版本的运行时库的可执行文件，则可以将以下选项与链接器结合使用：

```cmd
/NODEFAULTLIB:libcmt.lib /NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib
```
