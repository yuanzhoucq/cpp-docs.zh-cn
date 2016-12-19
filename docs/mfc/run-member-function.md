---
title: "运行成员函数 | Microsoft Docs"
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
  - "CWinApp 类, Run"
  - "CWinApp::Run 中的消息泵"
  - "消息, 循环"
  - "Run 方法, 消息和空闲处理"
  - "WinMain 方法"
  - "WinMain 方法, 调用 CWinApp::Run"
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 运行成员函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

框架应用程序花费类 [CWinApp](../mfc/reference/cwinapp-class.md) 的 [运行](../Topic/CWinApp::Run.md) 成员函数中的大部分时间。  在初始化之后， `WinMain` 调用 **运行** 处理信息循环。  
  
 **运行** 通过消息循环进行循环，检查可用消息的消息队列。  如果消息可用，**运行** 分派行动。  如果没有消息可获得，通常为 true， **运行** 调用 `OnIdle` 处理您或框架可能需要执行的任何闲置时间进程。  如果没消息和闲置进程要执行，该应用程序等待直到某事发生。  在应用程序终止时，**运行** 调用 `ExitInstance`。  在 [OnIdle 成员函数中的数字](../mfc/onidle-member-function.md) 在消息循环中显示操作序列。  
  
 消息调度取决于此消息的类型。  有关更多信息，请参阅 [消息和框架中的命令](../mfc/messages-and-commands-in-the-framework.md).  
  
## 请参阅  
 [CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)