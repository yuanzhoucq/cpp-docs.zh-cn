---
title: 如何：指定特定的计划程序策略
ms.date: 11/04/2016
helpviewer_keywords:
- specifying scheduler policies [Concurrency Runtime]
- scheduler policies, specifying [Concurrency Runtime]
ms.assetid: 9c5149f9-ac34-4ff3-9e79-0bad103e4e6b
ms.openlocfilehash: bd5edfbdf6b0fda9c7e327dab9538bbf6b5e4b12
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142455"
---
# <a name="how-to-specify-specific-scheduler-policies"></a>如何：指定特定的计划程序策略

计划程序策略使你能够控制计划程序在管理任务时使用的策略。 本主题说明如何使用计划程序策略来提高将进度指示器打印到控制台的任务的线程优先级。

有关将自定义计划程序策略与异步代理一起使用的示例，请参阅[如何：创建使用特定计划程序策略的代理](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)。

## <a name="example"></a>示例

下面的示例并行执行两个任务。 第一个任务<sup>计算第 n 个斐波</sup>那契数。 第二个任务将进度指示器打印到控制台。

第一个任务使用递归分解来计算斐波那契数。 也就是说，每个任务都以递归方式创建子任务来计算总体结果。 使用递归分解的任务可能会使用所有可用的资源，从而枯竭其他任务。 在此示例中，打印进度指示器的任务可能无法及时获得计算资源的访问权限。

为了提供打印进度消息公平访问计算资源的任务，此示例使用[如何：管理计划程序实例](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)中描述的步骤来创建具有自定义策略的计划程序实例。 自定义策略将线程优先级指定为最高优先级的类。

此示例使用[concurrency：： call](../../parallel/concrt/reference/call-class.md)和[concurrency：： timer](../../parallel/concrt/reference/timer-class.md)类来打印进度指示器。 这些类具有其构造函数的版本，这些构造函数获取对其进行计划的[concurrency：：计划程序](../../parallel/concrt/reference/scheduler-class.md)对象的引用。 该示例使用默认计划程序来计划计算斐波那契数的任务和计划程序实例，以便计划打印进度指示器的任务。

为了说明使用具有自定义策略的计划程序的优点，此示例执行了两次总体任务。 该示例首先使用默认计划程序来计划这两个任务。 然后，该示例使用默认计划程序来计划第一个任务，并使用一个计划程序，该计划程序具有自定义策略来安排第二个任务。

[!code-cpp[concrt-scheduler-policy#1](../../parallel/concrt/codesnippet/cpp/how-to-specify-specific-scheduler-policies_1.cpp)]

本示例生成以下输出。

```Output
Default scheduler:
...........................................................................done
Scheduler that has a custom policy:
...........................................................................done
```

尽管这两组任务都生成相同的结果，但使用自定义策略的版本使打印进度指示器的任务能够以提升的优先级运行，使其行为更对象。

## <a name="compiling-the-code"></a>编译代码

复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为 `scheduler-policy.cpp` 的文件中，然后在 Visual Studio 命令提示符窗口中运行以下命令。

> **cl/EHsc scheduler-policy**

## <a name="see-also"></a>另请参阅

[计划程序策略](../../parallel/concrt/scheduler-policies.md)<br/>
[如何：管理计划程序实例](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br/>
[如何：创建使用特定计划程序策略的代理](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)
