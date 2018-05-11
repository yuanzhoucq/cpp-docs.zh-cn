---
title: 如何： 使用 combinable 提高性能 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- combinable class, example
- improving parallel performance with combinable [Concurrency Runtime]
ms.assetid: fa730580-1c94-4b2d-8aec-57c91dc0497e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3185ee9f7546e6927197d2e3452ea4cf86f9ab5c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-use-combinable-to-improve-performance"></a>如何：使用 combinable 提高性能
此示例演示如何使用[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)类来计算中的数字的和[std:: array](../../standard-library/array-class-stl.md)质数的对象。 `combinable`类消除共享的状态，从而提高了性能。  
  
> [!TIP]
>  在某些情况下，并行映射 ([concurrency:: parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform))，并减少 ([并发:: parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce)) 可以通过提供的性能改进`combinable`。 示例使用映射和化简操作即可生成此示例与相同的结果，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。  
  
## <a name="example"></a>示例  
 下面的示例使用[std:: accumulate](../../standard-library/numeric-functions.md#accumulate)函数来计算质数数组中元素的总和。 在此示例中，`a`是`array`对象和`is_prime`函数确定其输入的值是否为质数。  
  
 [!code-cpp[concrt-parallel-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_1.cpp)]  
  
## <a name="example"></a>示例  

 下面的示例显示了 naïve 来并行执行前面的示例。 此示例使用[concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)要处理的数组中并行算法和[concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)对访问进行同步的对象`prime_sum`变量. 此示例不进行扩展，因为每个线程必须等待共享资源变得可用。  
  
 [!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_2.cpp)]  
  
## <a name="example"></a>示例  
 下面的示例使用`combinable`对象以提高性能的前面的示例。 此示例不需要将同步对象;因为进行缩放`combinable`对象使每个线程来独立执行其任务。  
  
 A`combinable`对象通常使用采用两个步骤。 首先，通过并行执行工作来生成一系列细化的计算。 接下来，组合 （或减少） 计算到最终结果。 此示例使用[concurrency::combinable::local](reference/combinable-class.md#local)方法来获取对本地之和的引用。 然后，它使用[concurrency::combinable::combine](reference/combinable-class.md#combine)方法和一个[std::plus](../../standard-library/plus-struct.md)要合并为最终结果将本地计算对象。  

  
 [!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_3.cpp)]  
  
## <a name="example"></a>示例  
 下面的完整示例串行和并行计算质数个数的总和。 示例控制台输出了进行两种计算所需的时间。  
  
 [!code-cpp[concrt-parallel-sum-of-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_4.cpp)]  
  
 以下是具有四个处理器的计算机的输出示例。  
  
```Output  
1709600813  
serial time: 6178 ms  
 
1709600813  
parallel time: 1638 ms  
```  
  
## <a name="compiling-the-code"></a>编译代码  
 若要编译代码，将其复制，然后将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`parallel-sum-of-primes.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc 并行的总和-的-primes.cpp**  
  
## <a name="robust-programming"></a>可靠编程  
 示例使用映射和化简操作即可生成相同的结果，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。  
  
## <a name="see-also"></a>请参阅  
 [并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)   
 [combinable 类](../../parallel/concrt/reference/combinable-class.md)   
 [critical_section 类](../../parallel/concrt/reference/critical-section-class.md)
