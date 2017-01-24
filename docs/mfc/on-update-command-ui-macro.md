---
title: "ON_UPDATE_COMMAND_UI 宏 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ON_UPDATE_COMMAND_UI"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令处理程序宏"
  - "ON_UPDATE_COMMAND_UI 宏"
  - "更新处理程序"
  - "更新用户界面对象"
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ON_UPDATE_COMMAND_UI 宏
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 **属性** 窗口连接到命令更新处理程序的用户界面对象命令目标对象的。  它会自动连接用户界面对象的 ID 设置为 `ON_UPDATE_COMMAND_UI` 并创建宏处理更新的对象的处理程序。  有关更多信息，请参见 [将消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)。  
  
 例如，更新对程序在"编辑"菜单上的所有命令，请使用 **属性** 窗口添加到的类选择的消息映射项的命令，更新处理程序声明的函数调用类中声明的 `OnUpdateEditClearAll` 类中的和实现文件的空白函数模板。  原型函数类似于这样：  
  
 [!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/CPP/on-update-command-ui-macro_1.h)]  
  
 同所有处理程序函数，显示 **afx\_msg** 关键字。  同所有更新处理程序，它带有一个参数，将 `CCmdUI` 对象的指针。  
  
## 请参阅  
 [如何：更新用户界面对象](../mfc/how-to-update-user-interface-objects.md)