---
title: 并发运行时演练 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- walkthroughs [Concurrency Runtime]
- Concurrency Runtime, walkthroughs
ms.assetid: 7374c5e9-54eb-44bf-9ed9-5e190cfd290b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05e50530bf1c7aa401a7422a0119f004e30234a9
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686628"
---
# <a name="concurrency-runtime-walkthroughs"></a>并发运行时演练
本部分中的基于方案的主题演示如何使用许多并发运行时的功能。  
  
## <a name="in-this-section"></a>本节内容  
 [演练：使用任务和 XML HTTP 请求进行连接](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)  
 演示如何使用[IXMLHTTPRequest2](http://msdn.microsoft.com/en-us/bbc11c4a-aecf-4d6d-8275-3e852e309908)和[IXMLHTTPRequest2Callback](http://msdn.microsoft.com/en-us/aa4b3f4c-6e28-458b-be25-6cce8865fc71)接口与任务以将 HTTP GET 和 POST 请求发送到通用 Windows 平台 (UWP) 应用程序中的 web 服务。  
  
 [演练：创建基于代理的应用程序](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)  
 描述如何创建基于代理的基本应用程序。  
  
 [演练：创建数据流代理](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)  
 演示如何创建基于代理的应用程序在基于数据流，而不是在控制流。  
  
 [演练：创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)  
 演示如何创建执行图像处理的异步消息块网络。  
  
 [演练：实现 Future](../../parallel/concrt/walkthrough-implementing-futures.md)  
 演示如何以异步方式计算以供将来使用的值。  
  
 [演练：使用 join 避免死锁](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)  
 使用通过哲学家就餐问题说明如何使用[concurrency:: join](../../parallel/concrt/reference/join-class.md)类以防止你的应用程序中发生死锁。  
  
 [演练：从用户界面线程中删除工作](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)  
 演示如何改进绘制 Mandelbrot 分形 MFC 应用程序的性能。  
  
 [演练：在启用 COM 的应用程序中使用并发运行时](../../parallel/concrt/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application.md)  
 演示如何在使用组件对象模型 (COM) 的应用程序中使用并发运行时。  
  
 [演练：调整现有代码以使用轻量级任务](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)  
 演示如何改编现有代码，它使用 Windows API 创建和执行一个线程以使用轻量级任务。  
  
 [演练：创建自定义消息块](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)  
 描述如何创建按优先级排序传入消息的自定义消息块类型。  
  
## <a name="related-sections"></a>相关章节  
 [并发运行时](../../parallel/concrt/concurrency-runtime.md)  
 为 Visual c + + 引入了并发编程框架。

