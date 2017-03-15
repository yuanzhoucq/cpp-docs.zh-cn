---
title: "命令目标 | Microsoft Docs"
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
  - "命令映射"
  - "命令传送, 命令目标"
  - "命令目标"
  - "消息, 命令"
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 命令目标
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[框架中的命令](../mfc/user-interface-objects-and-command-ids.md) 图显示用户界面对象之间的连接 \(例如，菜单项并执行命令的调用框架的处理程序函数，当对象时。  
  
 窗口发送不是命令消息直接对窗口消息的处理程序会调用的信息。  框架但是，路由命令。大量候选项对象 \- 调用的“命令以”\- 其中通常称为命令的处理程序。  处理程序函数按命令和标准 Windows 消息的方式，但调用机制不同，如 [Framework 如何通知处理程序](../mfc/how-the-framework-calls-a-handler.md)说明。  
  
## 请参阅  
 [框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)