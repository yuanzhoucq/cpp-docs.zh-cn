---
title: 如何： 在已完成的任务之间选择 |Microsoft 文档
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
ms.openlocfilehash: a485eb87f2caa62a382983c1cda2b9c098742d42
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687109"
---
# <a name="how-to-select-among-completed-tasks"></a>如何：在已完成的任务之间选择
此示例演示如何使用[concurrency:: choice](../../parallel/concrt/reference/choice-class.md)和[concurrency:: join](../../parallel/concrt/reference/join-class.md)类选择用于完成搜索算法的第一个任务。  
  
## <a name="example"></a>示例  
 下面的示例以并行方式执行这两种搜索算法，并选择要完成的第一个算法。 此示例定义`employee`类型，包含一个数字标识符和薪水员工。 `find_employee`函数查找第一个具有所提供的标识符或提供的薪水的员工。 `find_employee`函数还可以处理其中没有员工具有提供的标识符或薪金这种情况。 `wmain`函数创建的数组`employee`对象和搜索多个标识符和薪水值。  
  
 该示例使用`choice`对象之间以下情况下进行选择：  
  
1.  存在具有提供的标识符的员工。  
  
2.  存在具有提供的薪水的员工。  
  
3.  存在具有提供的标识符或薪金没有员工。  
  
 前两个情况下，为此示例使用[concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md)对象以保存该标识符，另一个`single_assignment`对象以保存工资。 该示例使用`join`为第三个用例的对象。 `join`对象组成的两个额外`single_assignment`对象，其中没有员工具有所提供的标识符存在，这种情况和在没有员工具有提供的薪水存在这种情况。 `join`对象发送一条消息，当收到消息时，其每个成员。 在此示例中，`join`对象发送消息时没有员工具有所提供的标识符或薪水。  
  
 该示例使用[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)能够并行运行这两种搜索算法的对象。 每个搜索任务写入一个`single_assignment`对象，以指示是否存在给定的员工。 该示例使用[concurrency:: receive](reference/concurrency-namespace-functions.md#receive)函数来获取第一个包含一条消息的缓冲区的索引和`switch`块来输出结果。  
  
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
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`find-employee.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc 查找 employee.cpp**  
  
## <a name="see-also"></a>请参阅  
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)   
 [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)   
 [消息传递函数](../../parallel/concrt/message-passing-functions.md)   
 [choice 类](../../parallel/concrt/reference/choice-class.md)   
 [join 类](../../parallel/concrt/reference/join-class.md)
