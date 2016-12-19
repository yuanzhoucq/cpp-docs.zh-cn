---
title: "C++ 库约定 | Microsoft Docs"
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
  - "类 [C++]"
  - "编码约定, 标准 C++ 库"
  - "约定 [C++], 标准 C++ 库"
  - "函数名 [C++]"
  - "函数 [C++], 库命名约定"
  - "命名规则 [C++], C++ 库"
  - "命名规则 [C++], 标准 C++ 库"
  - "标准 C++ 库, 约定"
ms.assetid: bf41b79a-2d53-4f46-8d05-779358335146
caps.latest.revision: 9
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C++ 库约定
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 库遵循的约定和标准 C 库相同，并加上所述的几示。  
  
 实现有某 Latitude 该如何在 C\+\+ 库中所声明类型和函数：  
  
-   函数名称在标准 C 库中存在外部”\# " C\+\+ 或 extern“C”链接。  标准 C 包含相应的标头而不是声明库实体内联。  
  
-   在库类的成员函数名可能包含在文档中列出的那些类型的函数签名。  您可确定所述的函数调用的行为预期，但无法可靠接受库成员函数的地址。\(类型可能不是您所期望的。\)  
  
-   库类可能有未证明的 \(非虚拟基类。\)  为文档从另一个类派生的类可以从该类派生，事实上，通过其他未证明的类。  
  
-   整数类型为某些的同义词定义的类型可能与若干不同的整数类型之一。  
  
-   位屏蔽类型可实现为任何整数类型或枚举。  在任何情况下，还可执行按位运算 \(如 `AND` 和 `OR`\) 位于同一个位掩码类型的值。  位屏蔽类型的元素 `A` 和 `B` 是非零值。这样 `A` &`B` 为零。  
  
-   没有异常规范的库函数可以引发任何异常，因此，除非其定义明显限制这种可能性。  
  
 另一方面，有一些限制：  
  
-   标准 C 库不使用阴影的宏。  某些特定功能签名保留的，函数的名称不是。  
  
-   在类外的库函数名称不会具有不同类型，使用未证明，函数签名。  可以可靠采用其地址。  
  
-   而。其中的描述确定其，基类函数和成员所述相同的虚确定虚拟的。  
  
-   文档，除非显式，否则建议 C\+\+ 库定义的两种类型始终是不同的。  
  
-   库提供的函数，其中包括函数可替换的默认版本，可以 *最多* 引发在所有异常规范列出的这些异常。  库提供的析构函数不引发异常。  函数在标准 C 库中可以传播异常，那么，当调用 `qsort` 会引发异常的比较函数时，但在其他方面不引发异常。  
  
## 请参阅  
 [STL 概述](../standard-library/cpp-standard-library-overview.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)