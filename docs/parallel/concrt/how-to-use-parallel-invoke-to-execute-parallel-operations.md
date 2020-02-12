---
title: 如何：使用 parallel_invoke 来执行并行操作
ms.date: 11/04/2016
helpviewer_keywords:
- parallel_invoke function, example
- calling multiple functions in parallel [Concurrency Runtime]
ms.assetid: a6aea69b-d647-4b7e-bf3b-e6a6a9880072
ms.openlocfilehash: 199b663331e3322601100206f222e80bbb7c8db0
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142272"
---
# <a name="how-to-use-parallel_invoke-to-execute-parallel-operations"></a>如何：使用 parallel_invoke 来执行并行操作

此示例演示如何使用[concurrency：:p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)算法来提高对共享数据源执行多个操作的程序的性能。 因为任何操作都不会修改源，所以可以直接并行执行这些操作。

## <a name="example"></a>示例

请考虑以下代码示例，该代码示例创建一个 `MyDataType`类型的变量，调用一个函数以初始化该变量，然后对这些数据执行多个较长的操作。

[!code-cpp[concrt-parallel-word-mining#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_1.cpp)]

如果 `lengthy_operation1`、`lengthy_operation2`和 `lengthy_operation3` 函数不会修改 `MyDataType` 变量，则无需进行其他修改即可并行执行这些函数。

## <a name="example"></a>示例

下面的示例修改了上一个示例以并行运行。 `parallel_invoke` 算法并行执行每个任务，并在所有任务完成后返回。

[!code-cpp[concrt-parallel-word-mining#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_2.cpp)]

## <a name="example"></a>示例

下面的示例从 gutenberg.org 下载*iliad of* by Homer，并对该文件执行多个操作。 该示例首先按顺序执行这些操作，然后并行执行相同的操作。

[!code-cpp[concrt-parallel-word-mining#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_3.cpp)]

此示例将生成以下示例输出。

```Output
Downloading 'The Iliad'...

Running serial version... took 953 ms.
Running parallel version... took 656 ms.

The most common words that have five or more letters are:
    their (953)
    shall (444)
    which (431)
    great (398)
    Hector (349)
    Achilles (309)
    through (301)
    these (268)
    chief (259)
The longest sequence of words that have the same first letter is:
    through the tempest to the tented
The following palindromes appear in the text:
    spots stops
    speed deeps
    keels sleek
```

此示例使用 `parallel_invoke` 算法调用对同一数据源执行的多个函数。 您可以使用 `parallel_invoke` 算法并行调用任意一组函数，而不仅是对相同数据进行操作的函数。

由于 `parallel_invoke` 算法并行调用每个工作函数，因此它的性能由完成最长时间的函数（即，如果运行时处理单独处理器上的每个函数）进行限制。 如果此示例并行执行的任务比可用处理器的数量多，则可以在每个处理器上运行多个任务。 在这种情况下，性能由完成时间最长的任务组进行限制。

由于本示例并行执行三个任务，因此，不应在具有三个以上处理器的计算机上缩放性能。 为了更好地提高性能，你可以将运行时间最长的任务分解为更小的任务并并行运行这些任务。

如果不需要取消支持，则可以使用 `parallel_invoke` 算法而不是[concurrency：： task_group](reference/task-group-class.md)和[concurrency：： structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)类。 有关比较 `parallel_invoke` 算法与任务组的用法的示例，请参阅[如何：使用 Parallel_invoke 编写并行排序例程](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)。

## <a name="compiling-the-code"></a>编译代码

若要编译代码，请复制代码并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为 `parallel-word-mining.cpp` 的文件中，然后在 Visual Studio 命令提示符窗口中运行以下命令。

> **cl al.exe/MD/DUNICODE/D_AFXDLL parallel-word-mining**

## <a name="see-also"></a>另请参阅

[并行算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_invoke 函数](reference/concurrency-namespace-functions.md#parallel_invoke)
