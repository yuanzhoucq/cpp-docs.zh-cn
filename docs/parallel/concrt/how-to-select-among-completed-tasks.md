---
title: 如何：在已完成的任务之间选择
ms.date: 11/04/2016
helpviewer_keywords:
- selecting among completed tasks [Concurrency Runtime]
- completed tasks, selecting among [Concurrency Runtime]
ms.assetid: c8ccc160-043f-4599-847b-32ed270bb257
ms.openlocfilehash: 75ecac8dd0e8845401e3e287e8c95ea614055970
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142476"
---
# <a name="how-to-select-among-completed-tasks"></a>如何：在已完成的任务之间选择

此示例演示如何使用[concurrency：： choice](../../parallel/concrt/reference/choice-class.md)和[concurrency：： join](../../parallel/concrt/reference/join-class.md)类选择完成搜索算法的第一个任务。

## <a name="example"></a>示例

下面的示例并行执行两个搜索算法，并选择要完成的第一个算法。 此示例定义 `employee` 类型，该类型保存雇员的数值标识符和薪金。 `find_employee` 函数查找第一个具有提供的标识符或提供的薪水的雇员。 `find_employee` 函数还可处理没有员工提供的标识符或薪金的情况。 `wmain` 函数创建 `employee` 对象的数组，并搜索多个标识符和薪金值。

该示例使用 `choice` 对象在下列情况下进行选择：

1. 存在具有提供的标识符的员工。

1. 存在具有所提供薪金的员工。

1. 不存在具有所提供的标识符或薪水的员工。

在前两种情况下，该示例使用[concurrency：： single_assignment](../../parallel/concrt/reference/single-assignment-class.md)对象保存标识符，使用另一个 `single_assignment` 对象保存薪金。 该示例使用第三种情况下的 `join` 对象。 `join` 对象包含两个附加的 `single_assignment` 对象，一个对象用于不存在具有提供的标识符的员工，另一个用于没有具有提供的薪水的员工。 当对象的每个成员收到消息时，`join` 对象将发送一条消息。 在此示例中，如果不存在具有提供的标识符或薪水的员工，则 `join` 对象将发送一条消息。

该示例使用[concurrency：： structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)对象并行运行两个搜索算法。 每个搜索任务都写入其中一个 `single_assignment` 对象，以指示给定的雇员是否存在。 该示例使用[concurrency：： receive](reference/concurrency-namespace-functions.md#receive)函数获取第一个缓冲区的索引，该缓冲区包含一条消息和一个 `switch` 块以打印结果。

[!code-cpp[concrt-find-employee#1](../../parallel/concrt/codesnippet/cpp/how-to-select-among-completed-tasks_1.cpp)]

本示例生成以下输出。

```Output
Employee with id 14758 has salary 27780.00.
Employee with salary 29150.00 has id 84345.
Employee with id 61935 has salary 29905.00.
No employee has id 899 or salary 31223.00.
```

此示例使用[concurrency：： make_choice](reference/concurrency-namespace-functions.md#make_choice) helper 函数创建 `choice` 对象，并使用[concurrency：： make_join](reference/concurrency-namespace-functions.md#make_join) helper 函数创建 `join` 对象。

## <a name="compiling-the-code"></a>编译代码

复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为 `find-employee.cpp` 的文件中，然后在 Visual Studio 命令提示符窗口中运行以下命令。

> **cl/EHsc find-employee**

## <a name="see-also"></a>另请参阅

[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[消息传递函数](../../parallel/concrt/message-passing-functions.md)<br/>
[choice 类](../../parallel/concrt/reference/choice-class.md)<br/>
[join 类](../../parallel/concrt/reference/join-class.md)
