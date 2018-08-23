---
title: 错误 C1060 |Microsoft 文档
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
ms.openlocfilehash: 5aa168c185bafbfd6fadf3f0d5f1320ba4f43d60
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226298"
---
# <a name="fatal-error-c1060"></a>错误 C1060
编译器的堆空间不足  
  
 操作系统或运行时库无法满足内存要求。  
  
### <a name="to-fix-this-error-try-the-following-possible-solutions"></a>若要修复此错误，请尝试以下可能的解决方案  
  
1.  如果编译器还发出错误[C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)和[C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md)，使用[/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)编译器选项减少内存分配限制。 如果减少剩余内存分配，更多堆空间可用于应用程序。  
  
     如果[/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)选项已设置，请尝试将其删除。 堆空间可能已用完，因为选项中指定的内存分配限制太高。 编译器使用的默认限制，如果你删除[/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)选项。  
  
2.  如果你正在 64 位平台上进行编译，请使用 64 位编译器工具集。 有关信息，请参阅[如何： 启用 64 位 Visual c + + 工具集在命令行上的](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)。  
  
3.  在 32 位 Windows 上，请尝试使用[3 GB](http://go.microsoft.com/fwlink/p/?linkid=177831) boot.ini 开关。  
  
4.  增加 Windows 交换文件的大小。  
  
5.  关闭其他正在运行的程序。  
  
6.  消除不需要的包含文件。  
  
7.  消除不需要的全局变量，例如，通过动态分配内存而不是声明一个大数组。  
  
8.  消除未使用的声明。  
  
9. 将当前文件拆分成更小的文件。