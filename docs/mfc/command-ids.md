---
title: "命令 ID | Microsoft Docs"
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
  - "命令 ID"
  - "命令 ID, MFC"
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 命令 ID
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

命令综合由单独其命令 ID 描述 \(编码中 **WM\_COMMAND** 消息\)。  此 ID 分配给生成命令的用户界面对象。  通常，它们分配的 ID 被命名的用户界面对象功能。  
  
 例如，签在"编辑"菜单上的所有项可能会指派一个 ID \(如 **ID\_EDIT\_CLEAR\_ALL**\)。  类库预定义某些 ID，具体而言框架处理本身的命令，例如 **ID\_EDIT\_CLEAR\_ALL** 或 `ID_FILE_OPEN`。  您将创建另命令 ID。  
  
 当创建时将自己在 Visual C\+\+ 编辑器，该菜单的菜单是一个好办法跟在类库的命名约定。阐释了由 `ID_FILE_OPEN`。  [标准命令](../mfc/standard-commands.md) 解释类库定义标准的命令。  
  
## 请参阅  
 [用户界面对象和命令 ID](../mfc/user-interface-objects-and-command-ids.md)