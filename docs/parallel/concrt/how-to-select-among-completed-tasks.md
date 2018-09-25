---
title: 如何： 在已完成的任务之间选择 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- selecting among completed tasks [Concurrency Runtime]
- completed tasks, selecting among [Concurrency Runtime]
ms.assetid: c8ccc160-043f-4599-847b-32ed270bb257
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c458ab708af738d181bd720085c8cf533652d2a6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436047"
---
# <a name="how-to-select-among-completed-tasks"></a>如何：在已完成的任务之间选择

此示例演示如何使用[concurrency:: choice](../../parallel/concrt/reference/choice-class.md)并[concurrency:: join](../../parallel/concrt/reference/join-class.md)类选择第一个任务完成搜索算法。

## <a name="example"></a>示例

下面的示例以并行执行两种搜索算法，并选择要完成的第一个算法。 此示例定义`employee`类型，它持有的某位员工的数字标识符和薪金。 `find_employee`函数查找第一个具有所提供的标识符或提供的薪水的员工。 `find_employee`函数还可以处理具有情况下，任何员工提供的标识符或薪金。 `wmain`函数创建的数组`employee`对象和搜索多个标识符和薪金值。

该示例使用`choice`对象之间在以下情况下进行选择：

1. 存在具有提供的标识符的员工。

1. 存在具有提供的薪水的员工。

1. 存在具有提供的标识符或薪金没有员工。

对于前两个情况下，该示例使用[3&gt;concurrency::single_assignment&lt;3}](../../parallel/concrt/reference/single-assignment-class.md)对象以保存该标识符，另一个`single_assignment`对象以保存薪金。 该示例使用`join`第三个用例的对象。 `join`对象包含两个额外`single_assignment`对象，其中没有员工具有所提供的标识符存在，这种情况和在没有员工具有提供的薪水存在这种情况。 `join`对象将发送一条消息，当收到消息时，其每个成员。 在此示例中，`join`对象发送消息时没有员工具有所提供的标识符或薪水。

该示例使用[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)对象来并行运行这两种搜索算法。 每个搜索任务写入一个`single_assignment`对象，来指示是否存在给定的员工。 该示例使用[concurrency:: receive](reference/concurrency-namespace-functions.md#receive)函数获取包含一条消息的第一个缓冲区的索引和一个`switch`块来输出结果。

[!code-cpp[concrt-find-employee#1](../../parallel/concrt/codesnippet/cpp/how-to-select-among-completed-tasks_1.cpp)]

本示例生成以下输出。

```Output
Employee with id 14758 has salary 27780.00.
Employee with salary 29150.00 has id 84345.
Employee with id 61935 has salary 29905.00.
No employee has id 899 or salary 31223.00.
```

此示例使用[concurrency::make_choice](reference/concurrency-namespace-functions.md#make_choice)帮助器函数来创建`choice`对象和[concurrency::make_join](reference/concurrency-namespace-functions.md#make_join)帮助器函数来创建`join`对象。

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`find-employee.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc 查找 employee.cpp**

## <a name="see-also"></a>请参阅

[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[消息传递函数](../../parallel/concrt/message-passing-functions.md)<br/>
[choice 类](../../parallel/concrt/reference/choice-class.md)<br/>
[join 类](../../parallel/concrt/reference/join-class.md)
