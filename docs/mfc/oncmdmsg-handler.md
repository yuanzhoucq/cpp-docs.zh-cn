---
title: "OnCmdMsg 处理程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OnCmdMsg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令传送, OnCmdMsg 处理程序"
  - "处理程序"
  - "处理程序, OnCmdMessage"
  - "消息, 路由"
  - "OnCmdMessage 方法"
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# OnCmdMsg 处理程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要完成路由命令，每个命令目标调用下命令目标的 `OnCmdMsg` 成员函数中的序列。  命令目标使用 `OnCmdMsg` 确定它们是否可以处理命令和发送到另一命令目标，则它们无法处理它。  
  
 每个命令目标类可能重写 `OnCmdMsg` 成员函数。  重写允许每类发送命令。下特定目标。  如下表所示， [标准命令路由](../mfc/command-routing.md)框架窗口，例如路由命令始终为其当前窗口或子视图。  
  
 默认`CCmdTarget` `OnCmdMsg` 实现命令目标类的消息映射为接收 \- 类似地每个命令消息处理程序函数搜索命令消息搜索。  如果找到匹配，它调用处理程序。  消息搜索映射在 [Framework 如何搜索消息映射](../mfc/how-the-framework-searches-message-maps.md)解释。  
  
## 请参阅  
 [框架如何调用处理程序](../mfc/how-the-framework-calls-a-handler.md)