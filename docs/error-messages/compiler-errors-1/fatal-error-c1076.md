---
title: 错误 C1076
ms.date: 11/04/2016
f1_keywords:
- C1076
helpviewer_keywords:
- C1076
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
ms.openlocfilehash: 70525426182a923de85eecbd5a3335693d6e8949
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644686"
---
# <a name="fatal-error-c1076"></a>错误 C1076

编译器限制 : 达到内部堆限制；使用 /Zm 指定更高的限制

此错误可能是由过多符号或过多模板实例化引起的。

解决此问题的方法是：

1. 使用[/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)选项将编译器内存限制设置中指定的值为[C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md)错误消息。 有关详细信息，包括如何在 Visual Studio 中设置此值，请参阅中的备注部分[/Zm （指定预编译标头内存分配限额）](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)。

1. 如果正在 64 位操作系统中使用 32 位托管编译器，请改用 64 位托管编译器。 有关详细信息，请参阅[如何： 启用 64 位 Visual c + + 工具集在命令行上的](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)。

1. 消除不需要的包含文件。

1. 消除不需要的全局变量，例如，动态分配内存而不是声明一个大数组。

1. 消除未使用的声明。

1. 将大函数拆分为更小的函数。

1. 将大类拆分为更小的类。

1. 将当前文件拆分成更小的文件。

如果立即在生成开始后，为指定的值发生 C1076 **/Zm**而言可能太高为您的程序。 减少 **/Zm**值。