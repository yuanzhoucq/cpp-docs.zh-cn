---
title: "命令传送示例 | Microsoft Docs"
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
  - "命令处理, 传送命令"
  - "命令传送, OnCmdMsg 处理程序"
  - "MFC, 命令传送"
ms.assetid: 4b7b4741-565f-4878-b076-fd85c670f87f
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 命令传送示例
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为了说明，从 MDI 应用程序的编辑菜单上的清除所有菜单项考虑命令消息。  假设此命令的处理程序函数恰好是应用程序的文档类的成员函数。  这里演示该在用户选择菜单项后命令如何达到其处理程序：  
  
1.  主框架窗口首先收到命令消息。  
  
2.  主 MDI 框架窗口赋予当前活动的 MDI 子窗口机会来处理命令。  
  
3.  MDI 子框架窗口中的标准路由在检查其自己的消息映射之前赋予其视图一个此命令的机会。  
  
4.  视图没有首先检查其自己的消息映射，然后，如果未处理则将命令路由到与其关联的文档。  
  
5.  文档检查其消息映射并找到一处理程序。  文档成员函数调用并终止路由。  
  
 如果文档没有处理程序，则将命令路由到其文档模板。  然后命令将返回视图然后返回框架窗口。  最后，框架窗口中检查其消息映射。  如果此检查也失败，命令将路由回主 MDI 框架窗口然后到应用程序对象 \- 未处理命令的最终目标。  
  
## 请参阅  
 [框架如何调用处理程序](../mfc/how-the-framework-calls-a-handler.md)