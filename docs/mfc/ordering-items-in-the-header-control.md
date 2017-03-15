---
title: "对标题控件中的项排序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DS_DRAGDROP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DS_DRAGDROP 通知"
  - "GetOrderArray 方法"
  - "标题控件, 对项进行排序"
  - "OrderToIndex 方法"
  - "序列"
  - "序列, 标题控件项"
  - "SetOrderArray 方法"
ms.assetid: 5aaef872-75b5-49c5-8fed-6f9a81fca812
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 对标题控件中的项排序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一旦已将 [对标题控件的项](../mfc/adding-items-to-the-header-control.md)，即可操作或获取有关它们的信息。下面的函数：  
  
-   [CHeaderCtrl::GetOrderArray](../Topic/CHeaderCtrl::GetOrderArray.md) 和 [CHeaderCtrl::SetOrderArray](../Topic/CHeaderCtrl::SetOrderArray.md)  
  
     检索和设置标题项的排序。  
  
-   [CHeaderCtrl::OrderToIndex](../Topic/CHeaderCtrl::OrderToIndex.md)。  
  
     检索特定标题项的索引值。  
  
 除了前面成员函数外，`HDS_DRAGDROP` 样式允许用户拖放在标题控件中的标题项。  有关更多信息，请参见 [提供的拖放支持标题项](../mfc/providing-drag-and-drop-support-for-header-items.md)。  
  
## 请参阅  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)