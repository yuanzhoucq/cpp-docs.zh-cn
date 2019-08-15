---
title: 如何：管理计划程序实例
ms.date: 11/04/2016
helpviewer_keywords:
- managing a scheduler instance [Concurrency Runtime]
- scheduler instances, managing [Concurrency Runtime]
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
ms.openlocfilehash: f402e82a18f7b804f2c25ebf0a4392d19694d25c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510529"
---
# <a name="how-to-manage-a-scheduler-instance"></a>如何：管理计划程序实例

计划程序实例允许您将特定的计划策略与不同类型的工作负载相关联。 本主题包含两个基本示例, 这些示例演示如何创建和管理计划程序实例。

这些示例创建使用默认计划程序策略的计划程序。 有关创建使用自定义策略的计划程序的示例, 请参阅[如何:指定特定的计划](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)程序策略。

### <a name="to-manage-a-scheduler-instance-in-your-application"></a>在应用程序中管理计划程序实例

1. 创建一个[concurrency:: SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md)对象, 其中包含要使用的计划程序的策略值。

1. 调用[concurrency:: CurrentScheduler:: create](reference/currentscheduler-class.md#create)方法或[Concurrency:: 调度器:: create](reference/scheduler-class.md#create)方法以创建计划程序实例。

   如果你使用`Scheduler::Create`方法, 则需要将计划程序与当前上下文相关联时, 请调用[concurrency:: 调度器:: Attach](reference/scheduler-class.md#attach)方法。

1. 调用[CreateEvent](/windows/win32/api/synchapi/nf-synchapi-createeventw)函数以创建非发出信号的自动重置事件对象的句柄。

1. 将句柄传递给刚刚创建的事件对象, 该对象为[concurrency:: CurrentScheduler:: RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)方法或[Concurrency:::: RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)方法。 这会在销毁计划程序时注册要设置的事件。

1. 执行希望当前计划程序计划的任务。

1. 调用[concurrency:: CurrentScheduler::D etach](reference/currentscheduler-class.md#detach)方法以分离当前计划程序, 并将以前的计划程序还原为当前计划程序。

   如果使用`Scheduler::Create`方法, 请调用[concurrency:: 调度器:: Release](reference/scheduler-class.md#release)方法来递减`Scheduler`对象的引用计数。

1. 将该事件的句柄传递给[WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject)函数, 以等待计划程序关闭。

1. 调用[CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle)函数以关闭事件对象的句柄。

## <a name="example"></a>示例

下面的代码演示了两种管理计划程序实例的方法。 每个示例首先使用默认计划程序来执行输出当前计划程序的唯一标识符的任务。 然后, 每个示例都使用一个计划程序实例再次执行相同的任务。 最后, 每个示例都将默认计划程序还原为当前计划程序, 然后再执行一次该任务。

第一个示例使用[concurrency:: CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md)类创建一个计划程序实例, 并将其与当前上下文相关联。 第二个示例使用[concurrency:: 调度](../../parallel/concrt/reference/scheduler-class.md)器类执行相同的任务。 通常, `CurrentScheduler`类用于处理当前计划程序。 如果要控制计划程序与当前`Scheduler`上下文的关联时间, 或者要将特定计划程序与特定任务相关联, 则第二个示例 (使用类) 非常有用。

[!code-cpp[concrt-scheduler-instance#1](../../parallel/concrt/codesnippet/cpp/how-to-manage-a-scheduler-instance_1.cpp)]

本示例生成以下输出。

```Output
Using CurrentScheduler class...

Current scheduler id: 0
Creating and attaching scheduler...
Current scheduler id: 1
Detaching scheduler...
Current scheduler id: 0

Using Scheduler class...

Current scheduler id: 0
Creating scheduler...
Attaching scheduler...
Current scheduler id: 2
Detaching scheduler...
Current scheduler id: 0
```

## <a name="compiling-the-code"></a>编译代码

复制代码示例并将其粘贴到 visual studio 项目中, 或粘贴到一个名`scheduler-instance.cpp`为的文件中, 然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl/EHsc scheduler-instance**

## <a name="see-also"></a>请参阅

[计划程序实例](../../parallel/concrt/scheduler-instances.md)<br/>
[如何：指定特定的计划程序策略](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)
