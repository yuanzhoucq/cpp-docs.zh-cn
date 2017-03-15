---
title: "在 __asm 块中使用 C 或 C++ 符号 | Microsoft Docs"
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
  - "__asm 关键字 [C++], 语法"
  - "symbols, 在 __asm 块中"
  - "Visual C, __asm 块中的符号"
  - "Visual C++, 在 __asm 块中"
ms.assetid: 0758ffdc-dfe9-41c8-a5e1-fd395bcac328
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 在 __asm 块中使用 C 或 C++ 符号
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定  
 `__asm`块，可以引用块将出现在其中的作用域中任何 C 或 c \+ \+ 符号。  （C 和 c \+ \+ 符号的变量名称、 函数名称和标签 ； 也就是说，不是符号常量的名称或`enum`成员。  您不能调用 c \+ \+ 成员函数）  
  
 使用 C 和 c \+ \+ 符号应用几个限制：  
  
-   每个程序集语言语句可以包含仅在一个 C 或 c \+ \+ 符号。  多个符号可以出现在同一程序集指令只与**长度**， **类型**，和 **大小**表达式。  
  
-   函数中引用`__asm`块必须声明前面的程序 \(原型）。  否则，编译器无法区分函数名称和标签在`__asm`块。  
  
-   `__asm`块不能与任何 C 或 c \+ \+ 符号使用相同的拼写 MASM 保留字 （不考虑大小写）。  MASM 保留字包含指令名称如**推**和 SI 等名称注册。  
  
-   在无法识别结构和联合标记`__asm`块。  
  
 **最终 Microsoft 特定**  
  
## 请参阅  
 [在 \_\_asm 块中使用 C 或 C\+\+](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)