---
title: 如何： 使用 parallel_invoke 来执行并行操作 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parallel_invoke function, example
- calling multiple functions in parallel [Concurrency Runtime]
ms.assetid: a6aea69b-d647-4b7e-bf3b-e6a6a9880072
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 07c7a5248d5a132ae7b0542bfcedddee0c081753
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>如何：使用 parallel_invoke 来执行并行操作
此示例演示如何使用[concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)算法提高执行共享的数据源的多个操作的程序的性能。 没有操作修改源，因为它们可以并行执行直接的方式。  

  
## <a name="example"></a>示例  
 请考虑下面的代码示例创建类型的变量的`MyDataType`、 调用一个函数来初始化该变量，然后执行对该数据的多个长时间的操作。  
  
 [!code-cpp[concrt-parallel-word-mining#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_1.cpp)]  
  
 如果`lengthy_operation1`， `lengthy_operation2`，和`lengthy_operation3`函数不会修改`MyDataType`变量，这些函数可以并行执行而无需其他的修改。  
  
## <a name="example"></a>示例  
 下面的示例修改了前面的示例中并行运行。 `parallel_invoke`算法以并行方式执行每个任务，并完成所有任务之后返回。  
  
 [!code-cpp[concrt-parallel-word-mining#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_2.cpp)]  
  
## <a name="example"></a>示例  
 下面的示例下载*伊利亚特*通过从 gutenberg.org Homer 并执行该文件上的多个操作。 该示例首先按顺序执行这些操作，然后并行执行相同的操作。  
  
 [!code-cpp[concrt-parallel-word-mining#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_3.cpp)]  
  
 该示例产生下面的示例输出。  
  
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
  
 此示例使用`parallel_invoke`算法调用多个函数作用于同一数据源。 你可以使用`parallel_invoke`算法以并行，不只是作用于相同的数据的那些调用的函数的任何集。  
  
 因为`parallel_invoke`算法并行调用每个工作函数，其性能受函数中需要最长的时间才能完成 （即，如果运行时处理每个单独的处理器上的函数）。 如果此示例比可用的处理器数的并行执行多个任务，可以在每个处理器上运行多个任务。 在这种情况下，性能受采用最长的时间才能完成的任务的组。  
  
 此示例并行执行三个任务，因为你不应指望性能有三个以上处理器的计算机上的缩放。 若要提高性能更多，可以将最长运行的任务分解为较小的任务，以并行方式运行这些任务。  
  
 你可以使用`parallel_invoke`算法而不是[concurrency:: task_group](reference/task-group-class.md)和[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)类如果不需要取消支持。 有关示例比较的使用情况`parallel_invoke`算法与任务组，请参阅[如何： 使用 parallel_invoke 来编写并行排序例程](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)。  
  
## <a name="compiling-the-code"></a>编译代码  
 若要编译代码，将其复制，然后将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`parallel-word-mining.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc /MD/DUNICODE /D_AFXDLL 并行 word mining.cpp**  
  
## <a name="see-also"></a>请参阅  
 [并行算法](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_invoke 函数](reference/concurrency-namespace-functions.md#parallel_invoke)


