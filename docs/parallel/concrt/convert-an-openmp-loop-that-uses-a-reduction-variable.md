---
title: "如何：将使用缩减变量的 OpenMP 循环转换为使用并发运行时 | Microsoft Docs"
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
  - "从 OpenMP 转换为并发运行时, 缩减变量"
  - "缩减变量, 从 OpenMP 转换为并发运行时"
ms.assetid: 96623f36-5e57-4d3f-8c13-669e6cd535b1
caps.latest.revision: 13
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：将使用缩减变量的 OpenMP 循环转换为使用并发运行时
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本示例演示如何转换使用 [reduction](../../parallel/openmp/reference/reduction.md) 子句的 OpenMP [parallel](../../parallel/openmp/reference/parallel.md) [for](../../parallel/openmp/reference/for-openmp.md) 循环，以便使用并发运行时。  
  
 您可以使用 OpenMP `reduction` 子句指定一个或多个与并行区域末端的缩减操作相关的线程专用变量。  OpenMP 预定义了一组缩减运算符。  每个缩减变量都必须是一个标量（例如，`int`、`long` 和 `float`）。  OpenMP 还定义了若干有关如何在并行区域中使用缩减变量的限制。  
  
 并行模式库 \(PPL\) 提供了 [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) 类，该类提供可重用的、线程本地存储，以允许您执行精细计算，然后再将这些计算合并为一个最终结果。  `combinable` 类是用于标量和复杂类型的模板。  若要使用 `combinable` 类，请在并行构造主体中执行子计算，然后调用 [concurrency::combinable::combine](../Topic/combinable::combine%20Method.md) 或 [concurrency::combinable::combine\_each](../Topic/combinable::combine_each%20Method.md) 方法以生成最终结果。  `combine` 和 `combine_each` 方法均会采用可指定每个元素对的组合方式的*组合函数*。  因此，`combinable` 类不仅限于一组固定的缩减运算符。  
  
## 示例  
 此示例使用 OpenMP 和并发运行时计算前 35 个 Fibonacci 数的总和。  
  
 [!code-cpp[concrt-openmp#7](../../parallel/concrt/codesnippet/CPP/convert-an-openmp-loop-that-uses-a-reduction-variable_1.cpp)]  
  
 该示例产生下面的输出。  
  
  **使用OpenMP…**  
**前 35 个 Fibonacci 数的总和为 14930351。**  
**使用并发运行时...**  
**前 35 个 Fibonacci 数的总和为 14930351。** 有关 `combinable` 类的更多信息，请参见[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## 编译代码  
 复制该代码示例，并将其粘贴到Visual Studio项目中或名为`concrt-omp-fibonacci-reduction.cpp` 的文件中，然后在Visual Studio命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc \/openmp concrt\-omp\-fibonacci\-reduction.cpp**  
  
## 请参阅  
 [从 OpenMP 迁移至并发运行时](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)