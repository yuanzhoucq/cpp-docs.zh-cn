---
title: 内联程序集的数据指令和运算符 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data directives [C++]
- __asm keyword [C++], referencing limitations
- MASM (Microsoft Macro Assembler), directives
- directives [C++], MASM
- MASM (Microsoft Macro Assembler), structures
- operators [MASM]
- inline assembly, operators
- inline assembly, data directives
- MASM (Microsoft Macro Assembler), operators
- structures [C++], MASM
ms.assetid: fb7410c7-156a-4131-bcfc-211aa70533e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0bd3bc686cc8cee1a02e9df936f80f542bec26bd
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32051380"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>内联程序集中的数据指令和运算符
## <a name="microsoft-specific"></a>Microsoft 专用  
 尽管 `__asm` 块可以引用 C 或 C++ 数据类型和对象，但它不能定义具有 MASM 指令或运算符的数据对象。 具体而言，不能使用定义指令**DB**， `DW`， **DD**， `DQ`， `DT`，和`DF`，或运算符`DUP`或**这**。 MASM 结构和记录也不可用。 内联汇编程序不接受指令`STRUC`， `RECORD`，**宽度**，或**掩码**。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)