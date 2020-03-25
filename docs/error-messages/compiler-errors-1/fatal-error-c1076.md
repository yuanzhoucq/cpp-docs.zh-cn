---
title: 错误 C1076
ms.date: 03/08/2019
f1_keywords:
- C1076
helpviewer_keywords:
- C1076
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
ms.openlocfilehash: ca5117342d406983e8cba675c2589d2431d09d38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204173"
---
# <a name="fatal-error-c1076"></a>错误 C1076

> 编译器限制 : 达到内部堆限制；使用 /Zm 指定更高的限制

此错误可能是由过多符号或过多模板实例化引起的。 从 Visual Studio 2015 开始，此消息可能是由于过多的并行生成过程导致的 Windows 虚拟内存压力导致的。 在这种情况下，除非使用的是 `#pragma hdrstop` 指令，否则应忽略使用 **/zm**选项的建议。

若要解决此错误，请执行以下操作：

1. 如果预编译标头使用 `#pragma hdrstop` 指令，请使用[/zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)选项将编译器内存限制设置为[C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md)错误消息中指定的值。 有关如何在 Visual Studio 中设置此值的详细信息，请参阅[/zm （指定预编译头内存分配限制）](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)中的 "备注" 部分。

1. 请考虑将使用 **/maxcpucount**选项指定的并行进程数减少到 MSBUILD。EXE，并将 **/mp**选项与 CL 一起提供.EXE. 有关详细信息，请参阅[预编译头（PCH）问题和建议](https://devblogs.microsoft.com/cppblog/precompiled-header-pch-issues-and-recommendations/)。

1. 如果正在 64 位操作系统中使用 32 位托管编译器，请改用 64 位托管编译器。 有关详细信息，请参阅[如何：在命令行上启用 64 C++位可视化工具集](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)。

1. 消除不需要的包含文件。

1. 消除不需要的全局变量，例如，动态分配内存而不是声明一个大数组。

1. 消除未使用的声明。

如果在生成开始后立即发生 C1076，则对于程序，为 **/zm**指定的值可能太高。 减小 **/zm**值。
