---
title: 如何：使用异常处理中断并行循环
ms.date: 11/04/2016
helpviewer_keywords:
- search algorithm, writing [Concurrency Runtime]
- writing a search algorithm [Concurrency Runtime]
ms.assetid: 16d7278c-2d10-4014-9f58-f1899e719ff9
ms.openlocfilehash: a5576e8f2416804cac89f5ec34005f4e08b99c47
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142115"
---
# <a name="how-to-use-exception-handling-to-break-from-a-parallel-loop"></a>如何：使用异常处理中断并行循环

本主题说明如何编写基本树结构的搜索算法。

主题[取消](cancellation-in-the-ppl.md)说明了并行模式库中取消操作的角色。 与使用[concurrency：： task_group：： cancel](reference/task-group-class.md#cancel)和[concurrency：： structured_task_group：： cancel](reference/structured-task-group-class.md#cancel)方法相比，使用异常处理是一种不太有效的方法来取消并行工作。 但是，当你调入使用任务或并行算法的第三方库，但不提供要取消的 `task_group` 或 `structured_task_group` 对象时，可以使用异常处理来取消工作。

## <a name="example"></a>示例

下面的示例演示一个基本 `tree` 类型，该类型包含一个数据元素和一个子节点列表。 以下部分介绍 `for_all` 方法的主体，该方法将以递归方式在每个子节点上执行工作函数。

[!code-cpp[concrt-task-tree-search#2](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_1.cpp)]

## <a name="example"></a>示例

下面的示例演示 `for_all` 方法。 它使用[concurrency：:p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)算法并行执行树的每个节点上的工作函数。

[!code-cpp[concrt-task-tree-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_2.cpp)]

## <a name="example"></a>示例

下面的介绍了 `search_for_value` 函数，它可在所提供的 `tree` 对象中搜索值。 此函数将一个工作函数传递给 `for_all` 方法，该函数会在找到包含所提供值的树节点时引发。

假定 `tree` 类由第三方库提供，并且您不能修改它。 在这种情况下，使用异常处理是合适的，因为 `for_all` 方法不向调用方提供 `task_group` 或 `structured_task_group` 对象。 因此，工作函数无法直接取消其父任务组。

当你提供给任务组的工作函数引发异常时，运行时会停止任务组中的所有任务（包括任何子任务组），并放弃尚未启动的任何任务。 `search_for_value` 函数使用 `try`-`catch` 块来捕获异常，并将结果输出到控制台。

[!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_3.cpp)]

## <a name="example"></a>示例

下面的示例创建一个 `tree` 对象，并以并行方式搜索多个值。 本主题后面的部分将显示 `build_tree` 函数。

[!code-cpp[concrt-task-tree-search#4](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_4.cpp)]

此示例使用[concurrency：:p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)算法并行搜索值。 有关此算法的详细信息，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="example"></a>示例

下面的完整示例使用异常处理来搜索基本树结构中的值。

[!code-cpp[concrt-task-tree-search#5](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_5.cpp)]

此示例将生成以下示例输出。

```Output
Found a node with value 32614.
Found a node with value 86131.
Did not find node with value 17522.
```

## <a name="compiling-the-code"></a>编译代码

复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为 `task-tree-search.cpp` 的文件中，然后在 Visual Studio 命令提示符窗口中运行以下命令。

> **cl/EHsc task-tree-search**

## <a name="see-also"></a>另请参阅

[PPL 中的取消操作](cancellation-in-the-ppl.md)<br/>
[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[并行算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[task_group 类](reference/task-group-class.md)<br/>
[structured_task_group 类](../../parallel/concrt/reference/structured-task-group-class.md)<br/>
[parallel_for_each 函数](reference/concurrency-namespace-functions.md#parallel_for_each)
