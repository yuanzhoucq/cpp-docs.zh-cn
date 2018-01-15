---
title: "内联程序集中的 MASM 宏指令 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0df9f8584b87e511c43430a5c0df7dac61805ede
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="masm-macro-directives-in-inline-assembly"></a>内联程序集中的 MASM 宏指令
## <a name="microsoft-specific"></a>Microsoft 专用  
 内联汇编程序不是宏汇编程序。 不能使用的 MASM 宏指令 (**宏**， `REPT`， **IRC**， `IRP`，和`ENDM`) 或宏运算符 (**<>**，**!**，  **&** ， `%`，和`.TYPE`)。 但是，`__asm` 块可以使用 C 预处理器指令。 请参阅[使用 C 或 c + + 在 __asm 块中](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)有关详细信息。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)