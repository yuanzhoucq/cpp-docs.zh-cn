---
title: "RUNTIME_FUNCTION 结构 | Microsoft Docs"
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
ms.assetid: 84386527-d3aa-41c5-871d-78e3e1913704
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# RUNTIME_FUNCTION 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

基于表的异常处理需要一个面向分配堆栈空间或调用其他函数的所有函数（例如，非叶函数）的表项。  函数表项的格式为：  
  
|||  
|-|-|  
|ULONG|函数起始地址|  
|ULONG|函数结束地址|  
|ULONG|展开信息地址|  
  
 RUNTIME\_FUNCTION 结构在内存中必须为 DWORD 对齐。  所有地址都与映像相关，即相对于包含函数表项的映像起始地址有 32 位的偏移量。  这些项已经过排序，放置在 PE32\+ 映像的 .pdata 节中。  对于动态生成的函数 \[JIT 编译器\]，要支持这些函数的运行时必须使用 RtlInstallFunctionTableCallback 或 RtlAddFunctionTable，以便向操作系统提供此信息。  如果不能满足此要求，则会导致不可靠的异常处理和进程调试。  
  
## 请参阅  
 [为异常处理和调试器支持展开数据](../build/unwind-data-for-exception-handling-debugger-support.md)