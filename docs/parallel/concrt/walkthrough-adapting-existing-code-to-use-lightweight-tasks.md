---
title: 演练：调整现有代码以使用轻量级任务
ms.date: 04/25/2019
helpviewer_keywords:
- using lightweight tasks [Concurrency Runtime]
- lightweight tasks, using [Concurrency Runtime]
ms.assetid: 1edfe818-d274-46de-bdd3-e92967c9bbe0
ms.openlocfilehash: e7c6096829a1cd45cfdb849a1899d6b4a2d4cb78
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141995"
---
# <a name="walkthrough-adapting-existing-code-to-use-lightweight-tasks"></a>演练：调整现有代码以使用轻量级任务

本主题演示如何调整使用 Windows API 的现有代码，以创建和执行线程以使用轻量级任务。

*轻量级任务*是从[concurrency：：](../../parallel/concrt/reference/scheduler-class.md) schedule 或[concurrency：： ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md)对象直接计划的任务。 当改编现有代码以使用并发运行时的计划功能时，轻量级任务非常有用。

## <a name="prerequisites"></a>先决条件

在开始本演练之前，请阅读[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)主题。

## <a name="example"></a>示例

下面的示例演示了 Windows API 用于创建和执行线程的典型用法。 此示例使用[CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)函数在单独的线程上调用 `MyThreadFunction`。

### <a name="initial-code"></a>初始代码

[!code-cpp[concrt-windows-threads#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_1.cpp)]

本示例生成以下输出。

```Output
Parameters = 50, 100
```

以下步骤演示如何调整代码示例，以使用并发运行时执行相同的任务。

### <a name="to-adapt-the-example-to-use-a-lightweight-task"></a>改编示例以使用轻量级任务

1. 为头文件 concrt 添加 `#include` 指令。

[!code-cpp[concrt-migration-lwt#2](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_2.cpp)]

1. 为 `concurrency` 命名空间添加 `using` 指令。

[!code-cpp[concrt-migration-lwt#3](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_3.cpp)]

1. 更改 `MyThreadFunction` 的声明以使用 `__cdecl` 调用约定并返回 `void`。

[!code-cpp[concrt-migration-lwt#4](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_4.cpp)]

1. 修改 `MyData` 结构，使其包含用于指示任务已完成的主应用程序的[concurrency：： event](../../parallel/concrt/reference/event-class.md)对象。

[!code-cpp[concrt-migration-lwt#5](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_5.cpp)]

1. 将对 `CreateThread` 的调用替换为对[concurrency：： CurrentScheduler：： ScheduleTask](reference/currentscheduler-class.md#scheduletask)方法的调用。

[!code-cpp[concrt-migration-lwt#6](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_6.cpp)]

1. 将对 `WaitForSingleObject` 的调用替换为调用[concurrency：： event：： wait](reference/event-class.md#wait)方法以等待任务完成。

[!code-cpp[concrt-migration-lwt#7](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_7.cpp)]

1. 删除对 `CloseHandle`的调用。

1. 将 `MyThreadFunction` 的定义的签名更改为与步骤3匹配。

[!code-cpp[concrt-migration-lwt#8](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_8.cpp)]

1. 在 `MyThreadFunction` 函数的末尾，调用[concurrency：： event：： set](reference/event-class.md#set)方法以向主应用程序发出任务已完成的信号。

[!code-cpp[concrt-migration-lwt#9](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_9.cpp)]

1. 从 `MyThreadFunction`中删除 `return` 语句。

### <a name="completed-code"></a>已完成代码

下面的完整示例显示了使用轻型任务调用 `MyThreadFunction` 函数的代码。

[!code-cpp[concrt-migration-lwt#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_10.cpp)]

## <a name="see-also"></a>另请参阅

[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Scheduler 类](../../parallel/concrt/reference/scheduler-class.md)
