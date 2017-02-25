---
title: "如何：使用 combinable 来组合集 | Microsoft Docs"
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
  - "combinable 类, 示例"
  - "使用 combinable 组合集 [并发运行时]"
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 如何：使用 combinable 来组合集
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题演示如何使用 [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) 类计算质数集。  
  
## 示例  
 下面的示例将质数集计算两次。  每次计算都会将结果存储在 [std::bitset](../../standard-library/bitset-class.md) 对象中。  此示例首先按顺序计算该集，然后以并行方式计算该集。  此示例还会将执行两个计算所需的时间输出到控制台。  
  
 此示例使用 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 算法和 `combinable` 对象生成线程本地集。  然后使用 [concurrency::combinable::combine\_each](../Topic/combinable::combine_each%20Method.md) 方法将这些线程本地集合并为一个最终集。  
  
 [!code-cpp[concrt-parallel-combine-primes#1](../../parallel/concrt/codesnippet/CPP/how-to-use-combinable-to-combine-sets_1.cpp)]  
  
 下例是四处理器计算机的输出结果。  
  
  **序列化时间：312 ms**  
**并行时间：78 ms**   
## 编译代码  
 复制代码示例，再将此代码粘贴到Visual Studio 项目中或一个名为 `parallel-combine-primes.cpp` 的文件中，然后在Visual Studio命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc parallel\-combine\-primes.cpp**  
  
## 请参阅  
 [并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)   
 [combinable 类](../../parallel/concrt/reference/combinable-class.md)   
 [combinable::combine\_each 方法](../Topic/combinable::combine_each%20Method.md)