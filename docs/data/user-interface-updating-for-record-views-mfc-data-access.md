---
title: "记录视图的用户界面更新（MFC 数据访问） | Microsoft Docs"
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
  - "菜单, 在上下文更改时更新"
  - "记录视图, 用户界面"
  - "用户界面, 更新"
ms.assetid: 2c7914b6-2dc3-40c3-b2f2-8371da2a4063
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 记录视图的用户界面更新（MFC 数据访问）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CRecordView` 和 `CDaoRecordView` 还为导航命令提供了默认的用户界面更新处理程序。  这些处理程序自动启用和禁用用户界面对象 — 菜单项和工具栏按钮。  应用程序向导提供标准菜单，如果选择“可停靠工具栏”选项，则为命令提供一组工具栏按钮。  如果使用 `CRecordView` 创建记录视图类，建议将类似的用户界面对象添加到应用程序。  
  
### 若要使用菜单编辑器创建菜单资源  
  
1.  参照有关使用[菜单编辑器](../mfc/menu-editor.md)的信息，使用相同的四个命令创建自己的菜单。  
  
#### 若要使用图形编辑器创建工具栏按钮  
  
1.  参照有关使用[工具栏编辑器](../mfc/toolbar-editor.md)的信息，编辑工具栏资源以便为记录导航命令添加工具栏按钮。  
  
## 请参阅  
 [支持在记录视图中导航](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)   
 [使用记录视图](../data/using-a-record-view-mfc-data-access.md)