---
title: "如何：指定特定的计划程序策略 | Microsoft Docs"
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
  - "指定计划程序策略 [并发运行时]"
  - "计划程序策略, 指定 [并发运行时]"
ms.assetid: 9c5149f9-ac34-4ff3-9e79-0bad103e4e6b
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# 如何：指定特定的计划程序策略
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计划程序策略让你能够控制的计划程序使用在管理任务时的策略。 本主题演示如何使用计划程序策略来打印到控制台进度指示器的任务的线程优先级提高。  
  
 有关自定义计划程序策略与异步代理一起使用的示例，请参阅 [如何︰ 创建该使用特定计划程序策略的代理](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)。  
  
## <a name="example"></a>示例  
 下面的示例并行执行两项任务。 第一项任务计算 n<sup>th</sup> 斐波纳契数。 第二个任务将打印到控制台进度指示器。  
  
 第一项任务使用递归分解计算斐波纳契数。 也就是说，每个任务以递归方式创建多个子任务计算的总体结果。 使用递归分解的任务可能会用尽所有可用的资源，并从而枯竭其他任务。 在此示例中，输出的进度指示器的任务可能无法收到及时对计算资源的访问权。  
  
 若要提供输出的计算资源的进度消息公平访问的任务，此示例使用中所述的步骤 [如何︰ 管理计划程序实例](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) 来创建具有自定义策略的计划程序实例。 自定义策略中指定的线程优先级最高的优先级类。  
  
 此示例使用 [concurrency:: call](../../parallel/concrt/reference/call-class.md) 和 [concurrency:: timer](../../parallel/concrt/reference/timer-class.md) 类要打印的进度指示器。 这些类都包含引用其构造函数的版本 [concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md) 安排这些对象。 该示例使用默认计划程序来计划计算斐波纳契数以及要计划的任务输出进度指示器的计划程序实例的任务。  
  
 为了说明使用具有自定义策略的计划程序的优势，此示例执行整个任务两次。 该示例首先使用默认计划程序计划这两项任务。 然后，该示例使用默认计划程序安排第一个任务，并具有计划第二个任务的自定义策略的计划程序。  
  
 [!CODE [concrt-scheduler-policy#1](../CodeSnippet/VS_Snippets_ConcRT/concrt-scheduler-policy#1)]  
  
 本示例生成以下输出。  
  
```Output  
Default scheduler:  
...........................................................................done  
Scheduler that has a custom policy:  
...........................................................................done  
```  
  
 虽然这两组任务产生相同的结果，但使用自定义策略的版本将使输出的进度指示器，以便它响应能力更强的行为，在提升的优先级别运行的任务。  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到名为 `scheduler-policy.cpp` ，然后在 Visual Studio 命令提示窗口中运行以下命令。  
  
 **cl.exe /EHsc 计划程序-policy.cpp**  
  
## <a name="see-also"></a>另请参阅  
 [计划程序策略](../../parallel/concrt/scheduler-policies.md)   
 [如何︰ 管理计划程序实例](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)   
 [如何︰ 创建使用特定计划程序策略的代理](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)

