---
title: "如何：编写 parallel_for 循环 | Microsoft Docs"
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
  - "编写 parallel_for 循环 [并发运行时]"
  - "parallel_for 函数, 示例"
ms.assetid: adb4d64e-5514-4b70-8dcb-b9210e6b5a1c
caps.latest.revision: 15
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：编写 parallel_for 循环
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本示例演示如何使用 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 计算两个矩阵的乘积。  
  
## 示例  
 下面的示例演示 `matrix_multiply` 函数，该函数计算两个方形矩阵的乘积。  
  
 [!code-cpp[concrt-parallel-matrix-multiply#1](../../parallel/concrt/codesnippet/CPP/how-to-write-a-parallel-for-loop_1.cpp)]  
  
## 示例  
 下面的示例演示 `parallel_matrix_multiply` 函数，该函数使用 `parallel_for` 算法并行执行外层循环。  
  
 [!code-cpp[concrt-parallel-matrix-multiply#2](../../parallel/concrt/codesnippet/CPP/how-to-write-a-parallel-for-loop_2.cpp)]  
  
 此示例仅并行化外层循环，这是因为该循环执行的工作足够多，可以从并行处理的开销中受益。  如果并行化内层循环，则将不会获得性能上的提升，这是因为内层循环执行的少量工作不能抵消并行处理的开销。  因此，仅并行化外部循环是在大多数系统上最大程度地发挥并发优势的最佳方式。  
  
## 示例  
 以下更为完整的示例将比较 `matrix_multiply` 函数与 `parallel_matrix_multiply` 函数的性能。  
  
 [!code-cpp[concrt-parallel-matrix-multiply#3](../../parallel/concrt/codesnippet/CPP/how-to-write-a-parallel-for-loop_3.cpp)]  
  
 下例是四处理器计算机的输出结果。  
  
  **序列：3853**  
**并行：1311**   
## 编译代码  
 若要编译代码，请复制代码并将其粘贴到 Visual Studio 项目中或一个名为 `parallel-matrix-multiply.cpp`的文件中，然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc parallel\-matrix\-multiply.cpp**  
  
## 请参阅  
 [并行算法](../../parallel/concrt/parallel-algorithms.md)   
 [parallel\_for 函数](../Topic/parallel_for%20Function.md)