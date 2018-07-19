---
title: 如何： 编写 parallel_for 循环 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- writing a parallel_for loop [Concurrency Runtime]
- parallel_for function, example
ms.assetid: adb4d64e-5514-4b70-8dcb-b9210e6b5a1c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4f3121130cd4b2871e3e3df73dd4117f946caca
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689813"
---
# <a name="how-to-write-a-parallelfor-loop"></a>如何：编写 parallel_for 循环
此示例演示如何使用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)来计算两个矩阵的乘积。  
  
## <a name="example"></a>示例  
 下面的示例演示`matrix_multiply`函数，计算两个正方形矩阵的乘积。  
  
 [!code-cpp[concrt-parallel-matrix-multiply#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_1.cpp)]  
  
## <a name="example"></a>示例  
 下面的示例演示`parallel_matrix_multiply`函数，使用`parallel_for`算法并行执行外部循环。  
  
 [!code-cpp[concrt-parallel-matrix-multiply#2](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_2.cpp)]  
  
 此示例进行并行化外部循环，只是因为它执行足够的工作来受益于并行处理的开销。 如果并行化内部循环时，你将不会收到提升性能因为的少量的内部循环执行的工作不能抵消并行处理的开销。 因此，仅并行化外部循环是在大多数系统上最大程度地发挥并发优势的最佳方式。  
  
## <a name="example"></a>示例  
 以下更完整的示例比较的性能`matrix_multiply`函数与`parallel_matrix_multiply`函数。  
  
 [!code-cpp[concrt-parallel-matrix-multiply#3](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_3.cpp)]  
  
 以下是具有四个处理器的计算机的输出示例。  
  
```Output  
serial: 3853  
parallel: 1311  
```  
  
## <a name="compiling-the-code"></a>编译代码  
 若要编译代码，将其复制，然后将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`parallel-matrix-multiply.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc 并行矩阵 multiply.cpp**  
  
## <a name="see-also"></a>请参阅  
 [并行算法](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_for 函数](reference/concurrency-namespace-functions.md#parallel_for)


