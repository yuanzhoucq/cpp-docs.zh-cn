---
title: "内联程序集中的数据指令和运算符 | Microsoft Docs"
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
  - "__asm 关键字 [C++], 引用限制"
  - "数据指令 [C++]"
  - "指令 [C++], MASM"
  - "内联程序集, 数据指令"
  - "内联程序集, 运算符"
  - "MASM (Microsoft Macro Assembler), 指令"
  - "MASM (Microsoft Macro Assembler), 运算符"
  - "MASM (Microsoft Macro Assembler), 结构"
  - "运算符 [MASM]"
  - "结构 [C++], MASM"
ms.assetid: fb7410c7-156a-4131-bcfc-211aa70533e3
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 内联程序集中的数据指令和运算符
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 尽管 `__asm` 块可以引用 C 或 C\+\+ 数据类型和对象，但它不能定义具有 MASM 指令或运算符的数据对象。  具体而言，您不能使用定义指令 **DB**、`DW`、**DD**、`DQ`、`DT` 和 `DF` 或运算符 `DUP` 或 **THIS**。  MASM 结构和记录也不可用。  内联汇编程序不接受指令 `STRUC`、`RECORD`、**WIDTH** 或 **MASK**。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [在 \_\_asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)