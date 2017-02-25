---
title: "如何：使用 parallel_invoke 来执行并行操作 | Microsoft Docs"
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
  - "parallel_invoke 函数, 示例"
  - "并行调用多个函数 [并发运行时]"
ms.assetid: a6aea69b-d647-4b7e-bf3b-e6a6a9880072
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# 如何：使用 parallel_invoke 来执行并行操作
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此示例演示如何使用 [concurrency::parallel\_invoke](../Topic/parallel_invoke%20Function.md) 算法提高对共享数据源执行多项操作的程序的性能。  由于任何操作都不修改源，因此可以直接并行执行这些操作。  
  
## 示例  
 请考虑以下创建类型为 `MyDataType` 的变量的代码示例，调用函数来初始化该变量，然后对该数据执行多项长时间操作。  
  
 [!code-cpp[concrt-parallel-word-mining#1](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-execute-parallel-operations_1.cpp)]  
  
 如果 `lengthy_operation1`、`lengthy_operation2` 和 `lengthy_operation3` 函数不修改 `MyDataType` 变量，则可以在不进行额外修改的情况下并行执行这些函数。  
  
## 示例  
 下面的示例修改了上面的示例以实现并行运行。  `parallel_invoke` 算法并行执行每项任务并在所有任务完成后返回。  
  
 [!code-cpp[concrt-parallel-word-mining#2](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-execute-parallel-operations_2.cpp)]  
  
## 示例  
 以下示例从 gutenberg.org 下载 *Iliad* by Homer 并对此文件执行多项操作。  此示例首先按顺序执行这些操作，然后并行执行相同操作。  
  
 [!code-cpp[concrt-parallel-word-mining#3](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-execute-parallel-operations_3.cpp)]  
  
 此示例产生下面的示例输出。  
  
  **下载'The Iliad'...**  
**的序列化版本…执行了 953 毫秒。**  
**运行并行生成…执行了 656 毫秒。**  
**具有五个或更多字母中最常用的单词是：**  
 **它们 \(953\)**  
 **将 \(444\)**  
 **哪些 \(431\)**  
 **大于\(398\)**  
 **赫克托耳 \(349\)**  
 **阿奇里斯 \(309\)**  
 **至 \(301\)**  
 **这些\(268\)**  
 **院长 \(259\)**  
**具有相同的第一个字母字符的最长序列为：**  
 **通过对帐篷按复盖的暴风雨**  
**下面回文显示文本：**  
 **发现 停止**  
 **速度 深海**  
 **船骨 打滑** 此示例使用 `parallel_invoke` 算法调用作用于相同数据源的多个函数。  您可以使用 `parallel_invoke` 算法来并行调用任何函数集，而不仅仅是那些作用于相同数据的函数集。  
  
 由于 `parallel_invoke` 算法将并行调用每个工作函数，因此其性能由花费最长时间完成的函数（即，如果运行时在单独的处理器上处理每个函数）限定。  如果此示例并行执行的任务数多于可用处理器的数目，则会在每个处理器上运行多项任务。  在此情况下，性能由花费最长时间完成的任务组限定。  
  
 因为此示例并行执行三项任务，所以您不应期望性能在超过三个处理器的计算机上会得到扩展。  若要进一步提高性能，您可以将运行时间最长的任务分为更小的任务，然后并行运行这些任务。  
  
 如果您无需取消支持，则可以使用 `parallel_invoke` 算法而不是 [concurrency::task\_group](../Topic/task_group%20Class.md) 和 [concurrency::structured\_task\_group](../../parallel/concrt/reference/structured-task-group-class.md) 类。  有关比较 `parallel_invoke` 算法与任务组的用法的示例，请参见[如何：使用 parallel\_invoke 来编写并行排序例程](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)。  
  
## 编译代码  
 若要编译代码，请复制该代码并将其粘贴到 Visual Studio项目中或名为`parallel-word-mining.cpp` 的文件中，然后在Visual Studio命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc \/MD \/DUNICODE \/D\_AFXDLL parallel\-word\-mining.cpp**  
  
## 请参阅  
 [并行算法](../../parallel/concrt/parallel-algorithms.md)   
 [parallel\_invoke 函数](../Topic/parallel_invoke%20Function.md)