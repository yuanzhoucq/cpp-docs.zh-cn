---
title: "演练： 调整现有代码以使用轻量级任务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- using lightweight tasks [Concurrency Runtime]
- lightweight tasks, using [Concurrency Runtime]
ms.assetid: 1edfe818-d274-46de-bdd3-e92967c9bbe0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8a50ad04421d7b4bcdc4a2c98de8f5a57b255c75
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-adapting-existing-code-to-use-lightweight-tasks"></a>演练：调整现有代码以使用轻量级任务
本主题演示如何改编现有代码，它使用 Windows API 创建和执行一个线程以使用轻量级任务。  
  
 A*轻量级任务*是直接从计划的任务[concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)或[concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md)对象。 当改编现有代码以使用并发运行时的计划功能时，轻量级任务非常有用。  
  
## <a name="prerequisites"></a>系统必备  
 在开始本演练之前，请阅读主题[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例阐释了要创建和执行线程的 Windows api 的典型用法。 此示例使用[CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453)函数调用`MyThreadFunction`在单独线程上。  
  
### <a name="code"></a>代码  
 [!code-cpp[concrt-windows-threads#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_1.cpp)]  
  
### <a name="comments"></a>注释  
 本示例生成以下输出。  
  
```Output  
Parameters = 50, 100  
```  
  
 以下步骤演示如何改编代码示例以使用并发运行时执行相同的任务。  
  
### <a name="to-adapt-the-example-to-use-a-lightweight-task"></a>若要调整该示例以使用轻量级任务  
  
1.  添加`#include`标头文件 concrt.h 指令。  
  
 [!code-cpp[concrt-migration-lwt#2](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_2.cpp)]  
  
2.  添加`using`指令`concurrency`命名空间。  
  
 [!code-cpp[concrt-migration-lwt#3](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_3.cpp)]  
  
3.  更改的声明`MyThreadFunction`使用`__cdecl`调用约定，并返回`void`。  
  
 [!code-cpp[concrt-migration-lwt#4](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_4.cpp)]  
  
4.  修改`MyData`结构以包含[concurrency:: event](../../parallel/concrt/reference/event-class.md)向发出信号，主应用程序任务已完成的对象。  
  
 [!code-cpp[concrt-migration-lwt#5](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_5.cpp)]  
  
5.  将对的调用`CreateThread`通过调用[:: scheduletask](reference/currentscheduler-class.md#scheduletask)方法。  

  
 [!code-cpp[concrt-migration-lwt#6](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_6.cpp)]  
  

6.  将对的调用`WaitForSingleObject`通过调用[concurrency::event::wait](reference/event-class.md#wait)方法来等待任务完成。  

 [!code-cpp[concrt-migration-lwt#7](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_7.cpp)]  
  
7.  删除对的调用`CloseHandle`。  
  
8.  更改的定义的签名`MyThreadFunction`以匹配第 3 步。  
  
 [!code-cpp[concrt-migration-lwt#8](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_8.cpp)]  
  
9. 在结束`MyThreadFunction`函数中，调用[concurrency::event::set](reference/event-class.md#set)方法用信号通知到主应用程序任务已完成。  
  
 [!code-cpp[concrt-migration-lwt#9](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_9.cpp)]  
  
10. 删除`return`语句从`MyThreadFunction`。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的已完成的示例演示使用轻量级任务调用的代码`MyThreadFunction`函数。  
  
### <a name="code"></a>代码  
 [!code-cpp[concrt-migration-lwt#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_10.cpp)]  
  
### <a name="comments"></a>注释  
  
## <a name="see-also"></a>请参阅  
 [任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Scheduler 类](../../parallel/concrt/reference/scheduler-class.md)
