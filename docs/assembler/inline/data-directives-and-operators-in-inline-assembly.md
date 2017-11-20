---
title: "内联程序集的数据指令和运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9875a6d4ee0b061db609f45d574a80a7ee5424ab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>内联程序集中的数据指令和运算符
## <a name="microsoft-specific"></a>Microsoft 专用  
 尽管 `__asm` 块可以引用 C 或 C++ 数据类型和对象，但它不能定义具有 MASM 指令或运算符的数据对象。 具体而言，不能使用定义指令**DB**， `DW`， **DD**， `DQ`， `DT`，和`DF`，或运算符`DUP`或**这**。 MASM 结构和记录也不可用。 内联汇编程序不接受指令`STRUC`， `RECORD`，**宽度**，或**掩码**。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)