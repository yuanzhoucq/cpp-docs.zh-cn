---
title: "消息 | Microsoft Docs"
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
  - "消息"
  - "消息, MFC"
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 消息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在类 `CWinApp` 的 **运行** 成员函数的消息循环以检索各种事件生成队列的消息。  例如，当用户单击窗口，鼠标时，发送若干与鼠标有关的信息，例如 `WM_LBUTTONDOWN`，当按鼠标左键和 `WM_LBUTTONUP` 时，鼠标左键释放时。  应用程序消息循环的框架实现的消息调度到相应的窗口。  
  
 消息重要类别在 [消息类别](../mfc/message-categories.md)中描述。  
  
## 请参阅  
 [框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)