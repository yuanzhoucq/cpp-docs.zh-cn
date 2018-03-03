---
title: "如何： 创建使用特定计划程序策略的代理 |Microsoft 文档"
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
- scheduler policies, agents [Concurrency Runtime]
- creating agents that use specific policies [Concurrency Runtime]
ms.assetid: 46a3e265-0777-4ec3-a142-967bafc49d67
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d465b39e00bee0911fb5b04bbe60af68e1f296c5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-agents-that-use-specific-scheduler-policies"></a>如何：创建使用特定计划程序策略的代理
代理是以异步方式与其他组件以解决更大的计算任务将应用程序组件。 代理通常具有设定的生命周期，并保持状态。  
  
 每个代理都有唯一的应用程序需求。 例如，使用户交互 （检索输入或显示输出） 的代理可能需要更高优先级访问的计算资源。 计划程序策略让你能够控制计划程序将使用在管理任务的策略。 本主题演示如何创建使用特定计划程序策略的代理。  
  
 有关自定义计划程序策略与异步消息块一起使用的基本示例，请参阅[如何： 指定特定计划程序策略](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)。  
  
 本主题使用通过异步代理库，如代理、 消息块和消息传递函数的功能来执行工作。 有关异步代理库的详细信息，请参阅[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)。  
  
## <a name="example"></a>示例  
 下面的示例定义两个类派生自[concurrency:: agent](../../parallel/concrt/reference/agent-class.md):`permutor`和`printer`。 `permutor`类计算所有排列给定的输入字符串。 `printer`类打印到控制台的进度消息。 `permutor`类执行一个计算密集型操作，从而可能会使用所有可用的计算资源。 若要很有用，`printer`类必须及时打印每个进度消息。  
  
 若要提供`printer`类对计算资源的公平访问，此示例使用中所述的步骤[如何： 管理计划程序实例](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)若要创建的自定义策略的计划程序实例。 自定义策略指定的线程优先级是最高的优先级类。  
  
 为了说明使用的计划程序的自定义策略的好处，此示例对整个任务执行两次。 该示例首先使用默认计划程序计划这两项任务。 示例然后使用默认计划程序来计划`permutor`对象，并且具有计划的自定义策略的计划程序`printer`对象。  
  
 [!code-cpp[concrt-permute-strings#1](../../parallel/concrt/codesnippet/cpp/how-to-create-agents-that-use-specific-scheduler-policies_1.cpp)]  
  
 本示例生成以下输出。  
  
```Output  
With default scheduler:  
Computing all permutations of 'Grapefruit'...  
100% complete...  
 
With higher context priority:  
Computing all permutations of 'Grapefruit'...  
100% complete...  
```  
  
 尽管这两组任务会产生相同的结果，使用自定义策略的版本使`printer`运行在提升的优先级别，以便它响应能力更强的行为的对象。  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`permute-strings.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc permute strings.cpp**  
  
## <a name="see-also"></a>请参阅  
 [计划程序策略](../../parallel/concrt/scheduler-policies.md)   
 [异步代理](../../parallel/concrt/asynchronous-agents.md)   
 

