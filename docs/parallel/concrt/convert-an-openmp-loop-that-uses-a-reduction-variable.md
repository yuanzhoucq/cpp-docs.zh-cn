---
title: "如何： 转换使用缩减变量以使用并发运行时的 OpenMP 循环 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, reduction variables
- reduction variables, converting from OpenMP to the Concurrency Runtime
ms.assetid: 96623f36-5e57-4d3f-8c13-669e6cd535b1
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f218bbc47fa33e6cc9546d032311417d9e10d554
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-convert-an-openmp-loop-that-uses-a-reduction-variable-to-use-the-concurrency-runtime"></a>如何：将使用缩减变量的 OpenMP 循环转换为使用并发运行时
此示例演示如何将转换 OpenMP[并行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[为](../../parallel/openmp/reference/for-openmp.md)使用循环[缩减](../../parallel/openmp/reference/reduction.md)子句，以使用并发运行时。  
  
 OpenMP`reduction`子句可让你可以指定适用于并行区域末尾的缩减运算的一个或多个线程私有变量。 OpenMP 预定义了一套减少运算符。 每个 reduction 变量必须是标量 (例如， `int`， `long`，和`float`)。 有关如何在并行区域中使用缩减变量的 OpenMP 还定义了多个限制。  
  
 并行模式库 (PPL) 提供[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)类，该类提供允许你执行细化的计算，然后将这些计算合并到最终的可重用的线程本地存储结果。 `combinable`类是作用于标量和复杂类型的模板。 若要使用`combinable`类，在并行构造的正文中执行子计算，然后调用[concurrency::combinable::combine](reference/combinable-class.md#combine)或[concurrency::combinable::combine_each](reference/combinable-class.md#combine_each)若要生成的最终结果的方法。 `combine`和`combine_each`方法都采用*组合函数*，它指定如何组合使用的每对元素。 因此，`combinable`类并不局限于一组固定的缩减运算符。  
  
## <a name="example"></a>示例  
 此示例使用 OpenMP 和并发运行时来计算这些首先 35 斐波那契数之和。  
  
 [!code-cpp[concrt-openmp#7](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-a-reduction-variable_1.cpp)]  
  
 本示例生成以下输出。  
  
```Output  
Using OpenMP...  
The sum of the first 35 Fibonacci numbers is 14930351.  
Using the Concurrency Runtime...  
The sum of the first 35 Fibonacci numbers is 14930351.  
```  
  
 有关详细信息`combinable`类，请参阅[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`concrt-omp-fibonacci-reduction.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc /openmp concrt-omp-斐波那契-reduction.cpp**  
  
## <a name="see-also"></a>请参阅  
 [从 OpenMP 迁移至并发运行时](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)

