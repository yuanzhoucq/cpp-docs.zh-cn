---
title: "消息传递函数 | Microsoft Docs"
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
  - "消息传递函数"
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
caps.latest.revision: 23
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 消息传递函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

异步代理库提供了一些函数，这些函数使您可以在组件之间传递消息。  
  
 这些消息传递函数与各种消息块类型一起使用。  有关并发运行时所定义的消息块类型的更多信息，请参见[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。  
  
##  <a name="top"></a> 各节内容  
 本主题描述以下消息传递函数：  
  
-   [send 和 asend](#send)  
  
-   [receive 和 try\_receive](#receive)  
  
-   [示例](#examples)  
  
##  <a name="send"></a> send 和 asend  
 [concurrency::send](../Topic/send%20Function.md) 函数可将消息同步发送到指定目标，[concurrency::asend](../Topic/asend%20Function.md) 函数可将消息异步发送到指定目标。  在目标指示它将最终接受或拒绝消息之前，`send` 和 `asend` 函数都将一直等待。  
  
 `send` 函数等到目标接受或拒绝消息后才会返回。  如果已发送消息，则 `send` 函数将返回 `true`，否则将返回 `false`。  因为 `send` 函数以同步方式工作，所以 `send` 函数会先等待目标接收消息，然后才会返回。  
  
 相反，`asend` 函数在返回之前不会等待目标接受或拒绝消息。  相反，当目标接受消息并且最终将采用该消息时，`asend` 函数会返回 `true`。  否则，`asend` 将返回 `false`，以指示目标拒绝了消息或者目标延迟决定是否采用消息。  
  
 \[[Top](#top)\]  
  
##  <a name="receive"></a> receive 和 try\_receive  
 [concurrency::receive](../Topic/receive%20Function.md) 和 [concurrency::try\_receive](../Topic/try_receive%20Function.md) 函数从给定的源读取数据。  `receive` 函数将等待数据可用，而 `try_receive` 函数将立即返回。  
  
 如果必须具有数据才能继续，请使用 `receive` 函数。  如果不必阻止当前上下文，或者不必具有数据便可继续，请使用 `try_receive` 函数。  
  
 \[[Top](#top)\]  
  
##  <a name="examples"></a> 示例  
 有关使用 `send`、`asend` 和 `receive` 函数的示例，请参见以下主题：  
  
-   [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [如何：实现各种制造者\-使用者模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)  
  
-   [如何：为 call 和 transformer 类提供工作函数](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)  
  
-   [如何：在数据管道中使用转换器](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)  
  
-   [如何：在已完成的任务之间选择](../../parallel/concrt/how-to-select-among-completed-tasks.md)  
  
-   [如何：定期发送消息](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)  
  
-   [如何：使用消息块筛选器](../../parallel/concrt/how-to-use-a-message-block-filter.md)  
  
 \[[Top](#top)\]  
  
## 请参阅  
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)   
 [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)   
 [send 函数](../Topic/send%20Function.md)   
 [asend 函数](../Topic/asend%20Function.md)   
 [receive 函数](../Topic/receive%20Function.md)   
 [try\_receive 函数](../Topic/try_receive%20Function.md)