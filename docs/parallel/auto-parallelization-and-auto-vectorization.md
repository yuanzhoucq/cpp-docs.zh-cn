---
title: 自动并行化和自动矢量化
ms.date: 11/04/2016
ms.assetid: ec71583a-287b-4599-8767-1d255e080fe3
ms.openlocfilehash: adc0dd9346cc2850b02e01804e26044c367f2d14
ms.sourcegitcommit: fcc3aeb271449f8be80348740cffef39ba543407
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2020
ms.locfileid: "82538614"
---
# <a name="auto-parallelization-and-auto-vectorization"></a>自动并行化和自动矢量化

自动并行化程序和自动向量化旨在为代码中的循环提供自动性能提升。

## <a name="auto-parallelizer"></a>自动并行化程序

[/Qpar](../build/reference/qpar-auto-parallelizer.md)编译器开关在代码中启用循环的*自动并行*化。 当您指定此标志而未更改现有代码时，编译器将评估代码以查找可能受益于并行化的循环。 因为它可能会发现循环未做大量的工作，因此不会受益于并行化，而且因为每个不必要的并行化可能导致线程池、额外的同步的增强，或其他处理往往会降低而不是改进性能，因此编译器将保守地选择它进行并行化的循环。 例如，考虑下面的示例，它们的循环上限在编译时未知：

```cpp
void loop_test(int u) {
   for (int i=0; i<u; ++i)
      A[i] = B[i] * C[i];
}
```

因为`u`可能是较小的值，则编译器不会自动并行化此循环。 但是，您可能仍希望它并行化，因为您知道 `u` 将始终很大。 若要启用自动并行化，请指定[#pragma loop （hint_parallel （n））](../preprocessor/loop.md)， `n`其中是要在其上进行并行化的线程数。 在下面的示例中，编译器将尝试跨 8 个线程并行循环。

```cpp
void loop_test(int u) {
#pragma loop(hint_parallel(8))
   for (int i=0; i<u; ++i)
      A[i] = B[i] * C[i];
}
```

与所有[杂注指令](../preprocessor/pragma-directives-and-the-pragma-keyword.md)一样，还支持备用`__pragma(loop(hint_parallel(n)))`杂注语法。

有一些编译器无法并行化的循环，即使您希望并行化。 下面是一个示例：

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

`cl d:\myproject\mylooptest.cpp /O2 /Qpar /Qpar-report:1`

生成此输出：

```Output
--- Analyzing function: void __cdecl test(void)
d:\myproject\mytest.cpp(4) : loop parallelized
```

使用此命令编译：

`cl d:\myproject\mylooptest.cpp /O2 /Qpar /Qpar-report:2`

生成此输出：

```Output
--- Analyzing function: void __cdecl test(void)
d:\myproject\mytest.cpp(4) : loop parallelized
d:\myproject\mytest.cpp(4) : loop not parallelized due to reason '1008'
```

请注意两个不同[/Qpar-report （自动并行报告级别）](../build/reference/qpar-report-auto-parallelizer-reporting-level.md)选项之间的输出差别。 `/Qpar-report:1` 仅为成功进行并行化的循环输出并行化程序消息。 `/Qpar-report:2` 为成功和不成功的循环并行化输出并行化程序消息。

有关原因代码和消息的详细信息，请参阅[向量化和并行消息](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。

## <a name="auto-vectorizer"></a>自动向量化

自动向量化分析代码中的循环，并使用矢量寄存器和目标计算机上的指令执行它们，如果它知道如何操作。 这可以提高代码的性能。 此编译器根据[/arch](../build/reference/arch-minimum-cpu-architecture.md)开关，根据 INTEL 或 AMD 处理器中的 SSE2、AVX 和 AVX2 说明，或 ARM 处理器上的霓虹灯说明。

自动向量化可能生成由`/arch`开关指定的不同指令。 这些说明由运行检查保护以确保代码仍然能够正常运行。 例如，在编译`/arch:SSE2`时，可能会发出 SSE4.2 指令。 运行时间检查将验证 SSE4.2 可在目标处理器上使用，如果处理器不支持这些指令，将跳转到非 SSE4.2 版本的循环中。

默认情况下，自动向量化处于启用状态。 如果要比较矢量化下的代码的性能，可以使用[#pragma 循环（no_vector）](../preprocessor/loop.md)来禁用任何给定循环的矢量化。

```cpp
#pragma loop(no_vector)
for (int i = 0; i < 1000; ++i)
   A[i] = B[i] + C[i];
```

与所有[杂注指令](../preprocessor/pragma-directives-and-the-pragma-keyword.md)一样，还支持备用`__pragma(loop(no_vector))`杂注语法。

与自动并行一样，你可以指定[/Qvec-report （自动向量化报告级别）](../build/reference/qvec-report-auto-vectorizer-reporting-level.md)命令行选项，以仅`/Qvec-report:1`报告成功的向量化循环，或者成功和未成功的向量化循环`/Qvec-report:2`）。

有关原因代码和消息的详细信息，请参阅[向量化和并行消息](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。

有关演示向量化的工作原理的示例，请参阅[Project 德克萨斯第2部分（共6部分）： Page 运行](https://devblogs.microsoft.com/cppblog/project-austin-part-2-of-6-page-curling/)

## <a name="see-also"></a>请参阅

[圈](../preprocessor/loop.md)<br/>
[本机代码中的并行编程](/archive/blogs/nativeconcurrency)<br/>
[/Qpar（自动并行化程序）](../build/reference/qpar-auto-parallelizer.md)<br/>
[/Qpar-report（自动并行化程序报告等级）](../build/reference/qpar-report-auto-parallelizer-reporting-level.md)<br/>
[/Qvec-report （自动向量化报告级别）](../build/reference/qvec-report-auto-vectorizer-reporting-level.md)<br/>
[向量化和并行消息](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)
