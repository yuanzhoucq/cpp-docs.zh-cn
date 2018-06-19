---
title: 自动并行化和自动向量化 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ec71583a-287b-4599-8767-1d255e080fe3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0b1ec19065647f78b4d9b2665003c0aa3a2795ba
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688461"
---
# <a name="auto-parallelization-and-auto-vectorization"></a>自动并行化和自动矢量化
自动并行化程序和自动向量化旨在为代码中的循环提供自动性能提升。  
  
## <a name="auto-parallelizer"></a>自动并行化程序  
 [/Qpar](../build/reference/qpar-auto-parallelizer.md)编译器开关可以启用*自动并行化*的代码中的循环。 当你指定此标志而未更改现有代码时，编译器将评估代码以查找可能受益于并行化的循环。 因为它可能会发现循环未做大量的工作，因此不会受益于并行化，而且因为每个不必要的并行化可能导致线程池、额外的同步的增强，或其他处理往往会降低而不是改进性能，因此编译器将保守地选择它进行并行化的循环。 例如，考虑下面的示例，它们的循环上限在编译时未知：  
  
```cpp  
void loop_test(int u) {  
   for (int i=0; i<u; ++i)  
      A[i] = B[i] * C[i];  
}  
```  
  
 因为`u`可能是较小的值，则编译器不会自动并行化此循环。 但是，您可能仍希望它并行化，因为您知道 `u` 将始终很大。 若要启用自动并行化，请指定[#pragma loop(hint_parallel(n))](../preprocessor/loop.md)，其中`n`是进行并行化的线程数。 在下面的示例中，编译器将尝试跨 8 个线程并行循环。  
  
```cpp  
void loop_test(int u) {  
#pragma loop(hint_parallel(8))  
   for (int i=0; i<u; ++i)  
      A[i] = B[i] * C[i];  
}  
```  
  
 正如所有[杂注指令](../preprocessor/pragma-directives-and-the-pragma-keyword.md)，替代杂注语法`__pragma(loop(hint_parallel(n)))`也支持。  
  
 有一些编译器无法并行化的循环，即使您希望并行化。 以下是一个示例：  
  
```cpp  
#pragma loop(hint_parallel(8))  
for (int i=0; i<upper_bound(); ++i)  
    A[i] = B[i] * C[i];  
```  
  
 每次调用该函数 `upper_bound()` 时，它可能会变化。 因为上限无法获知，编译器可以发出诊断消息解释为什么它无法并行化此循环。 下面的示例演示了可并行化的循环、无法并行化的循环，命令提示符下使用的编译器语法和每个命令行选项的编译器输出：  
  
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
  
 **cl d:\myproject\mylooptest.cpp /O2 /Qpar /Qpar-报表： 1**  
  
 生成此输出：  
  
 **---分析函数： void __cdecl test(void)**   
 **d:\myproject\mytest.cpp(4)： 循环并行化**  
  
 使用此命令编译：  
  
 **cl d:\myproject\mylooptest.cpp /O2 /Qpar /Qpar-报表： 2**  
  
 生成此输出：  
  
 **---分析函数： void __cdecl test(void)**   
 **d:\myproject\mytest.cpp(4)： 循环并行化**   
 **d:\myproject\mytest.cpp(4)： 循环未并行化由于原因"1008"**  
  
 请注意之间的两种不同的输出差异[/Qpar-report （自动并行化程序报告等级）](../build/reference/qpar-report-auto-parallelizer-reporting-level.md)选项。 **/Qpar-报表： 1**输出仅为成功进行并行化的循环并行化程序消息。 **/Qpar-报表： 2**输出这两个成功和不成功的循环并行化的并行化程序消息。  
  
 有关原因代码和消息的详细信息，请参阅[矢量化程序和并行化程序消息](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。  
  
## <a name="auto-vectorizer"></a>自动向量化  
 自动向量化分析代码中的循环，并使用矢量寄存器和目标计算机上的指令执行它们，如果它知道如何操作。 这可以提高代码的性能。 编译器面向 Intel 或 AMD 处理器中的 SSE2、 AVX 和 AVX2 指令或 ARM 处理器上的 NEON 指令根据[/arch](../build/reference/arch-minimum-cpu-architecture.md)切换。  
  
 指定自动向量化可能生成不同的指令 **/arch**切换。 这些说明由运行检查保护以确保代码仍然能够正常运行。 例如，编译 **/arch:SSE2**，可能会发出 SSE4.2 指令。 运行时间检查将验证 SSE4.2 可在目标处理器上使用，如果处理器不支持这些指令，将跳转到非 SSE4.2 版本的循环中。  
  
 默认情况下，自动向量化处于启用状态。 如果你想要比较的代码的性能，则可以使用[#pragma loop （no_vector)](../preprocessor/loop.md)禁用任何给定循环的向量化。  
  
```  
  
      #pragma loop(no_vector)  
for (int i = 0; i < 1000; ++i)  
   A[i] = B[i] + C[i];  
  
```  
  
 正如所有[杂注指令](../preprocessor/pragma-directives-and-the-pragma-keyword.md)，替代杂注语法`__pragma(loop(no_vector))`也支持。  
  
 作为使用自动并行化，可以指定[/Qvec-report （自动向量化报告等级）](../build/reference/qvec-report-auto-vectorizer-reporting-level.md)命令行选项用于报告已成功向量化循环仅-**/Qvec-报表： 1**— 或同时成功和未成功向量化循环-**/Qvec-报表： 2**)。  
  
 有关原因代码和消息的详细信息，请参阅[矢量化程序和并行化程序消息](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。  
  
 演示在实践中的向量化程序工作原理的示例，请参阅[项目 Austin 的第 2 部分 6： 翻页](http://blogs.msdn.com/b/vcblog/archive/2012/09/27/10348494.aspx)  
  
## <a name="see-also"></a>请参阅  
 [循环](../preprocessor/loop.md)   
 [本机代码中的并行编程](http://go.microsoft.com/fwlink/p/?linkid=263662)   
 [/Qpar （自动并行化）](../build/reference/qpar-auto-parallelizer.md)   
 [/Qpar-report （自动并行化程序报告等级）](../build/reference/qpar-report-auto-parallelizer-reporting-level.md)   
 [/Qvec-report （自动向量化报告等级）](../build/reference/qvec-report-auto-vectorizer-reporting-level.md)   
 [向量化和并行化消息](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)