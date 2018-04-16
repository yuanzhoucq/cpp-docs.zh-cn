---
title: "如何： 使用 combinable 组合多个集 |Microsoft 文档"
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
- combinable class, example
- combining sets with combinable [Concurrency Runtime]
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8bbd36e9536707bc639e8f80cc019b7fda18f793
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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


