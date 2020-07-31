---
title: 演练：调整现有代码以使用轻量级任务
ms.date: 04/25/2019
helpviewer_keywords:
- using lightweight tasks [Concurrency Runtime]
- lightweight tasks, using [Concurrency Runtime]
ms.assetid: 1edfe818-d274-46de-bdd3-e92967c9bbe0
ms.openlocfilehash: 7ce18b54835b2380d3baee77b00a670351e3279f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224911"
---
# <a name="walkthrough-adapting-existing-code-to-use-lightweight-tasks"></a>演练：调整现有代码以使用轻量级任务

本主题演示如何调整使用 Windows API 的现有代码，以创建和执行线程以使用轻量级任务。

*轻量级任务*是从[concurrency：：](../../parallel/concrt/reference/scheduler-class.md) schedule 或[concurrency：： ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md)对象直接计划的任务。 当改编现有代码以使用并发运行时的计划功能时，轻量级任务非常有用。

## <a name="prerequisites"></a>必备条件

在开始本演练之前，请阅读[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)主题。

## <a name="example"></a>示例

下面的示例演示了 Windows API 用于创建和执行线程的典型用法。 此示例使用[CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)函数 `MyThreadFunction` 在单独的线程上调用。

### <a name="initial-code"></a>初始代码

[!code-cpp[concrt-windows-threads#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_1.cpp)]

本示例生成以下输出。

```Output
Parameters = 50, 100
```

以下步骤演示如何调整代码示例，以使用并发运行时执行相同的任务。

### <a name="to-adapt-the-example-to-use-a-lightweight-task"></a>改编示例以使用轻量级任务

1. 添加 `#include` 标头文件 concrt 的指令。

[!code-cpp[concrt-migration-lwt#2](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_2.cpp)]

1. **`using`** 为命名空间添加指令 `concurrency` 。

[!code-cpp[concrt-migration-lwt#3](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_3.cpp)]

1. 更改的声明 `MyThreadFunction` 以使用 **`__cdecl`** 调用约定并返回 **`void`** 。

[!code-cpp[concrt-migration-lwt#4](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_4.cpp)]

1. 修改 `MyData` 结构，使之包含[concurrency：： event](../../parallel/concrt/reference/event-class.md)对象，该对象指示任务已完成的主应用程序。

[!code-cpp[concrt-migration-lwt#5](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_5.cpp)]

1. `CreateThread`使用对[concurrency：： CurrentScheduler：： ScheduleTask](reference/currentscheduler-class.md#scheduletask)方法的调用替换对的调用。

[!code-cpp[concrt-migration-lwt#6](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_6.cpp)]

1. `WaitForSingleObject`使用对[concurrency：： event：： wait](reference/event-class.md#wait)方法的调用替换对的调用，以等待任务完成。

[!code-cpp[concrt-migration-lwt#7](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_7.cpp)]

1. 删除对的调用 `CloseHandle` 。

1. 将的定义的签名更改 `MyThreadFunction` 为与步骤3匹配。

[!code-cpp[concrt-migration-lwt#8](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_8.cpp)]

1. 在函数的末尾 `MyThreadFunction` ，调用[concurrency：： event：： set](reference/event-class.md#set)方法以向主应用程序发出任务已完成的信号。

[!code-cpp[concrt-migration-lwt#9](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_9.cpp)]

1. **`return`** 从中删除语句 `MyThreadFunction` 。

### <a name="completed-code"></a>已完成代码

下面的已完成示例显示使用轻量级任务调用函数的代码 `MyThreadFunction` 。

[!code-cpp[concrt-migration-lwt#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_10.cpp)]

## <a name="see-also"></a>另请参阅

[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[计划程序类](../../parallel/concrt/reference/scheduler-class.md)
