---
title: "malloc 对齐 | Microsoft Docs"
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
ms.assetid: a8d1d1b4-5122-456f-9a64-a50e105e55a5
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# malloc 对齐
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[malloc](../c-runtime-library/reference/malloc.md) 保证返回这样一种内存，适于对齐存储具有基础对齐方式的任何对象并可以匹配于分配的存储数量。  *基本对齐方式*小于或等于由实现支持的无需对齐方式规范的最大对齐方式。（Visual C\+\+ 中，该对齐方式是 `double` 或 8 字节所需的对齐方式。  在面向 64 位平台的代码中，为 16 字节。）例如，一个四字节的分配在支持所有四字节或更小对象的边界上对齐。  
  
 Visual C\+\+ 允许具有“扩展对齐”的方式（也称为“过对齐”方式）。  例如，SSE 类型 [\_\_m128](../cpp/m128.md) 和 `__m256`，以及通过使用 `__declspec(align(``n``))`（其中 `n` 大于 8）声明的类型具有扩展对齐方式。  `malloc` 不保证适用于需要扩展对齐方式的对象的边界上的内存对齐。  若要为过对齐类型分配内存，请使用 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) 和相关函数。  
  
## 请参阅  
 [堆栈使用](../build/stack-usage.md)   
 [align](../cpp/align-cpp.md)   
 [\_\_declspec](../cpp/declspec.md)