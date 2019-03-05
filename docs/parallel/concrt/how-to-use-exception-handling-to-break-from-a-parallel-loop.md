---
title: 如何：使用异常处理来中断并行循环
ms.date: 11/04/2016
helpviewer_keywords:
- search algorithm, writing [Concurrency Runtime]
- writing a search algorithm [Concurrency Runtime]
ms.assetid: 16d7278c-2d10-4014-9f58-f1899e719ff9
ms.openlocfilehash: 19d732d98f24172471d96cd5e2962b2a99ab0203
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262306"
---
# <a name="how-to-use-exception-handling-to-break-from-a-parallel-loop"></a>如何：使用异常处理来中断并行循环

本主题演示如何编写基本树结构的搜索算法。

本主题[取消](cancellation-in-the-ppl.md)说明并行模式库中的取消操作的作用。 使用异常处理是一种不太有效的方式来取消并行工作的使用比[concurrency::task_group::cancel](reference/task-group-class.md#cancel)并[concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel)方法。 但是，使用异常处理来取消工作是相应的一种情况是调用到第三方库中使用任务或并行算法，但不提供`task_group`或`structured_task_group`要取消对象。

## <a name="example"></a>示例

下面的示例演示一个基本`tree`类型，它包含的数据元素和子节点的列表。 以下部分显示的正文`for_all`方法，而该操作递归执行每个子节点的工作函数。

[!code-cpp[concrt-task-tree-search#2](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_1.cpp)]

## <a name="example"></a>示例

下面的示例演示`for_all`方法。 它使用[concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)算法以并行树的每个节点上执行工作函数。

[!code-cpp[concrt-task-tree-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_2.cpp)]

## <a name="example"></a>示例

下面的介绍了 `search_for_value` 函数，它可在所提供的 `tree` 对象中搜索值。 此函数将传递给`for_all`方法中，找到包含所提供的值的树节点时，会引发的工作函数。

假定`tree`类提供由第三方库，并不能修改它。 使用异常处理适合这种情况下，因为`for_all`方法不提供`task_group`或`structured_task_group`给调用方的对象。 因此，工作函数不能直接取消其父任务组。

当向任务组提供工作函数引发了异常时，运行时停止任务组 （包括任何子任务组） 中的所有任务，并放弃任何尚未启动的任务。 `search_for_value`函数使用`try` - `catch`块来捕捉异常并将结果打印到控制台。

[!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_3.cpp)]

## <a name="example"></a>示例

下面的示例创建`tree`对象并在其中搜索有关并行的几个值。 `build_tree`函数在本主题后面所示。

[!code-cpp[concrt-task-tree-search#4](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_4.cpp)]

此示例使用[concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)要搜索的值以并行算法。 有关此算法的详细信息，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="example"></a>示例

下面的完整示例使用异常处理，若要搜索的基本的树状结构中的值。

[!code-cpp[concrt-task-tree-search#5](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_5.cpp)]

此示例生成下面的示例输出。

```Output
Found a node with value 32614.
Found a node with value 86131.
Did not find node with value 17522.
```

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`task-tree-search.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc 任务树 search.cpp**

## <a name="see-also"></a>请参阅

[PPL 中的取消操作](cancellation-in-the-ppl.md)<br/>
[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[并行算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[task_group 类](reference/task-group-class.md)<br/>
[structured_task_group 类](../../parallel/concrt/reference/structured-task-group-class.md)<br/>
[parallel_for_each 函数](reference/concurrency-namespace-functions.md#parallel_for_each)
