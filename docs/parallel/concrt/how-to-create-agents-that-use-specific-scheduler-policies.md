---
title: "如何：创建使用特定计划程序策略的代理 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "计划程序策略, 代理 [并发运行时]"
  - "创建使用特定策略的代理 [并发运行时]"
ms.assetid: 46a3e265-0777-4ec3-a142-967bafc49d67
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 如何：创建使用特定计划程序策略的代理
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

代理是以异步方式与其他组件一起解决更大的计算任务的应用程序组件。  代理通常具有已设置的生命周期并且会维护状态。  
  
 每个代理都可能具有独特的应用程序要求。  例如，启用用户交互（检索输入或显示输出）的代理在访问计算资源时可能需要较高的优先级别。  利用计划程序策略，可以控制计划程序在管理任务时使用的策略。  本主题演示如何创建使用特定计划程序策略的代理。  
  
 有关将自定义计划程序策略与异步消息块一起使用的基本示例，请参见[如何：指定特定的计划程序策略](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)。  
  
 本主题使用异步代理库中的功能（如代理、消息块和消息传递函数）执行工作。  有关异步代理库的更多信息，请参见[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)。  
  
## 示例  
 下面的示例定义了派生自 [concurrency::agent](../../parallel/concrt/reference/agent-class.md) 的两个类：`permutor` 和 `printer`。  `permutor` 类计算给定输入字符串的所有排列。  `printer` 类将进度消息打印到控制台。  `permutor` 类执行可能会使用所有可用计算资源的计算密集型操作。  `printer` 类必须及时打印每条进度消息才会有用。  
  
 为了向 `printer` 类提供对计算资源的公平访问权，此示例使用[如何：管理计划程序实例](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)中描述的步骤创建了一个具有自定义策略的计划程序实例。  自定义策略将线程优先级别指定为最高优先级别类。  
  
 为了说明使用具有自定义策略的计划程序的好处，此示例将整个任务执行两次。  此示例首先使用默认计划程序安排这两项任务，  然后使用默认计划程序安排 `permutor` 对象，并使用具有自定义策略的计划程序安排 `printer` 对象。  
  
 [!code-cpp[concrt-permute-strings#1](../../parallel/concrt/codesnippet/CPP/how-to-create-agents-that-use-specific-scheduler-policies_1.cpp)]  
  
 该示例产生下面的输出。  
  
  **默认计划程序：**  
**计算“葡萄柚”的所有排列…**  
**100% 完成...**  
**使用更高优先级别的上下文：**  
**计算“葡萄柚”的所有排列…**  
**100% 完成...** 虽然这两组任务产生的结果相同，但使用自定义策略的版本可使 `printer` 对象能够按照提升的优先级别运行，以使其行为的响应能力更强。  
  
## 编译代码  
 复制代码示例，并将此代码粘贴到 Visual Studio项目中或一个名为  `permute-strings.cpp` 的文件中，然后在 Visual Studio命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc permute\-strings.cpp**  
  
## 请参阅  
 [计划程序策略](../../parallel/concrt/scheduler-policies.md)   
 [异步代理](../../parallel/concrt/asynchronous-agents.md)   
 