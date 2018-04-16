---
title: "如何： 使用并行容器提高效率 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- increasing efficiency with parallel containers [Concurrency Runtime]
- concurrent_queue class, examples
- concurrent_vector class, examples
ms.assetid: bd00046d-e9b6-4ae1-b661-3995f671b867
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 64b191b97bcf4b5f1607cde56fac8fefd1505c7c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-parallel-containers-to-increase-efficiency"></a>如何：使用并行容器提高效率
本主题演示如何使用并行容器来高效地存储和访问数据并行。  
  
 示例代码计算质数和并行 Carmichael 数字的组。 然后，为每个 Carmichael 编号，代码会计算该数字的主要因素。  
  
## <a name="example"></a>示例  
 下面的示例演示`is_prime`函数，确定输入的值是否为质数，和`is_carmichael`函数，确定输入的值是否为 Carmichael 数。  
  
 [!code-cpp[concrt-carmichael-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_1.cpp)]  
  
## <a name="example"></a>示例  
 下面的示例使用`is_prime`和`is_carmichael`函数来计算质数和 Carmichael 数字的集。 该示例使用[concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)和[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)并行算法来计算每个设置。 有关并行算法的详细信息，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。  
  
 此示例使用[concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)对象以保存的一套 Carmichael 数字，因为它更高版本将通过以下方式使用该对象作为工作队列。 它使用[concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)对象以保存质数的集，因为它更高版本将循环访问该选项设置为查找主要因素。  
  
 [!code-cpp[concrt-carmichael-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_2.cpp)]  
  
## <a name="example"></a>示例  
 下面的示例演示`prime_factors_of`使用试用除法来查找给定值的所有主要因素的函数。  
  
 此函数使用[concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)要循环访问集合的质数算法。 `concurrent_vector`对象使并行循环并发添加到结果的主要因素。  
  
 [!code-cpp[concrt-carmichael-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_3.cpp)]  
  
## <a name="example"></a>示例  
 此示例通过调用处理 Carmichael 数字的队列中每个元素`prime_factors_of`函数来计算其主要因素。 它使用任务组来并行执行此工作。 有关任务组的详细信息，请参阅[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
 此示例将打印为每个 Carmichael 号码的主要因素，如果该版本号中有多个四个主要因素。  
  
 [!code-cpp[concrt-carmichael-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_4.cpp)]  
  
## <a name="example"></a>示例  
 下面的代码显示完整示例，其中使用并行容器来计算 Carmichael 数字的主要因素。  
  
 [!code-cpp[concrt-carmichael-primes#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_5.cpp)]  
  
 该示例产生下面的示例输出。  
  
```Output  
Prime factors of 9890881 are: 7 11 13 41 241.  
Prime factors of 825265 are: 5 7 17 19 73.  
Prime factors of 1050985 are: 5 13 19 23 37.  
```  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`carmichael-primes.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc carmichael primes.cpp**  
  
## <a name="see-also"></a>请参阅  
 [并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)   
 [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [concurrent_vector 类](../../parallel/concrt/reference/concurrent-vector-class.md)   
 [concurrent_queue 类](../../parallel/concrt/reference/concurrent-queue-class.md)   
 [parallel_invoke 函数](reference/concurrency-namespace-functions.md#parallel_invoke)   
 [parallel_for 函数](reference/concurrency-namespace-functions.md#parallel_for)   
 [task_group 类](reference/task-group-class.md)
