---
title: 错误 C1076
ms.date: 03/08/2019
f1_keywords:
- C1076
helpviewer_keywords:
- C1076
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
ms.openlocfilehash: 91753a49498548b4e523cd8564ee7a7ca7a3b373
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751669"
---
# <a name="fatal-error-c1076"></a>错误 C1076

> 编译器限制 : 达到内部堆限制；使用 /Zm 指定更高的限制

此错误可能是由过多符号或过多模板实例化引起的。 从 Visual Studio 2015 开始，此消息可能会导致 Windows 虚拟内存不足引起的太多的并行生成进程。 在此情况下，建议使用 **/Zm**应忽略选项，除非你使用`#pragma hdrstop`指令。

解决此问题的方法是：

1. 如果使用预编译标头`#pragma hdrstop`指令，使用[/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)选项将编译器内存限制设置中指定的值为[C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md)错误消息。 有关详细信息，包括如何在 Visual Studio 中设置此值，请参阅中的备注部分[/Zm （指定预编译标头内存分配限额）](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)。

1. 请考虑减少使用指定的并行进程数 **/maxcpucount** MSBUILD 选项。结合 EXE **/MP**改为 CL 选项。EXE。 有关详细信息，请参阅[预编译标头 (PCH) 问题和建议](https://devblogs.microsoft.com/cppblog/precompiled-header-pch-issues-and-recommendations/)。

1. 如果正在 64 位操作系统中使用 32 位托管编译器，请改用 64 位托管编译器。 有关详细信息，请参阅[如何：启用 64 位 Visual c + + 工具集在命令行上](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)。

1. 消除不需要的包含文件。

1. 消除不需要的全局变量，例如，动态分配内存而不是声明一个大数组。

1. 消除未使用的声明。

如果立即在生成开始后，为指定的值发生 C1076 **/Zm**而言可能太高为您的程序。 减少 **/Zm**值。