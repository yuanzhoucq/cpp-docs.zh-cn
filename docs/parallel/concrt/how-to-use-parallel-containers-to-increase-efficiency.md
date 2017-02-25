---
title: "如何：使用并行容器提高效率 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "使用并行容器提高效率 [并发运行时]"
  - "concurrent_queue 类，示例"
  - "concurrent_vector 类，示例"
ms.assetid: bd00046d-e9b6-4ae1-b661-3995f671b867
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 如何：使用并行容器提高效率
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题说明如何使用并行容器以并行方式高效地存储和访问数据。  
  
 代码示例以并行方式计算一组质数和 Carmichael 数。  然后，对于每个 Carmichael 数，此代码将计算该数的质数因子。  
  
## 示例  
 下面的示例显示了 `is_prime` 函数和 `is_carmichael` 函数，前者可确定输入值是否为质数，后者可确定输入值是否为 Carmichael 数。  
  
 [!code-cpp[concrt-carmichael-primes#1](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-containers-to-increase-efficiency_1.cpp)]  
  
## 示例  
 下面的示例使用 `is_prime` 和 `is_carmichael` 函数计算多组质数和 Carmichael 数。  此示例使用 [concurrency::parallel\_invoke](../Topic/parallel_invoke%20Function.md) 和 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 算法以并行方式计算每个组。  有关并行算法的更多信息，请参见[并行算法](../../parallel/concrt/parallel-algorithms.md)。  
  
 此示例使用 [concurrency::concurrent\_queue](../../parallel/concrt/reference/concurrent-queue-class.md) 对象保存一组 Carmichael 数，因为它稍后会将该对象用作工作队列。  此示例使用 [concurrency::concurrent\_vector](../../parallel/concrt/reference/concurrent-vector-class.md) 对象保存一组质数，因为它稍后将循环访问此组以查找质数因子。  
  
 [!code-cpp[concrt-carmichael-primes#2](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-containers-to-increase-efficiency_2.cpp)]  
  
## 示例  
 下面的示例演示 `prime_factors_of` 函数，该函数使用试除法来查找给定值的所有质数因子。  
  
 该函数使用 [concurrency::parallel\_for\_each](../Topic/parallel_for_each%20Function.md) 算法循环访问质数集合。  `concurrent_vector` 对象使并行循环能够同时向结果中添加多个质数因子。  
  
 [!code-cpp[concrt-carmichael-primes#3](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-containers-to-increase-efficiency_3.cpp)]  
  
## 示例  
 此示例通过调用 `prime_factors_of` 函数计算 Carmichael 数的质数因子来处理 Carmichael 数队列中的每个元素。  此示例使用任务组以并行方式执行此任务。  有关任务组的更多信息，请参见[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
 此示例将输出每个具有四个以上的质数因子的 Carmichael 数的质数因子。  
  
 [!code-cpp[concrt-carmichael-primes#4](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-containers-to-increase-efficiency_4.cpp)]  
  
## 示例  
 下面的代码演示完整示例，该示例使用并行容器计算 Carmichael 数的质数因子。  
  
 [!code-cpp[concrt-carmichael-primes#5](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-containers-to-increase-efficiency_5.cpp)]  
  
 此示例产生下面的示例输出。  
  
  **9890881的质因子为 :7 11 13 41 241。**  
**825265的质因子为 :5 7 17 19 73。**  
**1050985的质因子为 :5 13 19 23 37。**   
## 编译代码  
 复制代码示例，再将此代码粘贴到Visual Studio 项目中或一个名为`carmichael-primes.cpp`的文件中，然后在Visual Studio命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc carmichael\-primes.cpp**  
  
## 请参阅  
 [并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)   
 [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [concurrent\_vector 类](../../parallel/concrt/reference/concurrent-vector-class.md)   
 [concurrent\_queue 类](../../parallel/concrt/reference/concurrent-queue-class.md)   
 [parallel\_invoke 函数](../Topic/parallel_invoke%20Function.md)   
 [parallel\_for 函数](../Topic/parallel_for%20Function.md)   
 [task\_group 类](../Topic/task_group%20Class.md)