---
title: "映射消息 | Microsoft Docs"
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
  - "命令, 连接到处理程序函数"
  - "命令, 映射"
  - "映射, 命令"
  - "映射, 消息"
  - "消息处理, 连接到处理程序函数"
  - "消息映射, 关于消息映射"
  - "消息, 映射"
ms.assetid: 996f0652-0698-4b8c-b893-cdaa836d9d0f
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 映射消息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

接收消息或命令的每个框架类有自己“消息映射”。框架使用消息连接消息映射和命令到它们的处理程序函数。  从类派生的任何类 `CCmdTarget` 可以包含消息映射。  其他情景详细说明消息映射并说明如何使用它们。  
  
 尽管管名称“消息映射，”消息映射处理的消息和命令 \- 在 [消息类别](../mfc/message-categories.md)消息列出的三个类别。  
  
## 请参阅  
 [框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)