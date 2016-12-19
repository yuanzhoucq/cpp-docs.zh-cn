---
title: "演练：调整现有代码以使用轻量级任务 | Microsoft Docs"
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
  - "使用轻量级任务 [并发运行时]"
  - "轻量级任务, 使用 [并发运行时]"
ms.assetid: 1edfe818-d274-46de-bdd3-e92967c9bbe0
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：调整现有代码以使用轻量级任务
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题演示如何改编现有代码，从而使用 Windows API 创建并执行一个线程来使用轻量级任务。  
  
 *轻量级任务*是直接根据 [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) 或 [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) 对象计划的任务。  改编现有代码以使用并发运行时的日程排定功能时，轻量级任务很有用。  
  
## 系统必备  
 在开始本演练之前，请阅读[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)这一主题。  
  
## 示例  
  
### 说明  
 下面的示例阐释了使用 Windows API 创建和执行线程的典型方法。  此示例使用 [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) 函数对单独线程调用 `MyThreadFunction`。  
  
### 代码  
 [!code-cpp[concrt-windows-threads#1](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_1.cpp)]  
  
### 注释  
 该示例产生下面的输出。  
  
  **参数 \= 50, 100** 下列步骤演示如何调整代码示例以使用并发运行时执行相同任务。  
  
### 调整示例以使用轻量级任务  
  
1.  为头文件 concrt.h 添加一个 `#include` 指令。  
  
     [!code-cpp[concrt-migration-lwt#2](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_2.cpp)]  
  
2.  为`concurrency`命名空间添加 `using` 指令。  
  
     [!code-cpp[concrt-migration-lwt#3](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_3.cpp)]  
  
3.  更改 `MyThreadFunction` 的声明以使用 `__cdecl` 调用约定并返回 `void`。  
  
     [!code-cpp[concrt-migration-lwt#4](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_4.cpp)]  
  
4.  修改 `MyData` 结构以包括向任务已完成的主应用程序发送信号的 [concurrency::event](../../parallel/concrt/reference/event-class.md) 对象。  
  
     [!code-cpp[concrt-migration-lwt#5](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_5.cpp)]  
  
5.  不调用 `CreateThread`，改为调用 [concurrency::CurrentScheduler::ScheduleTask](../Topic/CurrentScheduler::ScheduleTask%20Method.md) 方法。  
  
     [!code-cpp[concrt-migration-lwt#6](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_6.cpp)]  
  
6.  不调用 `WaitForSingleObject`，改为调用 [concurrency::event::wait](../Topic/event::wait%20Method.md) 方法以等待任务完成。  
  
     [!code-cpp[concrt-migration-lwt#7](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_7.cpp)]  
  
7.  移除对 `CloseHandle` 的调用。  
  
8.  更改 `MyThreadFunction` 定义的签名以与步骤 3 匹配。  
  
     [!code-cpp[concrt-migration-lwt#8](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_8.cpp)]  
  
9. 在 `MyThreadFunction` 函数的末尾，调用 [concurrency::event::set](../Topic/event::set%20Method.md) 方法以向任务已完成的主应用程序发送信号。  
  
     [!code-cpp[concrt-migration-lwt#9](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_9.cpp)]  
  
10. 从 `MyThreadFunction` 中移除 `return` 语句。  
  
## 示例  
  
### 说明  
 下面已完成的示例演示了使用轻量级任务调用 `MyThreadFunction` 函数的代码。  
  
### 代码  
 [!code-cpp[concrt-migration-lwt#1](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_10.cpp)]  
  
### 注释  
  
## 请参阅  
 [任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Scheduler 类](../../parallel/concrt/reference/scheduler-class.md)