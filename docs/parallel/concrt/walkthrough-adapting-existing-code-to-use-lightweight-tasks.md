---
title: 演练：改编现有代码以使用轻量级任务
ms.date: 04/25/2019
helpviewer_keywords:
- using lightweight tasks [Concurrency Runtime]
- lightweight tasks, using [Concurrency Runtime]
ms.assetid: 1edfe818-d274-46de-bdd3-e92967c9bbe0
ms.openlocfilehash: 406d4d24d0042c7bded4f94dcef1e7731ab3947f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512148"
---
# <a name="walkthrough-adapting-existing-code-to-use-lightweight-tasks"></a>演练：改编现有代码以使用轻量级任务

本主题演示如何调整使用 Windows API 的现有代码, 以创建和执行线程以使用轻量级任务。

*轻量级任务*是从[concurrency::](../../parallel/concrt/reference/scheduler-class.md) schedule 或[concurrency:: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md)对象直接计划的任务。 当改编现有代码以使用并发运行时的计划功能时，轻量级任务非常有用。

## <a name="prerequisites"></a>系统必备

在开始本演练之前, 请阅读[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)主题。

## <a name="example"></a>示例

### <a name="description"></a>描述

下面的示例演示了 Windows API 用于创建和执行线程的典型用法。 此示例使用[CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)函数`MyThreadFunction`在单独的线程上调用。

### <a name="code"></a>代码

[!code-cpp[concrt-windows-threads#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_1.cpp)]

### <a name="comments"></a>注释

本示例生成以下输出。

```Output
Parameters = 50, 100
```

以下步骤演示如何调整代码示例, 以使用并发运行时执行相同的任务。

### <a name="to-adapt-the-example-to-use-a-lightweight-task"></a>改编示例以使用轻量级任务

1. 添加标头文件 concrt 的指令。`#include`

[!code-cpp[concrt-migration-lwt#2](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_2.cpp)]

1. 为命名空间添加`using`指令 `concurrency` 。

[!code-cpp[concrt-migration-lwt#3](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_3.cpp)]

1. 更改的`MyThreadFunction`声明以`__cdecl`使用调用约定并返回`void`。

[!code-cpp[concrt-migration-lwt#4](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_4.cpp)]

1. 修改结构, 使之包含[concurrency:: event](../../parallel/concrt/reference/event-class.md)对象, 该对象指示任务已完成的主应用程序。 `MyData`

[!code-cpp[concrt-migration-lwt#5](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_5.cpp)]

1. 使用对`CreateThread` [concurrency:: CurrentScheduler:: ScheduleTask](reference/currentscheduler-class.md#scheduletask)方法的调用替换对的调用。

[!code-cpp[concrt-migration-lwt#6](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_6.cpp)]

1. 使用对`WaitForSingleObject` [concurrency:: event:: wait](reference/event-class.md#wait)方法的调用替换对的调用, 以等待任务完成。

[!code-cpp[concrt-migration-lwt#7](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_7.cpp)]

1. 删除对`CloseHandle`的调用。

1. 将的定义`MyThreadFunction`的签名更改为与步骤3匹配。

[!code-cpp[concrt-migration-lwt#8](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_8.cpp)]

9. 在`MyThreadFunction`函数的末尾, 调用[concurrency:: event:: set](reference/event-class.md#set)方法以向主应用程序发出任务已完成的信号。

[!code-cpp[concrt-migration-lwt#9](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_9.cpp)]

10. 从中`MyThreadFunction`删除语句。 `return`

## <a name="example"></a>示例

### <a name="description"></a>描述

下面的已完成示例显示使用轻量级任务调用`MyThreadFunction`函数的代码。

### <a name="code"></a>代码

[!code-cpp[concrt-migration-lwt#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_10.cpp)]

### <a name="comments"></a>注释

## <a name="see-also"></a>请参阅

[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Scheduler 类](../../parallel/concrt/reference/scheduler-class.md)
