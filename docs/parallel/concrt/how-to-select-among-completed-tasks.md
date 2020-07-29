---
title: 如何：在已完成的任务之间选择
ms.date: 11/04/2016
helpviewer_keywords:
- selecting among completed tasks [Concurrency Runtime]
- completed tasks, selecting among [Concurrency Runtime]
ms.assetid: c8ccc160-043f-4599-847b-32ed270bb257
ms.openlocfilehash: fd9940dad0cd2f202bdc734a81a7eb37cd79420c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226719"
---
# <a name="how-to-select-among-completed-tasks"></a>如何：在已完成的任务之间选择

此示例演示如何使用[concurrency：： choice](../../parallel/concrt/reference/choice-class.md)和[concurrency：： join](../../parallel/concrt/reference/join-class.md)类选择完成搜索算法的第一个任务。

## <a name="example"></a>示例

下面的示例并行执行两个搜索算法，并选择要完成的第一个算法。 此示例定义 `employee` 类型，该类型保存雇员的数值标识符和薪金。 `find_employee`函数查找具有提供的标识符或提供的薪水的第一个雇员。 `find_employee`函数还处理没有员工提供的标识符或薪金的情况。 `wmain`函数创建对象的数组 `employee` ，并搜索多个标识符和薪金值。

该示例使用 `choice` 对象在下列情况下进行选择：

1. 存在具有提供的标识符的员工。

1. 存在具有所提供薪金的员工。

1. 不存在具有所提供的标识符或薪水的员工。

对于前两种情况，该示例使用[concurrency：： single_assignment](../../parallel/concrt/reference/single-assignment-class.md)对象来保存标识符，并使用另一个 `single_assignment` 对象来保存薪金。 该示例使用 `join` 第三种情况的对象。 此 `join` 对象由两个附加 `single_assignment` 对象组成，一个用于没有具有提供的标识符的员工，一个用于没有具有提供的薪水的员工。 `join`当对象的每个成员收到消息时，对象将发送一条消息。 在此示例中， `join` 如果不存在具有提供的标识符或薪水的员工，则对象将发送一条消息。

该示例使用[concurrency：： structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)对象并行运行两个搜索算法。 每个搜索任务都将写入一个 `single_assignment` 对象，以指示给定的雇员是否存在。 该示例使用[concurrency：： receive](reference/concurrency-namespace-functions.md#receive)函数获取第一个缓冲区的索引，该缓冲区包含 **`switch`** 用于打印结果的消息和块。

[!code-cpp[concrt-find-employee#1](../../parallel/concrt/codesnippet/cpp/how-to-select-among-completed-tasks_1.cpp)]

本示例生成以下输出。

```Output
Employee with id 14758 has salary 27780.00.
Employee with salary 29150.00 has id 84345.
Employee with id 61935 has salary 29905.00.
No employee has id 899 or salary 31223.00.
```

此示例使用[concurrency：： make_choice](reference/concurrency-namespace-functions.md#make_choice) helper 函数创建 `choice` 对象，使用[concurrency：： make_join](reference/concurrency-namespace-functions.md#make_join) helper 函数创建 `join` 对象。

## <a name="compiling-the-code"></a>编译代码

复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为的文件中， `find-employee.cpp` 然后在 Visual Studio 命令提示符窗口中运行以下命令。

> **cl.exe/EHsc find-employee**

## <a name="see-also"></a>另请参阅

[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[消息传递函数](../../parallel/concrt/message-passing-functions.md)<br/>
[choice 类](../../parallel/concrt/reference/choice-class.md)<br/>
[联接类](../../parallel/concrt/reference/join-class.md)
