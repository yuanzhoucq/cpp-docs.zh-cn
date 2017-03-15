---
title: "创建发行版本时遇到的常见问题 | Microsoft Docs"
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
  - "调试版本, 与发行版本的差异"
  - "调试内存分配器"
  - "调试 [MFC], 发行版本"
  - "堆布局问题"
  - "内存 [C++], 改写"
  - "MFC [C++], 发行版本"
  - "优化 [C++], 编译器"
  - "指针, 杂散"
  - "项目 [C++], 调试配置"
  - "发行版本, 生成应用程序"
  - "发行版本, 疑难解答"
  - "杂散指针"
  - "发行版本疑难解答"
  - "Visual C++ 疑难解答"
  - "意外的代码生成"
ms.assetid: 73cbc1f9-3e33-472d-9880-39a8e9977b95
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 创建发行版本时遇到的常见问题
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在开发期间，通常要生成项目的调试版本并用它进行测试。  如果那时生成应用程序的发布版本，则可能会发生访问冲突。  
  
 以下列表显示调试版本和发布（非调试）版本之间的主要差异。  还有其他差异，但以下是导致应用程序在调试版本中可以运行但在发布版本中失败的主要差异。  
  
-   [堆布局](#_core_heap_layout)  
  
-   [编译](#_core_compilation)  
  
-   [指针支持](#_core_pointer_support)  
  
-   [优化](#_core_optimizations)  
  
 有关如何在调试版本中捕捉发布版本错误的信息，请参见 [\/GZ（在调试版本中捕捉发布版本错误）](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md)编译器选项。  
  
##  <a name="_core_heap_layout"></a> 堆布局  
 在导致应用程序在调试时可运行，但在发布时不运行的问题中，约有百分之九十都是由堆布局引起的。  
  
 在生成用于调试的项目时，使用的是调试内存分配器。  这意味着所有内存分配的周围都有保护字节。  这些保护字节检测内存覆盖。  由于堆布局在发布版本和调试版本间不同，因此内存覆盖在调试版本中可能不会引起任何问题，但在发布版本中可能导致灾难性的后果。  
  
 有关更多信息，请参见[检查内存覆盖](../../build/reference/checking-for-memory-overwrites.md)和[使用调试版本来检查内存覆盖](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)。  
  
##  <a name="_core_compilation"></a> 编译  
 在生成发布版本时，许多 MFC 宏和 MFC 实现会更改。  具体说来，ASSERT 宏在发布版本中求得 nothing，因此将不执行 ASSERT 中的任何代码。  有关更多信息，请参见[检查 ASSERT 语句](../../build/reference/using-verify-instead-of-assert.md)。  
  
 在发布版本中，一些函数进行了内联以提高速度。  发布版本中的优化通常是打开的。  还使用了不同的内存分配器。  
  
##  <a name="_core_pointer_support"></a> 指针支持  
 缺少调试信息时，空白部分会被从应用程序中移除。  在发布版本中，游离的指针有更多机会指向未初始化的内存，而不是指向调试信息。  
  
##  <a name="_core_optimizations"></a> 优化  
 取决于某些代码段的特性，优化编译器可能会生成意外的代码。  这导致发布版本问题的可能性最低，但有时确实会发生。  有关解决方案，请参见[优化代码](../../build/reference/optimizing-your-code.md)。  
  
## 请参阅  
 [发行版本](../../build/reference/release-builds.md)   
 [修复发行版本问题](../../build/reference/fixing-release-build-problems.md)