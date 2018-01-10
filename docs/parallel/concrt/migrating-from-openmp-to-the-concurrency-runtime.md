---
title: "从 OpenMP 迁移至并发运行时 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Concurrency Runtime, migrating from OpenMP
- OpenMP, migrating to the Concurrency Runtime
ms.assetid: 9bab7bb1-e45d-44b2-8509-3b226be2c93b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 65359e76e036a0d8d33de2de9f6c96c6425d2152
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="migrating-from-openmp-to-the-concurrency-runtime"></a>从 OpenMP 迁移至并发运行时
并发运行时支持各种编程模型。 这些模型可能会与其他库的模型重叠或对其进行补充。 在此文档部分比较[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)的并发运行，并提供有关如何迁移现有 OpenMP 代码以使用并发运行时的示例。  
  
 OpenMP 编程模型由开放标准定义，具有与 Fortran 和 C/C++ 编程语言定义完善的绑定。 OpenMP 版本 2.0 和 2.5，Visual c + + 编译器支持，非常适合并行算法，迭代。也就是说，它们对数据的数组执行并行迭代。 OpenMP 3.0 支持非迭代任务和迭代的任务。  
  
 当预设了并行度，并匹配了系统上的可用资源时，OpenMP 的效率最高。 OpenMP 模型是特别适合于高性能计算，其中将非常大的计算问题分布在一台计算机的处理资源。 在此方案中，硬件环境通常固定的开发人员可以合理地期望执行算法时具有对所有计算资源的独占访问权限。  
  
 但是，更少受约束的计算环境可能不适合于 OpenMP。 例如，递归问题 （如快速排序算法或搜索数据的树） 会更加困难，以通过 OpenMP 2.0 和 2.5 来实现。 并发运行时进行了补充 OpenMP 的功能，可通过提供[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)和[并行模式库](../../parallel/concrt/parallel-patterns-library-ppl.md)(PPL)。 异步代理库支持粗粒度的任务并行;PPL 支持更多细粒度的并行任务。 并发运行时提供的基础结构所需并行执行操作，以便你可以专注于你的应用程序的逻辑。 但是，由于并发运行时可用于各种编程模型，其计划开销可能大于 OpenMP 等其他并发库。 因此，我们建议在转换现有 OpenMP 代码以使用并发运行时以增量方式测试性能。  
  
## <a name="when-to-migrate-from-openmp-to-the-concurrency-runtime"></a>何时将从 OpenMP 迁移至并发运行时  
 它可能会迁移现有 OpenMP 代码以使用并发运行时在以下情况下更有利。  
  
|Cases|并发运行时的优点|  
|-----------|-------------------------------------------|  
|你需要一种可扩展并发编程框架。|并发运行时中的许多功能均可扩展。 还可以结合现有功能来构造新功能。 OpenMP 依赖于编译器指令，因为它不能轻松扩展。|  
|你的应用程序将受益于协作停滞。|在任务块中，因为它需要的资源的尚不可用，并发运行时可在第一个任务等待资源时执行其他任务。|  
|你的应用程序会带来好处动态负载平衡。|并发运行时使用调整工作负荷更改计算资源的分配计划算法。 在 OpenMP 中，当计划程序分配到并行区域的计算资源时那些资源分配被固定整个计算。|  
|你需要异常处理支持。|PPL 中，可以捕获异常，同时内部和外部并行区域或循环。 在 OpenMP 中，你必须处理的并行区域或循环内的异常。|  
|你需要取消机制。|PPL 使应用程序能够取消各个任务和并行工作树。 OpenMP 要求应用程序实现其自己的取消机制。|  
|你需要并行代码，以完成在不同的上下文从其启动。|并发运行时，可以在一个上下文中，启动任务，然后等待或取消该任务在另一个上下文。 在 OpenMP 中，所有并行工作必须从其开始的上下文中完成。|  
|你需要增强的调试支持。|Visual Studio 提供**并行堆栈**和**并行任务**windows，以便你能够更轻松地调试多线程应用程序。<br /><br /> 有关调试支持并发运行时的详细信息，请参阅[使用任务窗口](/visualstudio/debugger/using-the-tasks-window)，[使用并行堆栈窗口](/visualstudio/debugger/using-the-parallel-stacks-window)，和[演练： 调试并行应用程序](/visualstudio/debugger/walkthrough-debugging-a-parallel-application)。|  
  
## <a name="when-not-to-migrate-from-openmp-to-the-concurrency-runtime"></a>何时不将从 OpenMP 迁移至并发运行时  
 以下情况下描述时它可能不适合迁移现有 OpenMP 代码以使用并发运行时。  
  
|Cases|说明|  
|-----------|-----------------|  
|应用程序已满足你的要求。|如果您感到满意应用程序性能和当前的调试支持，可能不适合迁移。|  
|并行循环正文执行一些工作。|不能并发运行时任务计划程序的开销可能会抵消并行，执行循环体，尤其是当循环体是相对较小的好处。|  
|你的应用程序是用 C 语言编写|并发运行时使用许多 c + + 功能，因为它可能不适合时无法编写代码来启用 C 应用程序以充分利用它。|  
  
## <a name="related-topics"></a>相关主题  
 [如何：转换 OpenMP 并行 for 循环以使用并发运行时](../../parallel/concrt/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime.md)  

 提供一个基本循环使用 OpenMP[并行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)和[为](../../parallel/openmp/reference/for-openmp.md)指令，演示如何将其转换为使用并发运行时[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法。  

  
 [如何：转换使用取消的 OpenMP 循环以使用并发运行时](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)  
 给定 OpenMP[并行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[为](../../parallel/openmp/reference/for-openmp.md)循环，不需要所有迭代，若要运行，演示如何将其转换为使用并发运行时取消机制。  
  
 [如何：转换使用异常处理的 OpenMP 循环以使用并发运行时](../../parallel/concrt/convert-an-openmp-loop-that uses-exception-handling.md)  
 给定 OpenMP[并行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[为](../../parallel/openmp/reference/for-openmp.md)循环执行异常处理，演示如何将其转换为使用并发运行时异常处理机制。  
  
 [如何：转换使用缩减变量的 OpenMP 循环以使用并发运行时](../../parallel/concrt/convert-an-openmp-loop-that-uses-a-reduction-variable.md)  
 给定 OpenMP[并行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[为](../../parallel/openmp/reference/for-openmp.md)使用循环[缩减](../../parallel/openmp/reference/reduction.md)子句，演示如何将其转换为使用并发运行时。  
  
## <a name="see-also"></a>请参阅  
 [并发运行时](../../parallel/concrt/concurrency-runtime.md)   
 [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)   
 [并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)

