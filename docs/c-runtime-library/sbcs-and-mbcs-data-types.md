---
title: "SBCS 和 MBCS 数据类型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MBCS"
  - "SBCS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SBCS 和 MBCS 数据类型"
  - "数据类型 [C], MBCS 和 SBCS"
ms.assetid: 4c3ef9da-e397-48d4-800e-49dba36db171
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# SBCS 和 MBCS 数据类型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

所有 Microsoft `MBCS` 类型库运行库程序（只处理一个多字节字符或多字节字符的一个字节）应使用 `unsigned` `int` 参数 \(其中是 0x00 \<\= 字符值 \<\= 0xFFFF 0x00 \<和 \= 字节值 \<为 0xFF。\)  在字符串上下文处理多字节字节或字符的例程 `MBCS` 期望一个多字节字符字符串表示为 `unsigned` `char` 指针。  
  
> [!CAUTION]
>  多字节字符的每个字节用 8 位 `char`来表示。  然而，`SBCS`或`MBCS`的单字节字符的`char`类型的值大于 0x7F时，则该值为负值。  当这样的字符直接转换为 `int` 或 `long`时，通过编译器的结果是带符号扩展的，并且会产生意外的结果。  
  
 因此用8位表示多字节字符的字节`unsigned char`是最佳的。  或者，为了避免一个负数结果， 在转换为 `int` 或 `long`之前，将类型 `char` 的单字节字符转换为`unsigned char`。  
  
 由于某些`SBCS` 字符串处理函数采用（有符号的）`char*`参数，因此当定义`_MBCS`时，编译器会发出类型不匹配的警告。  有三种方法来避免此警告，可按效率的顺序列出：  
  
1.  在 TCHAR.H 中使用类型安全的内联函数。  这是默认行为。  
  
2.  通过在命令行上定义 `_MB_MAP_DIRECT`，在TCHAR.H中使用直接宏。  如果这样做，必须手动匹配类型。  这是最快的方法，但不是类型安全的方法。  
  
3.  在 TCHAR.H 中使用类型安全静态链接库函数。  为此，请在命令行上定义 `_NO_INLINING` 常量。  这是最慢的方法，但却是类型安全性最高的方法。  
  
## 请参阅  
 [国际化](../c-runtime-library/internationalization.md)   
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)