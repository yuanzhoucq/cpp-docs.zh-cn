---
title: "测试 Internet 应用程序 | Microsoft Docs"
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
  - "调试 [MFC], Web 应用程序"
  - "调试 Web 应用程序, 测试应用程序"
  - "Internet 调试和测试"
  - "测试, Internet 应用程序"
  - "Web 应用程序, 测试"
ms.assetid: ac4c74e3-d4ad-4e19-8f6c-e270de067f01
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 测试 Internet 应用程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 Internet 的一些特殊的难题测试，特别是在 Web 服务器上运行应用程序。  初始测试可能完成使用连接到测试服务器的单个用户的帐户。  这对调试很有用。  
  
 还需要在实际条件下测试：而多个客户端连接。缓存以及连接低速串行的行，包括解调器连接。  模拟实际情况很难的，但是，它必须是值得所设计可能的方案和它们执行的时间。  如果可能，则还需要使用此工具执行容量和压力测试。  Bug 一些类，例如计时很难重现查找Bug。  
  
 一个 Internet 进行编程时遇到的挑战是其可见性。  对站点中访问许多可能降低服务器。  您希望服务器完全降低级别。  要防止可能破坏性于用户计算机的任何应用程序，则失败 \(例如，数据损坏，在写入注册表，或者在编写时 Cookie 保存在客户端\)。  
  
## 请参阅  
 [MFC Internet 编程任务](../mfc/mfc-internet-programming-tasks.md)   
 [MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)