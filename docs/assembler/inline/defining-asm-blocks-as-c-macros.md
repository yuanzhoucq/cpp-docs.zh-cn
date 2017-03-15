---
title: "将 __asm 块定义为 C 宏 | Microsoft Docs"
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
  - "__asm 关键字 [C++], 作为 C 宏"
  - "宏, __asm 块"
  - "Visual C, 宏"
ms.assetid: 677ba11c-21c8-4609-bba7-cd47312243b0
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 将 __asm 块定义为 C 宏
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定**  
  
 C 宏提供一种简便方法将程序集代码插入到源代码中，但它们要求格外小心，因为到一个逻辑行扩展的宏。  若要创建无故障的宏，请遵循下列规则：  
  
-   请将`__asm`在大括号内阻止。  
  
-   将`__asm`关键字前面每个程序集指令。  
  
-   使用旧式 C 注释 \(  `/* comment */`\) 而不是程序集样式注释 \(   `; comment`\) 或单行 C 注释 \(   `// comment`）。  
  
 为了说明，下面的示例定义了一个简单的宏：  
  
```  
#define PORTIO __asm      \  
/* Port output */         \  
{                         \  
   __asm mov al, 2        \  
   __asm mov dx, 0xD007   \  
   __asm out dx, al       \  
}  
```  
  
 在第一印象后, 三个`__asm`关键字似乎多余。  在需要，但是，因为该宏扩展到单个行：  
  
```  
__asm /* Port output */ { __asm mov al, 2  __asm mov dx, 0xD007 __asm out dx, al }  
```  
  
 第三、 第四`__asm`关键字需要作为语句分隔符。  语句分隔符中识别`__asm`块是换行符和  `__asm`关键字。  定义为宏块是一个逻辑行，因为您必须将每个指令，  `__asm`.  
  
 大括号也是必不可少的。  如果忽略这些参数时，编译器可以通过右侧的宏调用同一行上的 C 或 c \+ \+ 语句相混淆。  右大括号，而编译器无法判断其中的程序集代码停止，并看到的 C 或 c \+ \+ 语句`__asm`作为程序集指令块。  
  
 以分号开头的程序集的样式注释 \(**;**） 转到行的结尾。  这因为编译器会忽略所有内容之后一直到逻辑行尾注释，在宏会导致问题。  是如此的单行 C 或 c \+ \+ 注释 \(  `// comment`）。  若要避免错误，使用旧式 C 注释 \(  `/* comment */`\) 在  `__asm`块定义为宏。  
  
 `__asm`块写入为 C 宏可以带有参数。  与普通 C 宏，但是，  `__asm`宏不能返回值。  因此，在 C 或 c \+ \+ 表达式中，不能使用这些宏。  
  
 请注意不要不加选择地调用此类型的宏。  例如，调用的函数中的程序集语言宏声明与`__fastcall`约定可能会导致意外的结果。  （请参阅[使用内容，同时保留寄存器中内联程序集](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md)。）  
  
 **最终 Microsoft 特定**  
  
## 请参阅  
 [内联汇编程序](../../assembler/inline/inline-assembler.md)