---
title: "混合 C（结构化）和 C++ 异常 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 异常处理, 混合语言"
  - "catch 关键字 [C++], 混合的"
  - "异常, 混合 C 和 C++"
  - "结构化异常处理, 混合 C 和 C++"
  - "try-catch 关键字 [C++], 混合语言"
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 混合 C（结构化）和 C++ 异常
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要编写可移植性更高的代码，建议不要在 C\+\+ 程序中使用结构化异常处理。  但是，您有时可能希望使用 **\/EHa** 进行编译并将结构化异常和 C\+\+ 源代码组合在一起，并且需要用于处理这两种异常的某个设备。  由于结构化异常处理程序没有对象或类型化异常的概念，因此它无法处理 C\+\+ 代码引发的异常；但是，C\+\+ **catch** 处理程序可以处理结构化异常。  因此，C 编译器不接受 C\+\+ 异常处理语法（**TRY**、`throw`、**catch**），但 C\+\+ 编译器支持结构化异常处理语法（`__try`、`__except`、`__finally`）。  
  
 有关将结构化异常作为 C\+\+ 异常处理的信息，请参阅 [\_set\_se\_translator](../c-runtime-library/reference/set-se-translator.md)。  
  
 如果将结构化异常和 C\+\+ 异常混合，请注意以下几点：  
  
1.  不能在同一函数中混合 C\+\+ 异常和结构化异常。  
  
2.  始终执行终止处理程序（`__finally` 块），甚至在引发异常后的展开过程中也是如此。  
  
3.  C\+\+ 异常处理可以捕获并保留使用 [\/EH](../build/reference/eh-exception-handling-model.md) 编译器选项（此选项启用展开语义）编译的所有模块中的展开语义。  
  
4.  可以存在一些不为所有对象调用析构函数的情况。  例如，如果在尝试通过未初始化的函数指针进行函数调用时发生结构化异常，并且该函数将调用前构造的对象用作参数，则在堆栈展开过程中将不会调用这些对象的析构函数。  
  
## 您想进一步了解什么？  
  
-   [在 C\+\+ 程序中使用 setjmp 或 longjmp](../cpp/using-setjmp-longjmp.md)  
  
-   [SEH 和 C\+\+ EH 之间的差异](../cpp/exception-handling-differences.md)  
  
## 请参阅  
 [C\+\+ 异常处理](../cpp/cpp-exception-handling.md)