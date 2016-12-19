---
title: "内联程序集中的 MASM 宏指令 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "指令, 宏"
  - "内联程序集, 宏指令"
  - "宏, 指令"
  - "MASM (Microsoft Macro Assembler), 内联程序集宏指令"
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 内联程序集中的 MASM 宏指令
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 内联汇编程序不是宏汇编程序。  不能使用 MASM 宏指令（**MACRO**、`REPT`、**IRC**、`IRP` 和 `ENDM`）或宏运算符（**\<\>**、**\!**、**&**、`%` 和 `.TYPE`）。  但是，`__asm` 块可以使用 C 预处理器指令。  有关详细信息，请参阅[在 \_\_asm 块中使用 C 或者 C\+\+](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [在 \_\_asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)