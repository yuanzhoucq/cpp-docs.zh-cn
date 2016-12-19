---
title: "优化代码 | Microsoft Docs"
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
  - "cl.exe 编译器, 性能"
  - "代码, 优化"
  - "优化"
  - "优化, C++ 代码"
  - "性能, 编译器"
  - "性能, 优化代码"
ms.assetid: 4f33e6c7-9870-43b3-9c2f-d7e44f764971
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 优化代码
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通过优化可执行文件，可在较快执行速度和较小代码大小之间实现平衡。  本主题讨论了 Visual C\+\+ 提供的可帮助您优化代码的一些机制。  
  
## 语言功能  
 下面的主题介绍了 C\/C\+\+ 语言中的一些优化功能。  
  
 [优化杂注和关键字](../../build/reference/optimization-pragmas-and-keywords.md)  
 可在代码中使用以提高性能的关键字和杂注的列表。  
  
 [按类别列出的编译器选项](../../build/reference/compiler-options-listed-by-category.md)  
 专门影响执行速度或代码大小的 **\/O** 编译器选项的列表。  
  
 [规则引用声明符：&&](../../cpp/rvalue-reference-declarator-amp-amp.md)  
 Rvalue 引用支持移动语义的实现。  如果移动语义用于实现模板库，则使用这些模板的应用程序的性能可显著提高。  
  
### 优化杂注  
 如果经过优化的某个代码节导致错误或速度减慢，则可以使用 [optimize](../../preprocessor/optimize.md) 杂注对该代码节关闭优化。  
  
 用两个杂注将代码括起来，如下所示：  
  
```  
#pragma optimize("", off)  
// some code here   
#pragma optimize("", on)  
```  
  
## 编程惯例  
 在用优化的方式编译代码时，您可能会注意到一些附加的警告消息。  此行为是预期行为，因为一些警告仅与优化的代码有关。  如果您注意到这些警告，则可以避免许多优化问题。  
  
 矛盾的是，为了速度而对程序进行优化可能会导致代码运行速度减慢。  这是因为一些为了速度而进行的优化会增加代码大小。  例如，内联函数可消除函数调用的开销。  但是内联太多代码可能会使程序很大，致使虚拟内存页的错误数增加。  因此，通过消除函数调用获得的速度可能会丢失在内存交调中。  
  
 下面的主题讨论了良好的编程做法。  
  
 [提高时间关键代码的技巧](../../build/reference/tips-for-improving-time-critical-code.md)  
 更好的编码技术可产生更好的性能。  本主题建议了一些可帮助您确保时间关键代码部分的执行令人满意的编码技术。  
  
 [优化最佳做法](../../build/reference/optimization-best-practices.md)  
 提供了有关如何以最佳方式优化应用程序的一般准则。  
  
## 调试优化的代码  
 由于优化可能会更改编译器创建的代码，因此建议您调试应用程序并测量其性能，随后优化代码。  
  
 下面的主题提供有关如何进行调试的基本信息。  
  
-   [使用 Visual Studio 进行调试](../Topic/Debugging%20in%20Visual%20Studio.md)  
  
-   [创建发行版本时遇到的常见问题](../../build/reference/common-problems-when-creating-a-release-build.md)  
  
 下面的主题提供有关如何进行调试的更高级信息。  
  
-   [如何：调试优化的代码](../Topic/How%20to:%20Debug%20Optimized%20Code.md)  
  
-   [为何浮点数可能丢失精度](../../build/reference/why-floating-point-numbers-may-lose-precision.md)  
  
 以下各个主题提供有关如何优化生成、加载和执行代码的信息。  
  
-   [提高编译器吞吐量](../../build/reference/improving-compiler-throughput.md)  
  
-   [使用没有 \(\) 的函数名不产生代码](../../build/reference/using-function-name-without-parens-produces-no-code.md)  
  
-   [优化内联程序集](../../assembler/inline/optimizing-inline-assembly.md)  
  
-   [为 ATL 项目指定编译器优化](../../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)  
  
-   [加载时应使用哪些优化技术来提高客户端应用程序的性能？](../../build/what-optimization-techniques-should-i-use.md)  
  
-   [!INCLUDE[crabout](../../build/reference/includes/crabout_md.md)]如何缩短 DLL 方法加载时间的更多信息，请参见 [MSDN 库](http://go.microsoft.com/fwlink/?linkid=556)网站上的“MSDN 杂志”中“Under the Hood”（深入实质）专栏下的“Optimizing DLL Load Time Performance”（优化 DLL 加载时间性能）。  
  
-   [!INCLUDE[crabout](../../build/reference/includes/crabout_md.md)]如何在应用程序中最大程度减少分页的更多信息，请参见 [MSDN 库](http://go.microsoft.com/fwlink/?linkid=556) 网站上的“MSDN 杂志”中“Bugslayer”专栏下的“Improving Runtime Performance with the Smooth Working Set Tool”（使用 Smooth 工作集工具提高运行时性能）和“Improving Runtime Performance with the Smooth Working Set Tool—Part 2”（使用 Smooth 工作集工具提高运行时性能（第 2 部分））。  
  
## 请参阅  
 [C\/C\+\+ 生成参考](../../build/reference/c-cpp-building-reference.md)