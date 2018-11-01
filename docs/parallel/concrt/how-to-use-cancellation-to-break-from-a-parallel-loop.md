---
title: 如何：使用取消中断 Parallel 循环
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
ms.openlocfilehash: 2a19c2874ce331be2d4f5840f61cabf7bca9abf6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612740"
---
# <a name="how-to-use-cancellation-to-break-from-a-parallel-loop"></a>如何：使用取消中断 Parallel 循环

本示例说明如何使用取消操作来实现基本的并行搜索算法。

## <a name="example"></a>示例

以下示例使用取消搜索数组中的元素。 `parallel_find_any`函数使用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法以及[concurrency:: run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token)函数搜索包含给定的值的位置。 当并行循环找到该值时，它将调用[concurrency::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel)方法来取消未来的工作。

[!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]

[Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法并发作用。 因此，它不会按预先确定的顺序执行操作。 如果数组包含值的多个实例，则结果可以是其位置的任何一个。

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`parallel-array-search.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc 并行数组 search.cpp**

## <a name="see-also"></a>请参阅

[PPL 中的取消操作](cancellation-in-the-ppl.md)<br/>
[并行算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for 函数](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[cancellation_token_source 类](../../parallel/concrt/reference/cancellation-token-source-class.md)
