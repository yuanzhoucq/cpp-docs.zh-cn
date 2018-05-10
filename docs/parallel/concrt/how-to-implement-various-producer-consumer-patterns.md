---
title: 如何： 实现各种制造者-使用者模式 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- producer-consumer patterns, implementing [Concurrency Runtime]
- implementing producer-consumer patterns [Concurrency Runtime]
ms.assetid: 75f2c7cc-5399-49ea-98eb-847fe6747169
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50a6683db37fb6e994c1957a8df3ab6469acff6d
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-implement-various-producer-consumer-patterns"></a>如何：实现各种制造者-使用者模式
本主题介绍如何在你的应用程序中实现制造者-使用者模式。 在此模式下，制造者向消息块发送消息，使用者从该块读取消息。  
  
 本主题演示两种方案。 在第一个方案中，使用者必须接收制造者发送每条消息。 在第二个方案中，使用者会定期轮询数据，并因此不需要接收每条消息。  
  
 本主题中的这两个示例使用代理、 消息块和消息传递函数将消息从制造者向使用者传输。 制造者代理使用[concurrency:: send](reference/concurrency-namespace-functions.md#send)函数以将消息写入到[concurrency:: itarget](../../parallel/concrt/reference/itarget-class.md)对象。 使用者代理使用[concurrency:: receive](reference/concurrency-namespace-functions.md#receive)函数从中读取消息[concurrency:: isource](../../parallel/concrt/reference/isource-class.md)对象。 这两个代理保存 sentinel 值来协调过程结束时。  
  
 异步代理有关的详细信息，请参阅[异步代理](../../parallel/concrt/asynchronous-agents.md)。 有关消息块和消息传递函数的详细信息，请参阅[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)和[消息传递函数](../../parallel/concrt/message-passing-functions.md)。  
  
## <a name="example"></a>示例  
 在此示例中，制造者代理会将一系列数字发送到使用者代理。 使用者接收其中每个数字并计算其平均值。 应用程序将写入控制台的平均值。  
  
 此示例使用[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)对象，以允许到队列消息创建方。 `unbounded_buffer`类实现`ITarget`和`ISource`以便制造者和使用者可以发送和接收共享缓冲的消息。 `send`和`receive`函数协调传播中制造者向使用者的数据的任务。  
  
 [!code-cpp[concrt-producer-consumer-average#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_1.cpp)]  
  
 本示例生成以下输出。  
  
```Output  
The average is 50.  
```  
  
## <a name="example"></a>示例  
 在此示例中，制造者代理会将一系列的股票报价发送到使用者代理。 使用者代理定期读取当前报价，并将它打印到控制台。  
  
 此示例类似于前一个，只不过它使用[concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)对象，以允许创建方与使用者共享一条消息。 与前面的示例中，`overwrite_buffer`类实现`ITarget`和`ISource`以便制造者和使用者可以作用于共享的消息缓冲区。  
  
 [!code-cpp[concrt-producer-consumer-quotes#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_2.cpp)]  
  
 该示例产生下面的示例输出。  
  
```Output  
Current quote is 24.44.  
Current quote is 24.44.  
Current quote is 24.65.  
Current quote is 24.99.  
Current quote is 23.76.  
Current quote is 22.30.  
Current quote is 25.89.  
```  
  
 与不同与`unbounded_buffer`对象，`receive`函数不会删除从消息`overwrite_buffer`对象。 如果使用者从消息缓冲区中读取不止一次制造者覆盖该消息之前，接收方将获取相同消息每次。  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`producer-consumer.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc 制造者-consumer.cpp**  
  
## <a name="see-also"></a>请参阅  
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)   
 [异步代理](../../parallel/concrt/asynchronous-agents.md)   
 [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)   
 [消息传递函数](../../parallel/concrt/message-passing-functions.md)
