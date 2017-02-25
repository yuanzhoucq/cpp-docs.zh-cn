---
title: "具有文件范围的名称中的链接 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "声明 [C++], 外部"
  - "外部链接, 范围链接规则"
  - "文件范围 [C++]"
  - "链接 [C++], 范围链接规则"
  - "名称 [C++], 范围链接规则"
  - "范围 [C++], 链接规则"
  - "静态修饰符, 文件范围"
  - "静态名称和文件范围"
  - "静态变量, 外部声明"
ms.assetid: 38d3fa5e-1861-466e-a590-84b86f7b184e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 具有文件范围的名称中的链接
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

以下链接规则适用于带文件范围的名称（`typedef` 和枚举器名称除外）：  
  
-   如果将名称显式声明为“静态”，则它具有内部链接并标识其自己的翻译单元中的程序元素。  
  
-   枚举器名称和 `typedef` 名称没有链接。  
  
-   带文件范围的所有其他名称都具有外部链接。  
  
 **Microsoft 专用**  
  
-   如果带文件范围的函数名称被显式声明为“内联”，则在将其实例化或引用其地址时，它会具有外部链接。  因此，带文件范围的函数可以拥有内部链接或外部链接。  
  
 **结束 Microsoft 专用**  
  
 在以下情况下，类具有内部链接：  
  
-   不使用 C\+\+ 功能（例如，成员访问控制、成员函数、构造函数、析构函数等）。  
  
-   未用于具有外部链接的另一个名称的声明中。  此约束意味着，传递到带外部链接的函数的类类型对象会导致该类具有外部链接。  
  
## 请参阅  
 [程序和链接](../cpp/program-and-linkage-cpp.md)