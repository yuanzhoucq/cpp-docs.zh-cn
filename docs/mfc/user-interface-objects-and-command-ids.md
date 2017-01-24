---
title: "用户界面对象和命令 ID | Microsoft Docs"
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
  - "命令处理, 用户界面对象"
  - "命令 ID, 用户界面对象"
  - "命令传送, MFC"
  - "键盘快捷键, 与 ID 关联"
  - "菜单项, 与 ID 关联"
  - "MFC, 命令传送"
  - "工具栏控件 [MFC], 命令 ID"
  - "用户界面对象, 与 ID 关联"
ms.assetid: 4ea19e9b-ed1e-452e-bd33-7f509107a45b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 用户界面对象和命令 ID
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

菜单项、工具栏按钮和快捷键为“用户界面对象”的生成命令。  每个这样用户界面对象具有 ID.  将用户界面对象与命令通过分配同一 ID 对对象和命令。  按照 [消息](../mfc/messages.md)说明，命令作为专门信息实现。  图“Framework 命令”展示下面框架如何管理命令。  当用户界面对象生成某一命令，如 `ID_EDIT_CLEAR_ALL`，一个在应用程序的对象图，处理命令 \- 在下面的文档对象的 `OnEditClearAll` 通过消息映射调用文档的函数。  
  
 ![框架中的命令](../mfc/media/vc385p1.png "vc385P1")  
框架中的命令  
  
 图形“框架中的更新命令”下面展示 MFC 如何更新用户界面对象 \(如菜单项和工具栏按钮。  将在菜单下，或者在工具栏按钮循环停顿期间，MFC 路由更新命令。  在下图中，文档对象调用其更新命令处理程序，`OnUpdateEditClearAll`，启用或禁用用户界面对象。  
  
 ![框架中的命令更新](../Image/vc385P2.png "vc385P2")  
框架中的命令更新  
  
## 请参阅  
 [框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)