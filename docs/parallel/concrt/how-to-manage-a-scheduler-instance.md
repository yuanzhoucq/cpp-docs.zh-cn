---
title: 如何：管理计划程序实例
ms.date: 11/04/2016
helpviewer_keywords:
- managing a scheduler instance [Concurrency Runtime]
- scheduler instances, managing [Concurrency Runtime]
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
ms.openlocfilehash: bc7adfaeb4c96245488bbcb5cd70cdae9daf9e26
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276152"
---
# <a name="how-to-manage-a-scheduler-instance"></a>如何：管理计划程序实例

计划程序实例，您可以将特定的计划策略与各种类型的工作负荷相关联。 本主题包含两个基本示例，演示如何创建和管理计划程序实例。

这些示例将创建使用默认计划程序策略的计划程序。 创建一个计划程序的示例使用自定义策略，请参阅[如何：指定特定的计划程序策略](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)。

### <a name="to-manage-a-scheduler-instance-in-your-application"></a>若要管理你的应用程序中的计划程序实例

1. 创建[concurrency:: schedulerpolicy](../../parallel/concrt/reference/schedulerpolicy-class.md)计划程序使用的值包含策略的对象。

1. 调用[concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create)方法或[concurrency::Scheduler::Create](reference/scheduler-class.md#create)方法来创建计划程序实例。

   如果您使用`Scheduler::Create`方法中，调用[concurrency::Scheduler::Attach](reference/scheduler-class.md#attach)方法时您需要将计划程序与当前上下文相关联。

1. 调用[CreateEvent](/windows/desktop/api/synchapi/nf-synchapi-createeventa)函数来创建非信号状态，自动重置事件对象的句柄。

1. 将句柄传递给到刚创建的事件对象[concurrency::CurrentScheduler::RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)方法或[concurrency::Scheduler::RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)方法。 这将会注册时销毁计划程序设置的事件。

1. 执行所需的当前计划程序来计划任务。

1. 调用[concurrency::CurrentScheduler::Detach](reference/currentscheduler-class.md#detach)方法以分离当前计划程序并还原上一个与当前计划程序。

   如果您使用`Scheduler::Create`方法中，调用[concurrency::Scheduler::Release](reference/scheduler-class.md#release)方法以递减引用计数的`Scheduler`对象。

1. 将句柄传递给该事件[WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject)函数等待计划程序关闭。

1. 调用[CloseHandle](/windows/desktop/api/handleapi/nf-handleapi-closehandle)函数以关闭事件对象的句柄。

## <a name="example"></a>示例

下面的代码演示两种方法来管理计划程序实例。 每个示例首先使用默认计划程序执行某项任务，以输出当前计划程序的唯一标识符。 每个示例然后使用计划程序实例，则再次执行相同的任务。 最后，每个示例将还原为当前的默认计划程序并执行一次的任务。

第一个示例使用[concurrency:: currentscheduler](../../parallel/concrt/reference/currentscheduler-class.md)类来创建计划程序实例并将其与当前上下文相关联。 第二个示例使用[concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)类来执行相同的任务。 通常情况下，`CurrentScheduler`类用于处理当前计划程序。 使用第二个示例`Scheduler`类中，你想要控制当计划程序是与当前上下文关联，或如果想要将特定的计划程序与特定任务相关联时非常有用。

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

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`scheduler-instance.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc 计划程序-instance.cpp**

## <a name="see-also"></a>请参阅

[计划程序实例](../../parallel/concrt/scheduler-instances.md)<br/>
[如何：指定特定的计划程序策略](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)
