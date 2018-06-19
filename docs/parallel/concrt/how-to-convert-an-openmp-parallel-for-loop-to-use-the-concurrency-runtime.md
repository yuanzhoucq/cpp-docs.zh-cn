---
title: 如何： 转换 OpenMP parallel for 循环以使用并发运行时 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, parallel for loops
- converting from OpenMP to the Concurrency Runtime, parallel loops
- parallel for loops, converting from OpenMP to the Concurrency Runtime
- parallel loops, converting from OpenMP to the Concurrency Runtime
ms.assetid: d8a7b656-f86c-456e-9c5d-a7d52f94646e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93538e3188f0086039ecc0b681f936954d82ae97
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687018"
---
# <a name="how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime"></a>如何：转换 OpenMP parallel for 循环以使用并发运行时

此示例演示如何转换使用 OpenMP 基本循环[并行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)和[为](../../parallel/openmp/reference/for-openmp.md)指令以使用并发运行时[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法。  
  
## <a name="example"></a>示例  
 此示例使用 OpenMP 和并发运行时来计算数组中的随机值的质数的计数。  
  
 [!code-cpp[concrt-openmp#1](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_1.cpp)]  
  
 本示例生成以下输出。  
  
```Output  
Using OpenMP...  
found 107254 prime numbers.  
Using the Concurrency Runtime...  
found 107254 prime numbers.  
```  
  
 `parallel_for`算法和 OpenMP 3.0 允许对于索引类型是带符号整型类型或无符号整型类型。 `parallel_for`算法还可确保指定的范围不会溢出带符号的类型。 OpenMP 版本 2.0 和 2.5 允许仅适用于有符号整数的索引类型。 OpenMP 也不会验证索引范围。  
  
 此示例中，使用并发运行时的版本还使用[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)对象代替[原子](../../parallel/openmp/reference/atomic.md)指令而无需递增计数器值同步。  
  
 有关详细信息`parallel_for`和其他并行算法，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。 有关详细信息`combinable`类，请参阅[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## <a name="example"></a>示例  

 此示例修改在上一操作， [std:: array](../../standard-library/array-class-stl.md)而不是对象上的本机数组。 因为 OpenMP 版本 2.0 和 2.5 允许对于仅在已签名整数索引类型`parallel_for`构造，你不能使用迭代器访问的并行中的 c + + 标准库容器元素。 并行模式库 (PPL) 提供[concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)算法，并行，如提供的 c + + 标准库对迭代容器执行任务，该算法。 它使用相同的分区逻辑，`parallel_for`算法使用。 `parallel_for_each`算法类似于 c + + 标准库[for_each](../../standard-library/algorithm-functions.md#for_each)算法，只不过`parallel_for_each`算法并发执行的任务。  
  
 [!code-cpp[concrt-openmp#10](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_2.cpp)]  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`concrt-omp-count-primes.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc /openmp concrt-omp-计数-primes.cpp**  
  
## <a name="see-also"></a>请参阅  
 [从 OpenMP 迁移至并发运行时](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [并行算法](../../parallel/concrt/parallel-algorithms.md)   
 [并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)

