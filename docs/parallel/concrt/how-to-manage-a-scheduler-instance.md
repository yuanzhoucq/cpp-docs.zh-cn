---
title: 如何： 管理计划程序实例 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- managing a scheduler instance [Concurrency Runtime]
- scheduler instances, managing [Concurrency Runtime]
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 699abcbc75dc4f0df40d07d26c0e6987d4711fe3
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-manage-a-scheduler-instance"></a>如何：管理计划程序实例
计划程序实例，可以将特定的计划策略与各种类型的工作负荷相关联。 本主题包含两个基本示例，演示如何创建和管理计划程序实例。  
  
 这些示例将创建计划程序，使用默认计划程序策略。 创建一个计划程序的示例使用自定义策略，请参阅[如何： 指定特定计划程序策略](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)。  
  
### <a name="to-manage-a-scheduler-instance-in-your-application"></a>若要管理你的应用程序中的计划程序实例  
  
1.  创建[concurrency:: schedulerpolicy](../../parallel/concrt/reference/schedulerpolicy-class.md)包含策略的对象值的计划程序使用。  
  

2.  调用[concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create)方法或[concurrency::Scheduler::Create](reference/scheduler-class.md#create)方法来创建计划程序实例。  
  
     如果你使用`Scheduler::Create`方法中，调用[concurrency::Scheduler::Attach](reference/scheduler-class.md#attach)方法在需要以与当前上下文关联的计划程序时。  
  
3.  调用[CreateEvent](http://msdn.microsoft.com/library/windows/desktop/ms682396)函数来创建一个非终止，自动重置事件对象的句柄。  
  
4.  将句柄传递到你刚刚创建到的事件对象[concurrency::CurrentScheduler::RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)方法或[concurrency::Scheduler::RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)方法。 这将会注册要在计划程序被销毁时才能设置的事件。  
  
5.  执行所需的当前计划程序计划的任务。  
  
6.  调用[concurrency::CurrentScheduler::Detach](reference/currentscheduler-class.md#detach)方法以分离当前计划程序和还原以前与当前计划。  
  
     如果你使用`Scheduler::Create`方法中，调用[concurrency::Scheduler::Release](reference/scheduler-class.md#release)方法以递减的引用计数`Scheduler`对象。  
  
7.  将句柄传递到的事件[WaitForSingleObject](http://msdn.microsoft.com/library/windows/desktop/ms687032)函数等待计划程序以便关闭。  
  
8.  调用[CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211)函数以关闭事件对象的句柄。  
  
## <a name="example"></a>示例  
 下面的代码演示两种方法来管理计划程序实例。 每个示例首先使用默认计划程序来执行任务打印出的当前计划程序的唯一标识符。 每个示例然后使用计划程序实例，则再次执行相同的任务。 最后，每个示例将还原与当前的默认计划程序，并执行一次的任务。  
  
 第一个示例使用[concurrency:: currentscheduler](../../parallel/concrt/reference/currentscheduler-class.md)类创建的计划程序实例，然后将其与当前上下文相关联。 第二个示例使用[concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)类来执行相同的任务。 通常情况下，`CurrentScheduler`类用于处理的当前计划程序。 使用的第二个示例`Scheduler`类中，当你想要控制计划程序与当前上下文关联，或如果想要将特定计划程序与特定任务相关联时非常有用。  
  
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
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`scheduler-instance.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc 计划程序-instance.cpp**  
  
## <a name="see-also"></a>请参阅  
 [计划程序实例](../../parallel/concrt/scheduler-instances.md)   
 [如何：指定特定的计划程序策略](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)

