---
title: "CTreeCtrl 与 CTreeView | Microsoft Docs"
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
  - "CTreeCtrl"
  - "CTreeView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTreeCtrl 类, 与 CTreeView 类"
  - "CTreeView 类, 与 CTreeCtrl 类"
  - "树控件, 和树视图"
  - "树视图控件"
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTreeCtrl 与 CTreeView
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 提供了封装树控件的两类：[CTreeCtrl](../mfc/reference/ctreectrl-class.md) 和 [CTreeView](../mfc/reference/ctreeview-class.md)。  每类很有用不同的情况。  
  
 需要纯子窗口控件时，请使用 `CTreeCtrl` ;例如，对话框。  在典型的对话框特别是希望使用 `CTreeCtrl`，则在窗口的其他子控件。  
  
 如果希望控件树操作类似于文档\/视图体系结构以及树控件时，一个窗口中使用 `CTreeView`。  `CTreeView` 将占用框架窗口或拆分窗口的整个工作区。  将自动调整，当其父窗口调整大小，因此，它可以处理从菜单、快捷键和"工具栏的命令消息。  由于树控件包含必要的数据显示树，对应的文档对象不需要很复杂 \(您甚至可以使用 [CDocument](../mfc/reference/cdocument-class.md) 作为文档类型使用文档模板。  
  
## 请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)