---
title: "处理文档中的命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WM_COMMAND"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令处理"
  - "命令处理, 文档中的命令"
  - "文档, 处理消息"
  - "文档, 消息映射"
  - "消息处理, WM_COMMAND 消息"
  - "消息映射, 在文档类中"
  - "WM_COMMAND"
ms.assetid: c7375584-27af-4275-b2fd-afea476785d0
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 处理文档中的命令
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文档类还处理菜单项、工具栏按钮或快捷键生成的某些命令。  默认情况下，使用序列化，**CDocument** 处理" File "菜单上的"保存"和，"另存为"命令。  影响数据的其他命令可以由文档的成员函数来处理。  例如，在 Scribble 程序，`CScribDoc` 类为编辑签提供了处理程序的所有命令，删除文档中当前存储的所有数据。  文档可以包含消息映射，但是，不同视图，文档不能处理标准 Windows 消息 \( **WM\_COMMAND** 仅消息或“命令”。  
  
## 请参阅  
 [使用文档](../mfc/using-documents.md)