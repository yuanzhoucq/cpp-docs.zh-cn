---
title: "如何：使用异常处理中断并行循环 | Microsoft Docs"
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
  - "搜索算法, 编写 [并发运行时]"
  - "编写搜索算法 [并发运行时]"
ms.assetid: 16d7278c-2d10-4014-9f58-f1899e719ff9
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# 如何：使用异常处理中断并行循环
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题演示如何编写基本树结构的搜索算法。  
  
 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)主题说明了并行模式库中的取消功能。  使用异常处理取消并行工作不如使用 [concurrency::task\_group::cancel](../Topic/task_group::cancel%20Method.md) 和 [concurrency::structured\_task\_group::cancel](../Topic/structured_task_group::cancel%20Method.md) 方法有效。  但是，如果您调用使用任务或并行算法但不提供 `task_group` 或 `structured_task_group` 对象执行取消操作的第三方库，在这种情况下使用异常处理取消工作则比较合适。  
  
## 示例  
 下面的示例演示了一个基本的 `tree` 类型，该类型包含数据元素和子节点列表。  以下小节演示了以递归方式对每个子节点执行工作函数的 `for_all` 方法的主体。  
  
 [!CODE [concrt-task-tree-search#2](../CodeSnippet/VS_Snippets_ConcRT/concrt-task-tree-search#2)]  
  
## 示例  
 下面的示例演示了 `for_all` 方法。  此方法使用 [concurrency::parallel\_for\_each](../Topic/parallel_for_each%20Function.md) 算法对树中的各个节点并行执行工作函数。  
  
 [!CODE [concrt-task-tree-search#1](../CodeSnippet/VS_Snippets_ConcRT/concrt-task-tree-search#1)]  
  
## 示例  
 下面的示例演示了 `search_for_value` 函数，该函数在所提供的 `tree` 对象中搜索值。  此函数向 `for_all` 方法传递工作函数，该工作函数在找到包含所提供的值的树节点时将会引发。  
  
 假设第三方库提供 `tree` 类，并且您可以对其进行修改。  在这种情况下使用异常处理比较合适，因为 `for_all` 方法不向调用程序提供 `task_group` 或 `structured_task_group` 对象。  因此，工作函数无法直接取消其父任务组。  
  
 当提供给任务组的工作函数引发异常时，运行时将停止该任务组（包括任何子任务组）中的所有任务，并放弃任何尚未开始的任务。  `search_for_value` 函数使用 `try`\-`catch` 块捕获该异常，并将结果打印到控制台。  
  
 [!CODE [concrt-task-tree-search#3](../CodeSnippet/VS_Snippets_ConcRT/concrt-task-tree-search#3)]  
  
## 示例  
 下面的示例创建了一个 `tree` 对象，并以并行方式在该对象中搜索一些值。  本主题后面演示了 `build_tree` 函数。  
  
 [!CODE [concrt-task-tree-search#4](../CodeSnippet/VS_Snippets_ConcRT/concrt-task-tree-search#4)]  
  
 本示例使用 [concurrency::parallel\_invoke](../Topic/parallel_invoke%20Function.md) 算法并行搜索值。  有关此算法的更多信息，请参见[并行算法](../../parallel/concrt/parallel-algorithms.md)。  
  
## 示例  
 下面的完整示例使用异常处理在基本树结构中搜索值。  
  
 [!CODE [concrt-task-tree-search#5](../CodeSnippet/VS_Snippets_ConcRT/concrt-task-tree-search#5)]  
  
 此示例产生下面的示例输出。  
  
  **生成 32614 的值的节点。**  
**生成 86131 的值的节点。**  
**没有找到 17522 的值的节点。**   
## 编译代码  
 复制代码示例，并将此代码粘贴到Visual Studio项目中或一个名为`task-tree-search.cpp`的文件中，然后在Visual Studio命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc task\-tree\-search.cpp**  
  
## 请参阅  
 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)   
 [异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [并行算法](../../parallel/concrt/parallel-algorithms.md)   
 [task\_group 类](../Topic/task_group%20Class.md)   
 [structured\_task\_group 类](../../parallel/concrt/reference/structured-task-group-class.md)   
 [parallel\_for\_each 函数](../Topic/parallel_for_each%20Function.md)