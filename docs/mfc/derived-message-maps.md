---
title: "派生消息映射 | Microsoft Docs"
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
  - "派生消息映射"
  - "消息处理, 派生消息处理程序"
  - "消息映射, 派生"
  - "消息, 路由"
ms.assetid: 21829556-6e64-40c3-8279-fed85d99de77
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 派生消息映射
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

消息处理过程期间，检查类的消息映射不是消息映射文章的末尾。  如果类 `CMyView` \(从 `CView`派生\) 消息没有匹配输入将会发生什么？  
  
 记住 `CView` 是 `CMyView` 的基类，依次从 `CWnd` 派生。  因此，*为*`CView` 并且 `CMyView` *为*`CWnd`。  这些类都有各自的消息映射。  下面图像“视图层次结构”显示类的分层关系，但请记住 `CMyView` 对象是具有所有三个类特性的单个对象。  
  
 ![视图层次结构](../mfc/media/vc38621.png "vc38621")  
视图层次结构  
  
 因此，如果消息在类 `CMyView` 消息映射不能匹配，则该框架还搜索其直接基类的消息映射。  在消息映射的开始 `BEGIN_MESSAGE_MAP` 宏指定两个类名作为其参数：  
  
 [!CODE [NVC_MFCMessageHandling#2](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCMessageHandling#2)]  
  
 第一个参数属于命名消息映射的类。  第二个参数提供与直接基类 — `CView` 的连接 — 因此框架也可以搜索其消息映射。  
  
 在基类中提供的消息处理程序因此由派生类继承。  这非常类似于常规的虚拟成员函数，而不需要使用所有的处理程序虚成员函数。  
  
 如果在任何基类消息映射中未找到处理程序，则默认执行消息处理。  如果消息是命令，框架发送到下一个命令目标。  如果是标准 Windows 消息，将消息传递给适当的默认窗口程序。  
  
 若要加快匹配消息映射，框架缓存可能重新将接收相同消息的最近匹配。  这其中一个结果是框架高效处理未处理的消息。  消息映射比使用虚函数的实现有更高的空间利用率。  
  
## 请参阅  
 [框架如何搜索消息映射](../mfc/how-the-framework-searches-message-maps.md)