---
title: 如何： 使用异常处理中断并行循环 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- search algorithm, writing [Concurrency Runtime]
- writing a search algorithm [Concurrency Runtime]
ms.assetid: 16d7278c-2d10-4014-9f58-f1899e719ff9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6bacb9ea6a451026f7a515878cb649090ed9cbf4
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-use-exception-handling-to-break-from-a-parallel-loop"></a>如何：使用异常处理中断并行循环
本主题演示如何编写基本树结构的搜索算法。  
  
 主题[取消](cancellation-in-the-ppl.md)说明并行模式库中的取消操作的角色。 使用异常处理是效率较低的方法来取消并行工作的使用比[concurrency::task_group::cancel](reference/task-group-class.md#cancel)和[concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel)方法。 但是，使用异常处理来取消工作是适当的一种情况是调入第三方库使用任务或并行算法，但不提供`task_group`或`structured_task_group`对象取消。  

  
## <a name="example"></a>示例  
 下面的示例演示了一个基本`tree`包含的数据元素和子节点列表的类型。 以下部分显示的正文`for_all`方法，而该操作递归在每个子节点执行工作函数。  
  
 [!code-cpp[concrt-task-tree-search#2](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_1.cpp)]  
  
## <a name="example"></a>示例  
 下面的示例演示`for_all`方法。 它使用[concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)算法并行树的每个节点上执行工作函数。  
  
 [!code-cpp[concrt-task-tree-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_2.cpp)]  
  
## <a name="example"></a>示例  
 下面的介绍了 `search_for_value` 函数，它可在所提供的 `tree` 对象中搜索值。 此函数将传递到`for_all`找到包含所提供的值的树节点时，会引发的工作函数的方法。  
  
 假定`tree`类提供由第三方库，并且您不能修改它。 在这种情况下，使用异常处理适合因为`for_all`方法不提供`task_group`或`structured_task_group`给调用方的对象。 因此，工作函数不能直接取消其父任务组。  
  
 当提供给任务组工作函数引发了异常时，运行时将停止任务组 （包括任何子任务组） 中的所有任务，并且将放弃任何尚未启动的任务。 `search_for_value`函数使用`try` - `catch`块捕获异常并将结果打印到控制台。  
  
 [!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_3.cpp)]  
  
## <a name="example"></a>示例  
 下面的示例创建`tree`对象并在其中搜索并行的一些值。 `build_tree`函数显示在本主题后面。  
  
 [!code-cpp[concrt-task-tree-search#4](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_4.cpp)]  
  
 此示例使用[concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)要值并行搜索算法。 有关此算法的详细信息，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。  
  
## <a name="example"></a>示例  
 下面的完整示例使用异常处理要搜索的基本的树状结构中的值。  
  
 [!code-cpp[concrt-task-tree-search#5](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_5.cpp)]  
  
 该示例产生下面的示例输出。  
  
```Output  
Found a node with value 32614.  
Found a node with value 86131.  
Did not find node with value 17522.  
```  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`task-tree-search.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc 任务树 search.cpp**  
  
## <a name="see-also"></a>请参阅  
 [PPL 中的取消](cancellation-in-the-ppl.md)   
 [异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [并行算法](../../parallel/concrt/parallel-algorithms.md)   
 [task_group 类](reference/task-group-class.md)   
 [structured_task_group 类](../../parallel/concrt/reference/structured-task-group-class.md)   
 [parallel_for_each 函数](reference/concurrency-namespace-functions.md#parallel_for_each)


