---
title: "如何：更新用户界面对象 | Microsoft Docs"
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
  - "命令, 更新 UI"
  - "禁用菜单"
  - "禁用 UI 元素"
  - "启用菜单"
  - "启用 UI 元素"
  - "菜单, 在上下文更改时更新"
  - "更新处理程序"
  - "更新用户界面对象"
  - "用户界面对象"
  - "用户界面对象, 更新"
ms.assetid: 82f09773-c978-427b-b321-05a6143b7369
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 如何：更新用户界面对象
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通常，菜单项和工具栏按钮有多个状态。  例如，如果菜单项在当前上下文不可用，将变灰 \(变暗\)。  菜单项有检查或无检查。  如果不可用的，工具栏按钮将被禁用，也可以检查。  
  
 当程序情况更改，来更新这些项的状态？  在逻辑上，如果菜单项，生成由文档操作的命令，很有意义使文档更新菜单项。  文档可能包含更新的信息。  
  
 如果您的命令具有多个用户界面对象 \(或许菜单项和工具栏按钮\)，路由到同一处理两个函数。  它在一个地方封装全部的用户界面更新代码等效的用户界面对象。  
  
 框架为自动更新用户界面对象提供了方便的界面。  您可以选择这样更新以某种其他方式，但是，提供的接口是高效和易用性的。  
  
 下列主题解释了使用更新处理程序：  
  
-   [何时调用更新处理程序](../mfc/when-update-handlers-are-called.md)  
  
-   [ON\_UPDATE\_COMMAND\_UI 宏](../mfc/on-update-command-ui-macro.md)  
  
-   [CCmdUI 类](../mfc/the-ccmdui-class.md)  
  
## 请参阅  
 [菜单](../mfc/menus-mfc.md)