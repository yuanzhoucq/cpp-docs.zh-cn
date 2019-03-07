---
title: 从 OpenMP 迁移至并发运行时
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, migrating from OpenMP
- OpenMP, migrating to the Concurrency Runtime
ms.assetid: 9bab7bb1-e45d-44b2-8509-3b226be2c93b
ms.openlocfilehash: 16b0f175867e18e127997749098cce998674b3d2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259498"
---
# <a name="migrating-from-openmp-to-the-concurrency-runtime"></a>从 OpenMP 迁移至并发运行时

并发运行时支持各种编程模型。 这些模型可能会与其他库的模型重叠或对其进行补充。 在此文档部分比较[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)到并发运行时并提供了有关如何迁移现有 OpenMP 代码以使用并发运行时的示例。

OpenMP 编程模型由开放标准定义，具有与 Fortran 和 C/C++ 编程语言定义完善的绑定。 OpenMP 2.0 版和 2.5 中，支持的 Visual c + + 编译器，非常适合并行算法的迭代。也就是说，它们的数据数组上执行并行迭代。 OpenMP 3.0 支持非迭代任务和迭代的任务。

当预设了并行度，并匹配了系统上的可用资源时，OpenMP 的效率最高。 OpenMP 模型是特别适合于高性能计算，其中将大量运算问题分布在一台计算机的处理资源。 在此方案中，硬件环境通常固定的开发人员可以合理期望执行该算法时具有对所有计算资源的独占访问权限。

但是，不受限制的计算环境可能适合于 OpenMP。 例如，递归问题 （如快速排序算法或搜索数据树） 会更加困难，通过使用 OpenMP 2.0 和 2.5 来实现。 并发运行时是 OpenMP 的功能的补充，从而[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)并[并行模式库](../../parallel/concrt/parallel-patterns-library-ppl.md)(PPL)。 异步代理库支持粗粒度的任务并行度;PPL 支持更多细粒度的并行任务。 并发运行时提供的基础结构的需要来并行执行操作，以便你可以专注于你的应用程序的逻辑。 但是，因为并发运行时支持的各种编程模型，其计划开销可能会超出 OpenMP 等其他并发库。 因此，我们建议在转换现有 OpenMP 代码以使用并发运行时以增量方式测试性能。

## <a name="when-to-migrate-from-openmp-to-the-concurrency-runtime"></a>何时从 OpenMP 迁移至并发运行时

它可能更有利，若要迁移现有 OpenMP 代码以在以下情况下使用并发运行时。

|Cases|并发运行时的优点|
|-----------|-------------------------------------------|
|需要一种可扩展并发编程框架。|并发运行时中的许多功能均可扩展。 还可以结合现有功能来构造新功能。 由于 OpenMP 依赖于编译器指令，它不能轻松地扩展。|
|你的应用程序将受益于协作停滞。|当任务块中，因为它需要尚不可用的资源时，并发运行时可以执行其他任务，第一个任务等待资源时。|
|你的应用程序将受益于动态负载平衡。|并发运行时使用调整工作负载更改计算资源的分配计划算法。 在 OpenMP，当计划程序分配到并行区域的计算资源时这些资源分配被固定整个计算。|
|所需的异常处理支持。|PPL 可以捕获异常，内部和外部并行区域或循环。 在 OpenMP，必须处理并行区域或循环内的异常。|
|需要取消机制。|PPL 使应用程序可以取消单个任务和并行工作树。 OpenMP 要求应用程序以实现其自身取消的机制。|
|需要从其启动不同的上下文中完成的并行代码。|并发运行时，可以启动任务在一个上下文中，然后等待或取消该任务在另一个上下文中。 在 OpenMP 中，必须从其开始的上下文中完成所有的并行工作。|
|需要增强的调试支持。|Visual Studio 提供了**并行堆栈**并**并行任务**windows，以便可以更轻松地调试多线程应用程序。<br /><br /> 有关调试的并发运行时支持的详细信息，请参阅[使用任务窗口](/visualstudio/debugger/using-the-tasks-window)，[使用并行堆栈窗口](/visualstudio/debugger/using-the-parallel-stacks-window)，和[演练：调试并行应用程序](/visualstudio/debugger/walkthrough-debugging-a-parallel-application)。|

## <a name="when-not-to-migrate-from-openmp-to-the-concurrency-runtime"></a>何时不从 OpenMP 迁移到并发运行时

在以下情况下描述时它可能不适合迁移现有 OpenMP 代码以使用并发运行时。

|Cases|说明|
|-----------|-----------------|
|应用程序已满足您的要求。|如果应用程序性能和当前的调试支持感到满意，可能不适合迁移。|
|并行循环主体执行一些工作。|并发运行时任务计划程序的开销可能会不克服的循环主体并行执行的尤其是当循环主体是相对较小的好处。|
|用 c 语言编写应用程序|并发运行时使用多个 c + + 功能，因为它可能不适合时不能编写代码，使 C 应用程序能够充分利用它。|

## <a name="related-topics"></a>相关主题

[如何：转换 OpenMP parallel for 循环以使用并发运行时](../../parallel/concrt/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime.md)

提供一个基本循环使用 OpenMP[并行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)并[有关](../../parallel/openmp/reference/for-openmp.md)指令，演示如何将其转换为使用并发运行时[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法。

[如何：转换使用取消的 OpenMP 循环以使用并发运行时](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)<br/>
给定 OpenMP[并行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[为](../../parallel/openmp/reference/for-openmp.md)循环不需要所有迭代来运行，演示如何将其转换为使用并发运行时取消机制。

[如何：转换使用异常处理的 OpenMP 循环以使用并发运行时](../../parallel/concrt/convert-an-openmp-loop-that-uses-exception-handling.md)<br/>
给定 OpenMP[并行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[为](../../parallel/openmp/reference/for-openmp.md)循环执行异常处理，演示如何将其转换为使用并发运行时异常处理机制。

[如何：将使用缩减变量的 OpenMP 循环转换为使用并发运行时](../../parallel/concrt/convert-an-openmp-loop-that-uses-a-reduction-variable.md)<br/>
给定 OpenMP[并行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[有关](../../parallel/openmp/reference/for-openmp.md)使用循环[减少](../../parallel/openmp/reference/reduction.md)子句，演示如何将其转换为使用并发运行时。

## <a name="see-also"></a>请参阅

[并发运行时](../../parallel/concrt/concurrency-runtime.md)<br/>
[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)<br/>
[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)
