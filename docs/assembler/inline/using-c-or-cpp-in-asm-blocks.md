---
title: "在 __asm 块中使用 C 或 C++ | Microsoft Docs"
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
  - "__asm 关键字 [C++], 其中的 C/C++ 关键字"
  - "注释, 在 __asm 块中"
  - "常量, 在 __asm 块中"
  - "内联程序集, 将指令与 C/C++ 语句混合使用"
  - "宏, __asm 块"
  - "预处理器指令"
  - "预处理器指令, 在 __asm 块中使用"
  - "预处理器, 指令"
  - "symbols, 在 __asm 块中"
  - "类型名称, 在 __asm 块中使用"
  - "typedef 名称, 在 __asm 块中使用"
ms.assetid: ae8b2b52-6b75-42e3-ac0c-ad02d922ed97
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 在 __asm 块中使用 C 或 C++
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 由于内联程序集指令可以与 C 或 C\+\+ 语句组合，因此可以通过名称引用 C 或 C\+\+ 变量，或者使用这些语言的多个其他元素。  
  
 `__asm` 块可以使用下列语言元素：  
  
-   符号（包括标签、变量和函数名称）  
  
-   常量（包括符号常量和 `enum` 成员）  
  
-   宏和预处理器指令  
  
-   注释（**\/\* \*\/** 和 **\/\/**）  
  
-   类型名称（其中的 MASM 类型是合法的）  
  
-   `typedef` 名称，通常与运算符（例如，**PTR** 和 **TYPE**）一起使用或用于指定结构或联合成员  
  
 在 `__asm` 块内，您可以使用 C 表示法或汇编基数表示法指定整数常量（例如，0x100 和 100h 等效）。  这允许您在 C 中定义（使用 `#define`）常量，然后在 C 或 C\+\+ 以及程序的程序集部分中使用该常量。  您还可以通过在其前面放置 0 以八进制指定常量。  例如，0777 指定一个八进制常量。  
  
## 您想进一步了解什么？  
  
-   [在 \_\_asm 块中使用运算符](../../assembler/inline/using-operators-in-asm-blocks.md)  
  
-   [在 \_\_asm 块中使用 C 或 C\+\+ 符号](../../assembler/inline/using-c-or-cpp-symbols-in-asm-blocks.md)  
  
-   [在 \_\_asm 块中访问 C 或 C\+\+ 数据](../../assembler/inline/accessing-c-or-cpp-data-in-asm-blocks.md)  
  
-   [使用内联程序集编写函数](../../assembler/inline/writing-functions-with-inline-assembly.md)  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [内联汇编程序](../../assembler/inline/inline-assembler.md)