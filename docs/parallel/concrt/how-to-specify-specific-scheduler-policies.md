---
title: "如何： 指定特定计划程序策略 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- specifying scheduler policies [Concurrency Runtime]
- scheduler policies, specifying [Concurrency Runtime]
ms.assetid: 9c5149f9-ac34-4ff3-9e79-0bad103e4e6b
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: af30b38a89eb7e4b50c7d31be2d3ba6572843b1e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-specify-specific-scheduler-policies"></a>如何：指定特定的计划程序策略
计划程序策略让你能够控制计划程序将使用在管理任务的策略。 本主题演示如何使用计划程序策略来提高打印到控制台进度指示器的任务的线程优先级。  
  
 有关自定义计划程序策略与异步代理一起使用的示例，请参阅[如何： 创建该使用特定计划程序策略的代理](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)。  
  
## <a name="example"></a>示例  
 下面的示例并行执行两个任务。 第一个任务计算 n<sup>th</sup>斐波那契数。 第二个任务将打印到控制台进度指示器。  
  
 第一个任务使用递归分解计算斐波那契数。 也就是说，每个任务以递归方式创建多个子任务来计算的总体结果。 使用递归分解的任务可能会用尽所有可用的资源，并从而阻止其他任务。 在此示例中，输出的进度指示器的任务可能无法收到及时对计算资源的访问权。  
  
 若要提供打印进度消息公平对资源的访问计算的任务，此示例使用中所述的步骤[如何： 管理计划程序实例](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)若要创建的自定义策略的计划程序实例。 自定义策略指定的线程优先级是最高的优先级类。  
  
 此示例使用[concurrency:: call](../../parallel/concrt/reference/call-class.md)和[concurrency:: timer](../../parallel/concrt/reference/timer-class.md)类来打印进度指示器。 这些类有引用其构造函数的版本[concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)安排它们的对象。 该示例使用默认计划程序来计划计算斐波那契数和要计划的任务输出进度指示器的计划程序实例的任务。  
  
 为了说明使用的计划程序的自定义策略的好处，此示例对整个任务执行两次。 该示例首先使用默认计划程序计划这两项任务。 然后，该示例使用默认计划程序来计划第一个任务，并具有计划第二个任务的自定义策略的计划。  
  
 [!code-cpp[concrt-scheduler-policy#1](../../parallel/concrt/codesnippet/cpp/how-to-specify-specific-scheduler-policies_1.cpp)]  
  
 本示例生成以下输出。  
  
```Output  
Default scheduler:  
...........................................................................done  
Scheduler that has a custom policy:  
...........................................................................done  
```  
  
 尽管这两组任务会产生相同的结果，使用自定义策略的版本将使输出进度指示器，以便它响应能力更强的行为，以提升优先级运行的任务。  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`scheduler-policy.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc 计划程序-policy.cpp**  
  
## <a name="see-also"></a>请参阅  
 [计划程序策略](../../parallel/concrt/scheduler-policies.md)   
 [如何： 管理计划程序实例](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)   
 [如何：创建使用特定计划程序策略的代理](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)

