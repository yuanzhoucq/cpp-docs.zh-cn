---
title: 内联程序集中的 MASM 宏指令 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cfd8e3ca5fb6bf65a288c17b1754d567b2b081a8
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32049846"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>内联程序集中的 MASM 宏指令
## <a name="microsoft-specific"></a>Microsoft 专用  
 内联汇编程序不是宏汇编程序。 不能使用的 MASM 宏指令 (**宏**， `REPT`， **IRC**， `IRP`，和`ENDM`) 或宏运算符 (**<>**，**!**， **&**， `%`，和`.TYPE`)。 但是，`__asm` 块可以使用 C 预处理器指令。 请参阅[使用 C 或 c + + 在 __asm 块中](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)有关详细信息。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)