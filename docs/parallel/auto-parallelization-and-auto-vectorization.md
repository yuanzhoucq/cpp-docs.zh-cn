---
title: "自动并行化和自动矢量化 | Microsoft Docs"
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
ms.assetid: ec71583a-287b-4599-8767-1d255e080fe3
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 自动并行化和自动矢量化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

自动并行化程序和自动向量化旨在为代码中的循环提供自动性能提升。  
  
## 自动并行化程序  
 [\/Qpar](../build/reference/qpar-auto-parallelizer.md)编译器开关可以启用代码中循环的*自动并行化*。  当您指定此标志而未更改现有代码时，编译器将评估代码以查找可能受益于并行化的循环。  因为它可能会发现循环未做大量的工作，因此不会受益于并行化，而且因为每个不必要的并行化可能导致线程池、额外的同步的增强，或其他处理往往会降低而不是改进性能，因此编译器将保守地选择它进行并行化的循环。  例如，考虑下面的示例，它们的循环上限在编译时未知：  
  
```cpp  
  
void loop_test(int u) {  
   for (int i=0; i<u; ++i)  
      A[i] = B[i] * C[i];  
}  
```  
  
 因为`u`可能是较小的值，则编译器不会自动并行化此循环。  但是，您可能仍希望它并行化，因为您知道 `u` 将始终很大。  若要启用自动并行化，请指定[\#pragma loop\(hint\_parallel\(n\)\)](../preprocessor/loop.md)，其中`n`是进行并行化的线程数。  在下面的示例中，编译器将尝试跨 8 个线程并行循环。  
  
```cpp  
  
void loop_test(int u) {  
#pragma loop(hint_parallel(8))  
   for (int i=0; i<u; ++i)  
      A[i] = B[i] * C[i];  
}  
```  
  
 正如所有[杂注指令](../preprocessor/pragma-directives-and-the-pragma-keyword.md)一样，也支持替代杂注语法`__pragma(loop(hint_parallel(n)))`。  
  
 有一些编译器无法并行化的循环，即使您希望并行化。  以下是一个示例：  
  
```cpp  
  
#pragma loop(hint_parallel(8))  
for (int i=0; i<upper_bound(); ++i)  
    A[i] = B[i] * C[i];  
```  
  
 每次调用该函数 `upper_bound()` 时，它可能会变化。  因为上限无法获知，编译器可以发出诊断消息解释为什么它无法并行化此循环。  下面的示例演示了可并行化的循环、无法并行化的循环，命令提示符下使用的编译器语法和每个命令行选项的编译器输出：  
  
```cpp  
int A[1000];  
void test() {  
#pragma loop(hint_parallel(0))  
    for (int i=0; i<1000; ++i) {  
        A[i] = A[i] + 1;  
    }  
  
    for (int i=1000; i<2000; ++i) {  
        A[i] = A[i] + 1;  
    }  
}  
  
```  
  
 使用此命令编译：  
  
 **cl d:\\myproject\\mylooptest.cpp \/O2 \/Qpar \/Qpar\-report:1**  
  
 生成此输出：  
  
 **\-\-\- Analyzing function: void \_\_cdecl test\(void\)**   
  **d:\\myproject\\mytest.cpp\(4\) : loop parallelized**  
  
 使用此命令编译：  
  
 **cl d:\\myproject\\mylooptest.cpp \/O2 \/Qpar \/Qpar\-report:2**  
  
 生成此输出：  
  
 **\-\-\- Analyzing function: void \_\_cdecl test\(void\)**   
  **d:\\myproject\\mytest.cpp\(4\) : loop parallelized**   
  **d:\\myproject\\mytest.cpp\(4\) : loop not parallelized due to reason '1008'**  
  
 请注意两个不同 [\/Qpar\-report（自动并行化程序报告等级）](../build/reference/qpar-report-auto-parallelizer-reporting-level.md) 选项之间的输出差异。  **\/Qpar\-report:1** 仅为成功进行并行化的循环输出并行化程序消息。  **\/Qpar\-report:2** 为成功和不成功的循环并行化输出并行化程序消息。  
  
 有关原因代码和消息的详细信息，请参阅[矢量化程序和并行化程序消息](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。  
  
## 自动向量化  
 自动向量化分析代码中的循环，并使用矢量寄存器和目标计算机上的指令执行它们，如果它知道如何操作。  这可以提高代码的性能。  编译器面向 Intel 或 AMD 处理器的 SSE2、AVX 和 AVX2 指令或 ARM 处理器上的 NEON 指令，取决于 [\/arch](../build/reference/arch-minimum-cpu-architecture.md) 开关。  
  
 自动向量化可能生成由**\/arch**开关指定的不同指令。  这些说明由运行检查保护以确保代码仍然能够正常运行。  例如，在编译**\/arch:SSE2**时，可能会发出 SSE4.2 指令。  运行时间检查将验证 SSE4.2 可在目标处理器上使用，如果处理器不支持这些指令，将跳转到非 SSE4.2 版本的循环中。  
  
 默认情况下，自动向量化处于启用状态。  如果您要比较您的向量化的代码的性能，您可以使用 [\#pragma loop\(no\_vector\)](../preprocessor/loop.md) 禁用任何给定循环的向量化。  
  
```  
  
#pragma loop(no_vector)  
for (int i = 0; i < 1000; ++i)  
   A[i] = B[i] + C[i];  
  
```  
  
 正如所有[杂注指令](../preprocessor/pragma-directives-and-the-pragma-keyword.md)一样，也支持替代杂注语法`__pragma(loop(no_vector))`。  
  
 如果使用自动并行化程序，则可以指定 [\/Qvec\-report（自动矢量化程序报告等级）](../build/reference/qvec-report-auto-vectorizer-reporting-level.md) 命令行选项，以便仅报告成功进行向量化的循环 \(**\/Qvec\-report:1**\) 或报告成功和未成功进行向量化的循环 \(**\/Qvec\-report:2**\)。  
  
 有关原因代码和消息的详细信息，请参阅[矢量化程序和并行化程序消息](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。  
  
 有关演示如何在实践中运用向量化程序的示例，请参阅 [Project Austin 的第 2 部分（共 6 部分）：翻页](http://blogs.msdn.com/b/vcblog/archive/2012/09/27/10348494.aspx)  
  
## 请参阅  
 [循环](../preprocessor/loop.md)   
 [本机代码中的并行编程](http://go.microsoft.com/fwlink/?LinkId=263662)   
 [\/Qpar（自动并行化程序）](../build/reference/qpar-auto-parallelizer.md)   
 [\/Qpar\-report（自动并行化程序报告等级）](../build/reference/qpar-report-auto-parallelizer-reporting-level.md)   
 [\/Qvec\-report（自动矢量化程序报告等级）](../build/reference/qvec-report-auto-vectorizer-reporting-level.md)   
 [矢量化程序和并行化程序消息](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)