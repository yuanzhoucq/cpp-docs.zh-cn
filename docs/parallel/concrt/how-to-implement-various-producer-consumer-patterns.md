---
title: "如何：实现各种制造者-使用者模式 | Microsoft Docs"
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
  - "制造者-使用者模式, 实现 [并发运行时]"
  - "实现制造者-使用者模式 [并发运行时]"
ms.assetid: 75f2c7cc-5399-49ea-98eb-847fe6747169
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：实现各种制造者-使用者模式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题描述如何在您的应用程序中实现制造者\-使用者模式。  在此模式中，制造者向消息块发送消息，使用者从该块中读取消息。  
  
 本主题演示了两种方案。  在第一个方案中，使用者必须接收制造者发送的每条消息。  在第二个方案中，使用者定期轮询数据，因此不必接收每条消息。  
  
 本主题中的两个示例均使用代理、消息块和消息传递函数将消息从制造者传输给使用者。  制造者代理使用 [concurrency::send](../Topic/send%20Function.md) 函数将消息写入 [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) 对象。  使用者代理使用 [concurrency::receive](../Topic/receive%20Function.md) 函数从 [concurrency::ISource](../../parallel/concrt/reference/isource-class.md) 对象读取消息。  两个代理都具有 sentinel 值以协调处理结束。  
  
 有关异步代理的更多信息，请参见[异步代理](../../parallel/concrt/asynchronous-agents.md)。  有关消息块和消息传递函数的更多信息，请参见[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)和[消息传递函数](../../parallel/concrt/message-passing-functions.md)。  
  
## 示例  
 在本示例中，制造者代理将一系列数字发送给使用者代理。  使用者接收其中每个数字并计算它们的平均值。  应用程序将平均值写入控制台。  
  
 本示例使用 [concurrency::unbounded\_buffer](../Topic/unbounded_buffer%20Class.md) 对象使制造者能够对消息进行排队。  `unbounded_buffer` 类实现 `ITarget` 和 `ISource`，以便制造者和使用者可以将消息发送到共享缓冲区以及从共享缓冲区接收消息。  `send` 和 `receive` 函数会对将数据从制造者传播给使用者这一任务进行协调。  
  
 [!code-cpp[concrt-producer-consumer-average#1](../../parallel/concrt/codesnippet/CPP/how-to-implement-various-producer-consumer-patterns_1.cpp)]  
  
 该示例产生下面的输出。  
  
  **平均值是50.**   
## 示例  
 在本示例中，制造者代理将一系列股票报价发送给使用者代理。  使用者代理定期读取当前报价并将其打印到控制台。  
  
 本示例与前一个示例相似，但它使用 [concurrency::overwrite\_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) 对象来使制造者能够与使用者共享一条消息。  就像在上一个示例中一样，`overwrite_buffer` 类实现 `ITarget` 和 `ISource`，以便制造者和使用者可以操作共享的消息缓冲区。  
  
 [!code-cpp[concrt-producer-consumer-quotes#1](../../parallel/concrt/codesnippet/CPP/how-to-implement-various-producer-consumer-patterns_2.cpp)]  
  
 此示例产生下面的示例输出。  
  
  **当前报价为 24.44。**  
**当前报价为 24.44。**  
**当前报价为 24.65。**  
**当前报价为 24.99。**  
**当前报价为 23.76。**  
**当前报价为 22.30。**  
**当前报价为 25.89。** 与 `unbounded_buffer` 对象不同，`receive` 函数不会从 `overwrite_buffer` 对象中移除消息。  如果使用者在制造者覆盖该消息之前多次从消息缓冲区中进行读取，则接收者每次都将获得相同的消息。  
  
## 编译代码  
 复制代码示例，并将此代码粘贴到Visual Studio项目中或一个名为 `producer-consumer.cpp` 的文件中，然后在Visual Studio命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc producer\-consumer.cpp**  
  
## 请参阅  
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)   
 [异步代理](../../parallel/concrt/asynchronous-agents.md)   
 [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)   
 [消息传递函数](../../parallel/concrt/message-passing-functions.md)