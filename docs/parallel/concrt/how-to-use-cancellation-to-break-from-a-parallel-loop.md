---
title: 如何：使用取消中断并行循环
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
ms.openlocfilehash: 21907de6c5625f7774ae788cef0449ac49107e40
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142138"
---
# <a name="how-to-use-cancellation-to-break-from-a-parallel-loop"></a>如何：使用取消中断并行循环

本示例说明如何使用取消操作来实现基本的并行搜索算法。

## <a name="example"></a>示例

下面的示例使用取消在数组中搜索元素。 `parallel_find_any` 函数使用[concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法，使用[concurrency：： run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token)函数搜索包含给定值的位置。 当并行循环查找值时，它会调用[concurrency：： cancellation_token_source：： cancel](reference/cancellation-token-source-class.md#cancel)方法来取消将来的工作。

[!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]

[Concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法并发操作。 因此，它不按预先确定的顺序执行操作。 如果数组包含值的多个实例，则结果可以是其任何一个位置。

## <a name="compiling-the-code"></a>编译代码

复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为 `parallel-array-search.cpp` 的文件中，然后在 Visual Studio 命令提示符窗口中运行以下命令。

> **cl/EHsc parallel-array-search**

## <a name="see-also"></a>另请参阅

[PPL 中的取消操作](cancellation-in-the-ppl.md)<br/>
[并行算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for 函数](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[cancellation_token_source 类](../../parallel/concrt/reference/cancellation-token-source-class.md)
