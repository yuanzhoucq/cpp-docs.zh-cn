---
title: "OnIdle 成员函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OnIdle"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinApp 类, OnIdle 方法"
  - "空闲循环处理"
  - "消息处理, OnIdle 方法"
  - "OnIdle 方法"
  - "处理消息"
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# OnIdle 成员函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在窗口消息未处理时，框架调用成员函数 [CWinApp](../mfc/reference/cwinapp-class.md) [OnIdle](../Topic/CWinApp::OnIdle.md) \(介绍 MFC 库引用\)。  
  
 重写执行后台任务的 `OnIdle`。  默认生成更新用户界面对象的状态。例如工具栏按钮并执行框架创建的临时对象清除其操作过程。  下图说明消息循环方式调用 `OnIdle`，则不在队列中的消息。  
  
 ![消息循环过程](../mfc/media/vc387c1.png "vc387C1")  
消息循环  
  
 有关要完成工作的更多信息可以在、执行，请参见 [、处理](../mfc/idle-loop-processing.md)。  
  
## 请参阅  
 [CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)