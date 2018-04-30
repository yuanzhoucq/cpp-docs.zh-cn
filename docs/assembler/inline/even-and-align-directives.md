---
title: EVEN 和 ALIGN 指令 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
f1_keywords:
- align
- EVEN
dev_langs:
- C++
helpviewer_keywords:
- EVEN directive
- directives, MASM
- MASM (Microsoft Macro Assembler), directives
- NOP (no operation instruction)
- ALIGN directive
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a43425a4038ffb140eeaa0a9d111a39fc5c11ff0
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="even-and-align-directives"></a>EVEN 和 ALIGN 指令
## <a name="microsoft-specific"></a>Microsoft 专用  
 尽管内联汇编程序不支持大多数 MASM 指令，但它支持`EVEN`和**ALIGN**。 这些指令放**NOP** （非运算） 程序集代码中，将标签与特定边界对齐所需的说明。 对某些处理器来说，这使得指令取回操作更加有效。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)