---
title: "并发运行时中的异常处理 | Microsoft Docs"
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
  - "轻量级任务, 异常处理 [并发运行时]"
  - "异常处理 [并发运行时]"
  - "结构化任务组, 异常处理 [并发运行时]"
  - "代理, 异常处理 [并发运行时]"
  - "任务组, 异常处理 [并发运行时]"
ms.assetid: 4d1494fb-3089-4f4b-8cfb-712aa67d7a7a
caps.latest.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# 并发运行时中的异常处理
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

并发运行时使用 C\+\+ 异常处理来告知多种错误。  这些错误包括使用的运行时无效、诸如无法获取资源之类的运行时错误，以及发生在提供给任务和任务组的工作函数中的错误。  当任务或任务组引发异常时，运行时将保存该异常，并将其封送到等待任务或任务组完成的上下文。  对于诸如轻量级任务和代理之类的组件，运行时不会为您管理异常。  在这些情况下，您必须实现自己的异常处理机制。  本主题描述运行时如何处理任务、任务组、轻量级任务和异步代理引发的异常，以及如何在应用程序中响应异常。  
  
## 关键点  
  
-   当任务或任务组引发异常时，运行时将保存该异常，并将其封送到等待任务或任务组完成的上下文。  
  
-   如果可能，请包含每调用 [concurrency::task::get](../Topic/task::get%20Method.md) 和 [concurrency::task::wait](../Topic/task::wait%20Method.md) 使用 `try`\/`catch` 块处理可恢复的错误。  运行时终止应用，则任务引发异常，该异常不会被捕捉，延续任务之一或主应用。  
  
-   基于任务的延续始终运行；非关键成功完成前面的任务，是否引发了异常，也未取消。  如果前面的任务引发或移除，基于值的延续将不运行。  
  
-   由于基于任务的延续始终运行，则考虑添加基于任务的延续在继续字符串结尾。  这有助于确保代码观察到所有异常。  
  
-   运行时引发 [concurrency::task\_canceled](../../parallel/concrt/reference/task-canceled-class.md)，当调用 [concurrency::task::get](../Topic/task::get%20Method.md) 时，该任务将取消。  
  
-   运行时不会管理轻量级任务和代理之类的异常。  
  
##  <a name="top"></a> 在本文档中  
  
-   [任务和继续](#tasks)  
  
-   [任务组和并行算法](#task_groups)  
  
-   [运行时引发的异常](#runtime)  
  
-   [多个异常](#multiple)  
  
-   [取消](#cancellation)  
  
-   [轻量级任务](#lwts)  
  
-   [异步代理](#agents)  
  
##  <a name="tasks"></a> 任务和继续  
 本节描述运行时如何处理由 [concurrency::task](../../parallel/concrt/reference/task-class-concurrency-runtime.md) 对象及其延续引发的异常。  有关任务和继续模型的更多信息，请参见[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
 当您在传递给`task` 对象的工作函数体中引发异常时，运行时存储该异常，并将该异常封送到调用[concurrency::task::get](../Topic/task::get%20Method.md)或[concurrency::task::wait](../Topic/task::wait%20Method.md)的上下文。  [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md) 文档描述基于任务与基于的值，继续，汇总，但基于值继续接受类型 `T` 的参数，并根据任务中继续一个采用 `task<T>`类型的参数。  如果引发的任务具有一个或多个基于值的后续，这些延续不计划运行。  下面的示例阐释了这一点：  
  
 [!CODE [concrt-eh-task#1](../CodeSnippet/VS_Snippets_ConcRT/concrt-eh-task#1)]  
  
 基于任务的延续可以处理由前面的任务引发的任何异常。  基于任务的延续始终运行；非关键成功完成的任务，是否引发了异常，也未取消。  当任务引发异常时，它基于任务的计划继续运行。  下面的示例演示引发始终的任务。  有两个任务继续；一个值，此文件基于并其他任务开始。  基于任务的 Exception 始终运行，可以捕获由前面的任务引发的异常。  当两继续示例等待完成后，再次引发某个异常，这是因为任务异常始终引发，当调用 `task::get` 或 `task::wait` 时。  
  
 [!code-cpp[concrt-eh-continuations#1](../../parallel/concrt/codesnippet/CPP/exception-handling-in-the-concurrency-runtime_1.cpp)]  
  
 建议使用基于任务延续的异常捕捉您要处理的文件。  由于基于任务的延续始终运行，则考虑添加基于任务的延续在继续字符串结尾。  这有助于确保代码观察到所有异常。  下面的示例演示一个简单的基于的值继续字符串。  链中引发的第三项任务，并且其后的任何基于值的延续将不会运行。  但是，在最终延续任务开始，并始终运行。  此最终继续由第三个任务引发的异常。  
  
 建议捕捉您的最特定的异常。  如果没有捕获特定的异常，则可以忽略此最终基于任务中继续。  所有异常都将保持未处理并且可以终止应用。  
  
 [!code-cpp[concrt-eh-task-chain#1](../../parallel/concrt/codesnippet/CPP/exception-handling-in-the-concurrency-runtime_2.cpp)]  
  
> [!TIP]
>  可以使用 [concurrency::task\_completion\_event::set\_exception](../../parallel/concrt/reference/task-completion-event-class.md) 方法关联的异常处理任务完成事件。  文档 [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md) 更详细地介绍。[concurrency::task\_completion\_event](../../parallel/concrt/reference/task-completion-event-class.md) 类。  
  
 [concurrency::task\_canceled](../../parallel/concrt/reference/task-canceled-class.md) 是与 `task`的一个重要运行时异常类型。  运行时引发 `task_canceled`，当您调用 `task::get` 时，取消该任务。\(反之，[task\_status::canceled](../Topic/task_group_status%20Enumeration.md) `task::wait` 返回，且不会引发。\)您可以捕获和处理从基于任务的延续的此异常时，或者当调用 `task::get`。  有关任务取消的更多信息，请参见 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)。  
  
> [!CAUTION]
>  请勿从代码抛出 `task_canceled`。  调用 [concurrency::cancel\_current\_task](../Topic/cancel_current_task%20Function.md)。  
  
 运行时终止应用，则任务引发异常，该异常不会被捕捉，延续任务之一或主应用。  如果应用程序崩溃，可以配置 Visual Studio，在 C\+\+ 异常时中断。  在诊断未经处理的异常的位置后，请使用基于任务的后续处理它。  
  
 文档中的 [运行时引发的异常](#runtime) 一节描述如何更详细地使用运行时异常一起使用。  
  
 \[[Top](#top)\]  
  
##  <a name="task_groups"></a> 任务组和并行算法  
 本节描述运行时如何处理任务组引发的异常。  本节还适用于 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 等并行算法，因为这些算法建立在任务组基础之上。  
  
> [!CAUTION]
>  确保您了解异常对于依赖任务的影响。  有关如何对任务或并行算法使用异常处理的推荐做法，请参见“并行模式库中的最佳做法”主题中的[了解取消和异常处理如何影响对象销毁](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) 一节。  
  
 有关任务组的更多信息，请参见[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  有关并行算法的更多信息，请参见[并行算法](../../parallel/concrt/parallel-algorithms.md)。  
  
 在传递给 [concurrency::task\_group](../Topic/task_group%20Class.md) 或 [concurrency::structured\_task\_group](../../parallel/concrt/reference/structured-task-group-class.md) 对象的工作函数的主体中引发异常时，运行时将存储该异常，并将其封送到调用 [concurrency::task\_group::wait](../Topic/task_group::wait%20Method.md)、[concurrency::structured\_task\_group::wait](../Topic/structured_task_group::wait%20Method.md)、[concurrency::task\_group::run\_and\_wait](../Topic/task_group::run_and_wait%20Method.md) 或 [concurrency::structured\_task\_group::run\_and\_wait](../Topic/structured_task_group::run_and_wait%20Method.md) 的上下文。  运行时还将停止任务组中的所有活动任务（包括子任务组中的任务），并放弃任何尚未开始的任务。  
  
 下面的示例演示了引发异常的工作函数的基本结构。  该示例使用 `task_group` 对象并行打印两个 `point` 对象的值。  `print_point` 工作函数会将 `point` 对象的值打印到控制台。  如果输入值为 `NULL`，则该工作函数将引发异常。  运行时将存储此异常，并将其封送到调用 `task_group::wait` 的上下文。  
  
 [!code-cpp[concrt-eh-task-group#1](../../parallel/concrt/codesnippet/CPP/exception-handling-in-the-concurrency-runtime_3.cpp)]  
  
 该示例产生下面的输出。  
  
  **X \= 15, Y \= 30**  
**捕获的异常：点 NULL。** 有关在任务组中使用异常处理的完整示例，请参阅[如何：使用异常处理中断并行循环](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)。  
  
 \[[Top](#top)\]  
  
##  <a name="runtime"></a> 运行时引发的异常  
 异常可能由调用该运行时。  大多数异常类型，除和 [concurrency::task\_canceled](../../parallel/concrt/reference/task-canceled-class.md) [concurrency::operation\_timed\_out](../../parallel/concrt/reference/operation-timed-out-class.md)，指示程序错误。  由于这些错误通常无法恢复，因此不应由应用程序代码来捕获或处理。  我们建议您在需要诊断编程错误时仅捕获或处理应用程序代码中不可恢复的错误。  但是，了解运行时所定义的异常类型可以帮助您诊断编程错误。  
  
 对于运行时引发的异常以及工作函数引发的异常，异常处理机制是相同的。  例如，如果 [concurrency::receive](../Topic/receive%20Function.md) 函数在指定的时间段内未接收消息，它将引发 `operation_timed_out`。  如果 `receive` 在您传递给任务组的工作函数中引发异常，则运行时将存储该异常，并将其封送到调用 `task_group::wait`、`structured_task_group::wait`、`task_group::run_and_wait` 或 `structured_task_group::run_and_wait` 的上下文。  
  
 下面的示例使用 [concurrency::parallel\_invoke](../Topic/parallel_invoke%20Function.md) 算法以并行方式运行两个任务。  第一个任务等待五秒钟，然后将消息发送到消息缓冲区。  第二个任务使用 `receive` 函数等待三秒钟，以从相同的消息缓冲区中接收消息。  如果 `receive` 函数在该时间段中未收到消息，则它将引发 `operation_timed_out`。  
  
 [!code-cpp[concrt-eh-time-out#1](../../parallel/concrt/codesnippet/CPP/exception-handling-in-the-concurrency-runtime_4.cpp)]  
  
 该示例产生下面的输出。  
  
  **操作超时。** 若要阻止应用程序异常终止，请确保代码在调入运行时的时候对异常进行处理。  此外，在调入使用并发运行时的外部代码（如第三方库）时，也要处理异常。  
  
 \[[Top](#top)\]  
  
##  <a name="multiple"></a> 多个异常  
 如果任务或并行算法收到多个异常，则运行时仅将这些异常之一封送到调用上下文。  运行时不能保证它将封送哪个异常。  
  
 下面的示例使用 `parallel_for` 算法将数字打印到控制台。  如果输入值小于某最小值或大于某最大值，则它将引发异常。  在本示例中，多个工作函数可能会引发异常。  
  
 [!CODE [concrt-eh-multiple#1](../CodeSnippet/VS_Snippets_ConcRT/concrt-eh-multiple#1)]  
  
 以下显示的是此示例的示例输出。  
  
  **8**  
**2**  
**9**  
**3**  
**10**  
**4**  
**5**  
**6**  
**7**  
**捕获的异常：\-5:值大于最小位数小于。** \[[Top](#top)\]  
  
##  <a name="cancellation"></a> 取消  
 不是所有异常都表示错误。  例如，搜索算法在找到结果时可能会使用异常处理来停止其关联任务。  有关如何在代码中使用取消机制的更多信息，请参见 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)。  
  
 \[[Top](#top)\]  
  
##  <a name="lwts"></a> 轻量级任务  
 轻量级任务是直接从 [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) 对象计划的任务。  轻量级任务所需的开销比普通任务小。  但是，轻量级任务引发的异常并不是由运行时来捕获，  而是由未经处理的异常处理程序来捕获，默认情况下该程序会终止进程。  因此，请在应用程序中使用适当的错误处理机制。  有关轻量级任务的更多信息，请参见[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
 \[[Top](#top)\]  
  
##  <a name="agents"></a> 异步代理  
 与轻量级任务相似，运行时不会管理异步代理引发的异常。  
  
 下面的示例演示一种处理派生自 [concurrency::agent](../../parallel/concrt/reference/agent-class.md) 的类中异常的方法。  此示例定义了 `points_agent` 类。  `points_agent::run` 方法将读取消息缓冲区中的 `point` 对象，并将它们打印到控制台。  如果 `run` 方法收到 `NULL` 指针，则它将引发异常。  
  
 `run` 方法会将所有工作包含在 `try`\-`catch` 块中。  `catch` 块将异常存储在消息缓冲区中。  在代理完成之后，应用程序通过从此缓冲区中进行读取来检查代理是否遇到了错误。  
  
 [!CODE [concrt-eh-agents#1](../CodeSnippet/VS_Snippets_ConcRT/concrt-eh-agents#1)]  
  
 该示例产生下面的输出。  
  
  **X: 10 Y: 20**  
**X: 20 Y: 30**  
**代理在错误发生：点无法 NULL**  
**代理的状态为：执行** 因为 `try`\-`catch` 块存在于 `while` 循环之外，所以代理在遇到第一个错误时将终止处理。  如果 `try`\-`catch` 块在 `while` 循环内，则在出错后代理将继续处理。  
  
 本示例将异常存储在消息缓冲区中，以便另一个组件可以在代理运行时监视代理是否出错。  此示例使用 [concurrency::single\_assignment](../../parallel/concrt/reference/single-assignment-class.md) 对象存储错误。  如果代理处理多个异常，则 `single_assignment` 类只存储传递给它的第一条消息。  若要只存储最后一个异常，请使用 [concurrency::overwrite\_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) 类。  若要存储所有异常，请使用 [concurrency::unbounded\_buffer](../Topic/unbounded_buffer%20Class.md) 类。  有关这些消息块的更多信息，请参见[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。  
  
 有关异步代理的更多信息，请参见[异步代理](../../parallel/concrt/asynchronous-agents.md)。  
  
 \[[Top](#top)\]  
  
##  <a name="summary"></a> 摘要  
 \[[Top](#top)\]  
  
## 请参阅  
 [并发运行时](../../parallel/concrt/concurrency-runtime.md)   
 [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [并行算法](../../parallel/concrt/parallel-algorithms.md)   
 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)   
 [任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [异步代理](../../parallel/concrt/asynchronous-agents.md)