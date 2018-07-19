---
title: 内联汇编的优点 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- assembler [C++], advantages
- inline assembly [C++], about inline assembly
- inline assembly [C++], using
ms.assetid: 94364d97-faa7-4bdf-8473-570956986c51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 998ec5ff04911d3e476f0864f81f82b804969a82
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32051702"
---
# <a name="advantages-of-inline-assembly"></a>内联汇编的优点
## <a name="microsoft-specific"></a>Microsoft 专用  
 由于内联汇编程序不需要单独的程序集和链接步骤，因此它比单独的汇编程序更方便。 内联程序集代码可以使用任何 C 变量或范围中的函数名，因此，将其与程序的 C 代码集成非常容易。 由于程序集代码可与 C 或 C++ 语句内联组合，因此它可以执行在 C 或 C++ 中难以完成或无法完成的任务。  
  
 内联程序集的用法包括：  
  
-   使用汇编语言编写函数。  
  
-   代码的点优化速度临界区。  
  
-   通过硬件直接访问设备驱动程序。  
  
-   为“naked”调用编写 prolog 和 epilog 代码。  
  
 内联程序集是一个具有特殊用途的工具。 如果您计划通过端口将应用程序传输到其他计算机，您可能需要在单独的模块中放置计算机特定的代码。 由于内联汇编程序不支持任何 Microsoft 宏汇编程序 (MASM) 的宏和数据指令，因此您可能会发现对此类模块使用 MASM 会更方便。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [内联汇编程序](../../assembler/inline/inline-assembler.md)