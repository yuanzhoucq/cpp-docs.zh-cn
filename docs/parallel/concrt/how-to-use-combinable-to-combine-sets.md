---
title: 如何： 使用 combinable 组合多个集 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- combinable class, example
- combining sets with combinable [Concurrency Runtime]
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 689dacb98bc9f8053686a02414151b4982edca67
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695767"
---
# <a name="how-to-use-combinable-to-combine-sets"></a>如何：使用 combinable 来组合集
本主题演示如何使用[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)类来计算质数的组。  
  
## <a name="example"></a>示例  
 下面的示例计算的一套质数两次。 每个计算存储中的结果[std::bitset](../../standard-library/bitset-class.md)对象。 该示例首先按顺序计算组，然后计算并行组。 示例还控制台输出了进行两种计算所需的时间。  
  
 此示例使用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法和`combinable`要生成线程本地组对象。 然后，它使用[concurrency::combinable::combine_each](reference/combinable-class.md#combine_each)方法，将合并到最后一组的线程本地集。  

  
 [!code-cpp[concrt-parallel-combine-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-combine-sets_1.cpp)]  
  
 以下是具有四个处理器的计算机的输出示例。  
  
```Output  
serial time: 312 ms  
 
parallel time: 78 ms  
```  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`parallel-combine-primes.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc 并行组合 primes.cpp**  
  
## <a name="see-also"></a>请参阅  
 [并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)   
 [combinable 类](../../parallel/concrt/reference/combinable-class.md)   
 [combinable:: combine_each 方法](reference/combinable-class.md#combine_each)


