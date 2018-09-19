---
title: 错误 C1060 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1060
dev_langs:
- C++
helpviewer_keywords:
- C1060
ms.assetid: feaf305c-c84c-4160-b974-50e283412849
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5288400b5c7303840dfef98c7e1a48e7cf5d06f8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032559"
---
# <a name="fatal-error-c1060"></a>错误 C1060

编译器的堆空间不足

操作系统或运行时库无法满足内存要求。

### <a name="to-fix-this-error-try-the-following-possible-solutions"></a>若要修复此错误，请尝试以下可能的解决方案

1. 如果编译器还发出错误[C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)并[C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md)，使用[/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)编译器选项减少内存分配限制。 如果减少剩余内存分配，更多堆空间可用于应用程序。

     如果[/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)选项已设置，请尝试将其删除。 堆空间可能已用完，因为选项中指定的内存分配限制太高。 编译器使用的默认限制，如果删除[/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)选项。

1. 如果你正在 64 位平台上进行编译，请使用 64 位编译器工具集。 有关信息，请参阅[如何： 启用 64 位 Visual c + + 工具集在命令行上的](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)。

1. 在 32 位 Windows，请尝试使用[3GB](https://support.microsoft.com/en-us/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) boot.ini 开关。

1. 增加 Windows 交换文件的大小。

1. 关闭其他正在运行的程序。

1. 消除不需要的包含文件。

1. 消除不需要的全局变量，例如，通过动态分配内存而不是声明一个大数组。

1. 消除未使用的声明。

9. 将当前文件拆分成更小的文件。