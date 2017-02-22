---
title: "并发运行时演练 | Microsoft Docs"
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
  - "并发运行时, 演练"
  - "演练 [并发运行时]"
ms.assetid: 7374c5e9-54eb-44bf-9ed9-5e190cfd290b
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 并发运行时演练
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本节中基于方案的主题演示如何使用并行运行时的多项功能。  
  
## 本节内容  
 [演练：使用任务和 XML HTTP 请求进行连接](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)  
 演示如何将 [IXMLHTTPRequest2](http://msdn.microsoft.com/zh-cn/bbc11c4a-aecf-4d6d-8275-3e852e309908) 和 [IXMLHTTPRequest2Callback](http://msdn.microsoft.com/zh-cn/aa4b3f4c-6e28-458b-be25-6cce8865fc71) 接口与任务结合使用，以将 HTTP GET 和 POST 请求发送至 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]应用中的 Web 服务。  
  
 [演练：创建基于代理的应用程序](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)  
 描述如何创建基于代理的基本应用程序。  
  
 [演练：创建数据流代理](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)  
 演示如何创建基于代理的应用程序，这些应用程序基于数据流而不是控制流。  
  
 [演练：创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)  
 演示如何创建执行图像处理的异步消息块的网络。  
  
 [演练：实现 Future](../../parallel/concrt/walkthrough-implementing-futures.md)  
 演示如何异步计算值供以后使用。  
  
 [演练：使用 join 避免死锁](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)  
 通过哲学家就餐问题说明如何使用 [concurrency::join](../../parallel/concrt/reference/join-class.md) 类来避免应用程序中发生死锁。  
  
 [演练：从用户界面线程中移除工作](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)  
 演示如何提高绘制 Mandelbrot 分形的 MFC 应用程序的性能。  
  
 [演练：在启用 COM 的应用程序中使用并发运行时](../../parallel/concrt/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application.md)  
 演示如何在使用组件对象模型 \(COM\) 的应用程序中使用并发运行时。  
  
 [演练：调整现有代码以使用轻量级任务](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)  
 演示如何改编现有代码，从而使用 Windows API 创建并执行一个线程来使用轻量级任务。  
  
 [演练：创建自定义消息块](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)  
 介绍如何创建按优先级排序传入消息的自定义消息块类型。  
  
## 相关章节  
 [并发运行时](../../parallel/concrt/concurrency-runtime.md)  
 介绍 Visual C\+\+ 的并发编程框架。