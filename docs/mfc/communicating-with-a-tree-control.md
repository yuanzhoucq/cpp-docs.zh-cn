---
title: "与树控件通信 | Microsoft Docs"
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
  - "通信, 树控件"
  - "CTreeCtrl 类, 调用成员函数"
  - "树控件"
  - "树控件, 与其通信"
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 与树控件通信
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 [CTreeCtrl](../mfc/reference/ctreectrl-class.md) 对象中调用成员函数的不同方法，对象根据如何创建对象：  
  
-   如果树控件在对话框中，使用你在对象框类中创建的 `CTreeCtrl` 类型的成员变量。  
  
-   如果树控件是子窗口，请使用 `CTreeCtrl` 对象或指针\) \(用于构造对象。  
  
-   如果使用 `CTreeView` 对象，请使用 [CTreeView::GetTreeCtrl](../Topic/CTreeView::GetTreeCtrl.md) 函数获取对树控件的引用。  您可以初始化与此值的另引用或分配引用的地址为 `CTreeCtrl` 指针的。  
  
## 请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)