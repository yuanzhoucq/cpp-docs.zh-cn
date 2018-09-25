---
title: 如何： 指定特定的计划程序策略 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- specifying scheduler policies [Concurrency Runtime]
- scheduler policies, specifying [Concurrency Runtime]
ms.assetid: 9c5149f9-ac34-4ff3-9e79-0bad103e4e6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 578743fc9ffc6931e596a1b924282544f5ee9601
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435410"
---
# <a name="how-to-specify-specific-scheduler-policies"></a>如何：指定特定的计划程序策略

计划程序策略让你控制管理任务时，计划程序使用的策略。 本主题演示如何使用计划程序策略来提高打印到控制台的进度指示器的任务的线程优先级别。

自定义计划程序策略与异步代理一起使用的示例，请参阅[如何： 创建该使用特定计划程序策略的代理](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)。

## <a name="example"></a>示例

下面的示例并行执行两项任务。 第一个任务将计算 n<sup>th</sup>斐波纳契数。 第二个任务将打印到控制台的进度指示器。

第一个任务使用递归分解来计算斐波纳契数。 也就是说，每个任务以递归方式创建子任务计算的整体结果。 使用递归分解的任务可能会使用所有可用资源，从而影响其他任务。 在此示例中，输出进度指示器的任务可能无法收到及时访问计算资源。

若要提供打印进度消息公平访问计算资源的任务，此示例使用中所述的步骤[如何： 管理计划程序实例](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)来创建具有自定义策略的计划程序实例。 自定义策略指定的线程优先级别是最高的优先级类。

此示例使用[concurrency:: call](../../parallel/concrt/reference/call-class.md)并[concurrency:: timer](../../parallel/concrt/reference/timer-class.md)类，以打印进度指示器。 这些类具有引用其构造函数的版本[concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)对象，该计划，方便其对象。 该示例使用默认计划程序来计划任务，用于计算斐波纳契数以及要计划的任务的输出进度指示器的计划程序实例。

为了说明使用的计划程序的自定义策略的好处，此示例执行整个任务两次。 该示例首先使用默认计划程序来计划这两项任务。 该示例然后使用默认计划程序安排第一个任务，并具有自定义策略来安排第二个任务计划程序。

[!code-cpp[concrt-scheduler-policy#1](../../parallel/concrt/codesnippet/cpp/how-to-specify-specific-scheduler-policies_1.cpp)]

本示例生成以下输出。

```Output
Default scheduler:
...........................................................................done
Scheduler that has a custom policy:
...........................................................................done
```

尽管这两组任务生成相同的结果，但使用的自定义策略的版本，输出进度指示器，以便它响应能力更强的行为在提升的优先级别运行的任务。

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`scheduler-policy.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc 计划程序-policy.cpp**

## <a name="see-also"></a>请参阅

[计划程序策略](../../parallel/concrt/scheduler-policies.md)<br/>
[如何：管理计划程序实例](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br/>
[如何：创建使用特定计划程序策略的代理](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)

