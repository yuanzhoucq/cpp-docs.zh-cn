---
title: "如何：在已完成的任务之间选择 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "在已完成的任务中选择 [并发运行时]"
  - "已完成的任务，在 [并发运行时] 中选择"
ms.assetid: c8ccc160-043f-4599-847b-32ed270bb257
caps.latest.revision: 17
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：在已完成的任务之间选择
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本示例演示如何使用 [concurrency::choice](../../parallel/concrt/reference/choice-class.md) 和 [concurrency::join](../../parallel/concrt/reference/join-class.md) 类选择用于完成搜索算法的第一个任务。  
  
## 示例  
 下面的示例以并行方式执行两个搜索算法，并选择第一个算法来完成。  该示例定义了保存员工的数字标识符和薪水的 `employee` 类型。  `find_employee` 函数会查找第一个具有提供的标识符或薪水的员工。  `find_employee` 函数还处理没有员工具有提供的标识符或薪水的情况。  `wmain` 函数创建一个 `employee` 对象数组，并搜索若干标识符和薪水值。  
  
 该示例使用 `choice` 对象在以下情况之间进行选择：  
  
1.  存在一个具有提供的标识符的员工。  
  
2.  存在一个具有提供的薪水的员工。  
  
3.  没有员工具有提供的标识符或薪水。  
  
 对于前两种情况，该示例使用 [concurrency::single\_assignment](../../parallel/concrt/reference/single-assignment-class.md) 对象保存标识符，使用另一个 `single_assignment` 对象保存薪水。  该示例对第三种情况使用 `join` 对象。  `join` 对象由两个附加 `single_assignment` 对象组成，一个用于没有员工具有提供的标识符的情况，一个用于没有员工具有提供的薪水的情况。  `join` 对象在其每个成员收到一条消息时发送一条消息。  在该示例中，`join` 对象在没有员工具有提供的标识符或薪水时发送一条消息。  
  
 该示例使用 [concurrency::structured\_task\_group](../../parallel/concrt/reference/structured-task-group-class.md) 对象并行运行这两个搜索算法。  每个搜索任务写入一个 `single_assignment` 对象，以指示是否存在给定的员工。  该示例使用 [concurrency::receive](../Topic/receive%20Function.md) 函数获取第一个缓冲区的索引，该缓冲区包含用于输出结果的消息和 `switch` 块。  
  
 [!code-cpp[concrt-find-employee#1](../../parallel/concrt/codesnippet/CPP/how-to-select-among-completed-tasks_1.cpp)]  
  
 该示例产生下面的输出。  
  
  **ID为 14758 的雇员工资为 27780.00。**  
**ID为 29150.00 的雇员工资为 84345。**  
**ID为 61935 的雇员工资为 29905.00。**  
**没有员工的 ID为 899 或薪水为31223.00。** 该示例使用 [concurrency::make\_choice](../Topic/make_choice%20Function.md) helper 函数创建 `choice` 对象，使用 [concurrency::make\_join](../Topic/make_join%20Function.md) helper 函数创建 `join` 对象。  
  
## 编译代码  
 复制代码示例，再将此代码粘贴到Visual Studio 项目中或一个名为`find-employee.cpp` 的文件中，然后在Visual Studio命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc find\-employee.cpp**  
  
## 请参阅  
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)   
 [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)   
 [消息传递函数](../../parallel/concrt/message-passing-functions.md)   
 [choice 类](../../parallel/concrt/reference/choice-class.md)   
 [join 类](../../parallel/concrt/reference/join-class.md)