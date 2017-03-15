---
title: "EVEN 和 ALIGN 指令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "align"
  - "EVEN"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ALIGN 指令"
  - "指令, MASM"
  - "EVEN 指令"
  - "MASM (Microsoft Macro Assembler), 指令"
  - "NOP（无操作指令）"
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# EVEN 和 ALIGN 指令
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 尽管内联汇编程序不支持大多数 MASM 指令，但它支持 `EVEN` 和 **ALIGN**。  这些指令将根据需要将 **NOP**（非运算）指令放入程序集代码中，以将标签与特定边界对齐。  对某些处理器来说，这使得指令取回操作更加有效。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [在 \_\_asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)