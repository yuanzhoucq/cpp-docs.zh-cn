---
title: "如何：使用取消中断 Parallel 循环 | Microsoft Docs"
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
  - "并行搜索算法, 编写 [并发运行时]"
  - "编写并行搜索算法 [并发运行时]"
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
caps.latest.revision: 19
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用取消中断 Parallel 循环
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本示例说明如何使用取消操作来实现并行基本搜索算法。  
  
## 示例  
 下面的示例使用取消操作来搜索数组中的元素。  `parallel_find_any` 函数使用 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 算法和 [concurrency::run\_with\_cancellation\_token](../Topic/run_with_cancellation_token%20Function.md) 方法搜索包含指定值的位置。  当并行循环查找值时，它调用 [concurrency::cancellation\_token\_source::cancel](../Topic/cancellation_token_source::cancel%20Method.md) 方法取消将来工作。  
  
 [!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/CPP/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]  
  
 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 算法并发作用。  因此，此算法不会按预先确定的顺序执行这些运算。  如果数组包含该值的多个实例，则结果可以是其任一位置。  
  
## 编译代码  
 复制代码示例，再将此代码粘贴到 Visual Studio项目中或一个名为`parallel-array-search.cpp` 的文件中，然后在Visual Studio命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc parallel\-array\-search.cpp**  
  
## 请参阅  
 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)   
 [并行算法](../../parallel/concrt/parallel-algorithms.md)   
 [parallel\_for 函数](../Topic/parallel_for%20Function.md)   
 [cancellation\_token\_source 类](../../parallel/concrt/reference/cancellation-token-source-class.md)