---
title: "在 __asm 块中使用运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm 关键字 [C++], 运算符"
  - "中括号 [ ]"
  - "中括号 [ ], __asm 块"
  - "运算符 [C++], 在 __asm 块中使用"
  - "方括号 [ ]"
  - "方括号 [ ], __asm 块"
ms.assetid: a26ccfd4-40ae-4a61-952f-c417982aa8dd
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 在 __asm 块中使用运算符
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 `__asm` 块不能使用 C 或 C\+\+ 特定运算符，如 **\<\<** 运算符。  但是，C 和 MASM 共享的运算符（如 \* 运算符）将被解释为汇编语言运算符。  例如，在 `__asm` 块的外部，方括号 \(**\[ \]**\) 被解释为封闭数组下标，C 会自动将其缩放到数组中元素的大小。  在 `__asm` 块的内部，它们被视为 MASM 索引运算符，该运算符将从任何数据对象或标签（不仅仅是数组）中生成未缩放的字节偏移量。  下面的代码阐释了差异：  
  
```  
int array[10];  
  
__asm mov array[6], bx ;  Store BX at array+6 (not scaled)  
  
array[6] = 0;         /* Store 0 at array+24 (scaled) */  
```  
  
 不缩放对 `array` 的第一个引用，但缩放第二个引用。  请注意，您可以使用 **TYPE** 运算符实现基于常数的缩放。  例如，下面的语句是等效的：  
  
```  
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24  
  
array[6] = 0;                   /* Store 0 at array + 24 */  
```  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [在 \_\_asm 块中使用 C 或 C\+\+](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)