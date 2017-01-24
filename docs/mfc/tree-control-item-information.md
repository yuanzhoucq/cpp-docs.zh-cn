---
title: "树控件项信息 | Microsoft Docs"
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
  - "CTreeCtrl 类, 项信息"
  - "树控件, 项信息"
ms.assetid: 8dcab855-27de-49e9-95d8-f78ba963ea71
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 树控件项信息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

树控件具有 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) 检索有关项目中的项的信息。控件的成员函数。  [GetItem](../Topic/CTreeCtrl::GetItem.md) 成员函数检索某些或全部数据与项。  此数据可以包括项的状态、文本、图像、计数和子项一个应用程序所定义的 32 位数据值。  还可以设置某些或全部数据与项的函数[SetItem](../Topic/CTreeCtrl::SetItem.md)。  
  
 The [GetItemState](../Topic/CTreeCtrl::GetItemState.md), [GetItemText](../Topic/CTreeCtrl::GetItemText.md), [GetItemData](../Topic/CTreeCtrl::GetItemData.md), and [GetItemImage](../Topic/CTreeCtrl::GetItemImage.md) 和成员函数检索项的各个特性。  这些函数中的每个设置的特性集合相应的函数。  
  
 [GetNextItem](../Topic/CTreeCtrl::GetNextItem.md)成员函数检索对当前项的负担指定的项的树控件项。  此函数来检索项的父级下，或以前可见项，第一个子项，依此类推。  也具有树遍历的成员函数： [GetRootItem](../Topic/CTreeCtrl::GetRootItem.md), [GetFirstVisibleItem](../Topic/CTreeCtrl::GetFirstVisibleItem.md), [GetNextVisibleItem](../Topic/CTreeCtrl::GetNextVisibleItem.md), [GetPrevVisibleItem](../Topic/CTreeCtrl::GetPrevVisibleItem.md), [GetChildItem](../Topic/CTreeCtrl::GetChildItem.md), [GetNextSiblingItem](../Topic/CTreeCtrl::GetNextSiblingItem.md), [GetPrevSiblingItem](../Topic/CTreeCtrl::GetPrevSiblingItem.md), [GetParentItem](../Topic/CTreeCtrl::GetParentItem.md), [GetSelectedItem](../Topic/CTreeCtrl::GetSelectedItem.md), and [GetDropHilightItem](../Topic/CTreeCtrl::GetDropHilightItem.md)。  
  
 [GetItemRect](../Topic/CTreeCtrl::GetItemRect.md)成员函数检索树项控件的边框。  [GetCount](../Topic/CTreeCtrl::GetCount.md) and [GetVisibleCount](../Topic/CTreeCtrl::GetVisibleCount.md) 成员和函数分别检索项的计数和控件在树的当前可见的窗口在树控件项的计数。  可以确保特定项通过调用成员函数 [EnsureVisible](../Topic/CTreeCtrl::EnsureVisible.md) 可见。  
  
## 请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)