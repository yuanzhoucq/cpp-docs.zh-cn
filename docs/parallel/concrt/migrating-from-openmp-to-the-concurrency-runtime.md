---
title: "从 OpenMP 迁移至并发运行时 | Microsoft Docs"
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
  - "并发运行时, 从 OpenMP 迁移"
  - "OpenMP, 迁移到并发运行时"
ms.assetid: 9bab7bb1-e45d-44b2-8509-3b226be2c93b
caps.latest.revision: 12
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 从 OpenMP 迁移至并发运行时
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

并发运行时启用各种编程模型。  这些模型可能会重叠或补充其他库的模型。  本节中的文档将 [OpenMP](../../parallel/openmp/openmp-in-visual-cpp.md) 与并发运行时进行比较，并提供有关如何迁移现有 OpenMP 代码以使用并发运行时的示例。  
  
 OpenMP 编程模型是由开放标准定义的，具有与 Fortran 和 C\/C\+\+ 编程语言的定义完善的绑定。  OpenMP 2.0 和 2.5 版（它们均受 Visual C\+\+ 编译器的支持）非常适合于迭代的并行算法，也就是说，它们可以对数据数组执行并行迭代。  除迭代任务以外，OpenMP 3.0 还支持非迭代任务。  
  
 当并行度是预先确定的并与系统上的可用资源相匹配时，OpenMP 效率最高。  OpenMP 模型特别适合于高性能计算，在高性能计算中，跨一台计算机的处理资源分布了大量计算问题。  在此情况下，硬件环境通常是固定的，并且开发人员在算法执行时预期可以获得对所有计算资源的独占访问权。  
  
 但是，较少受到约束的计算环境可能不适合使用 OpenMP。  例如，使用 OpenMP 2.0 和 2.5 更难实现递归问题（例如快速排序算法或搜索数据树）。  通过提供[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)和[并行模式库](../../parallel/concrt/parallel-patterns-library-ppl.md) \(PPL\)，并发运行时对 OpenMP 的功能进行了补充。  异步代理库支持粗粒度的任务并行度；PPL 支持更加细化的并行任务。  并发运行时可提供并行执行操作所需的基础结构，以使您可以关注应用程序逻辑。  但是，因为并发运行时可实现各种编程模型，所以其计划开销可能大于其他并发库（如 OpenMP）。  因此，如果您转换现有 OpenMP 代码以使用并发运行时，建议您以递增方式测试性能。  
  
## 何时从 OpenMP 迁移到并发运行时  
 在以下情况下，迁移现有 OpenMP 代码以使用并发运行时可能会有好处。  
  
|情况|并发运行时的优点|  
|--------|--------------|  
|您需要可扩展的并发编程框架。|可以扩展并发运行时中的许多功能。  您还可以组合现有功能来构成新功能。  由于 OpenMP 依赖于编译器指令，因此无法轻松扩展它。|  
|您的应用程序将受益于协作停滞。|当一项任务因为其需要尚不可用的资源而停滞时，并发运行时可在第一项任务等待资源时执行其他任务。|  
|您的应用程序将受益于动态负载平衡。|并发运行时使用按工作负载变化来调整计算资源分配的计划算法。  在 OpenMP 中，当计划程序向并行区域分配计算资源时，这些资源分配在整个计算过程中是固定的。|  
|您需要异常处理支持。|您可以通过 PPL 捕获并行区域或循环内外的异常。  在 OpenMP 中，您必须处理并行区域或循环内的异常。|  
|您需要一个取消机制。|PPL 使应用程序能够取消工作中的各个任务和并行树。  OpenMP 需要应用程序实现其自己的取消机制。|  
|您需要并行代码在其起始上下文以外的其他上下文中完成。|您可以通过并发运行时在一个上下文中启动一项任务，然后在另一个上下文中等待或取消此任务。  在 OpenMP 中，所有并行工作都必须在启动此工作的上下文中完成。|  
|您需要增强的调试支持。|Visual Studio 提供了**“并行堆栈”**和**“并行任务”**窗口，以使您可以更容易地调试多线程应用程序。<br /><br /> 有关并发运行时的调试支持的更多信息，请参见[使用“任务”窗口](../Topic/Using%20the%20Tasks%20Window.md)、[使用“并行堆栈”窗口](../Topic/Using%20the%20Parallel%20Stacks%20Window.md)和[演练：调试并行应用程序](../Topic/Walkthrough:%20Debugging%20a%20Parallel%20Application.md)。|  
  
## 何时不从 OpenMP 迁移到并发运行时  
 在以下情况下，可能不适合迁移现有 OpenMP 代码以使用并发运行时。  
  
|情况|说明|  
|--------|--------|  
|您的应用程序已经满足您的要求。|如果您对应用程序性能和当前的调试支持感到满意，则可能不适合进行迁移。|  
|您的并行循环主体很少工作。|并发运行时任务计划程序的开销可能无法与并行执行循环主体所带来的好处相比，特别是在循环主体相对较小的情况下。|  
|您的应用程序是用 C 语言编写的。|因为并发运行时使用了许多 C\+\+ 功能，所以当您无法编写使 C 应用程序能够充分使用的代码时，并发运行时可能并不合适。|  
  
## 相关主题  
 [如何：转换 OpenMP parallel for 循环以使用并发运行时](../../parallel/concrt/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime.md)  
 指定一个使用 OpenMP [parallel](../../parallel/openmp/reference/parallel.md) 和 [for](../../parallel/openmp/reference/for-openmp.md) 指令的基本循环，演示如何转换它以便使用并发运行时 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 算法。  
  
 [如何：转换使用取消的 OpenMP 循环以使用并发运行时](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)  
 指定一个无需运行所有迭代的 OpenMP [parallel](../../parallel/openmp/reference/parallel.md) [for](../../parallel/openmp/reference/for-openmp.md) 循环，演示如何转换它以便使用并发运行时取消机制。  
  
 [如何：转换使用异常处理的 OpenMP 循环以使用并发运行时](../../parallel/concrt/convert-an-openmp-loop-that uses-exception-handling.md)  
 指定一个执行异常处理的 OpenMP [parallel](../../parallel/openmp/reference/parallel.md) [for](../../parallel/openmp/reference/for-openmp.md) 循环，演示如何转换它以便使用并发运行时异常处理机制。  
  
 [如何：将使用缩减变量的 OpenMP 循环转换为使用并发运行时](../../parallel/concrt/convert-an-openmp-loop-that-uses-a-reduction-variable.md)  
 指定一个使用 [reduction](../../parallel/openmp/reference/reduction.md) 子句的 OpenMP [parallel](../../parallel/openmp/reference/parallel.md) [for](../../parallel/openmp/reference/for-openmp.md) 循环，演示如何转换它以便使用并发运行时。  
  
## 请参阅  
 [并发运行时](../../parallel/concrt/concurrency-runtime.md)   
 [OpenMP](../../parallel/openmp/openmp-in-visual-cpp.md)   
 [并行模式库 \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)