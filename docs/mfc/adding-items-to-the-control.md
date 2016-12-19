---
title: "向控件添加项 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "CListCtrl 类, 添加项"
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 向控件添加项
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要向列表控件添加项 \([CListCtrl](../mfc/reference/clistctrl-class.md)\)，具体根据信息称为 [InsertItem](../Topic/CListCtrl::InsertItem.md) 成员函数的几个版本之一，则具有。  一个版本采用您准备的 [LV\_ITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760) 结构。  由于 `LV_ITEM` 结构包含过多成员，则更多的控制。列表控件项的特性。  
  
 两个关键成员 \(随报表视图\) `LV_ITEM` 结构是 `iItem` 和 `iSubItem` 成员。  `iItem` 成员是引用结构项的从零开始的索引，而 `iSubItem` 成员是从一开始的子项的索引或零，则结构包含有关项目中的项的信息。  利用这两个成员。确定，每个项目类型，和值显示子项列表控件的信息，请在"视图时。  有关更多信息，请参见 [CListCtrl::SetItem](../Topic/CListCtrl::SetItem.md)。  
  
 附加成员指定项的文本、图标、状态和项数据。“项数据”是由应用程序定义的值与列表视图项。  有关`LV_ITEM`结构的更多信息，请参见[CListCtrl::GetItem](../Topic/CListCtrl::GetItem.md)。  
  
 `InsertItem` 的其他版本采用一个或多个单独值，与 `LV_ITEM` 结构的相应成员，使您可以初始化希望只支持的这些成员。  通常，列表控件管理列表项的存储，但是，可以存储在某些应用程序的信息，使用回调“项”。有关更多信息，请参见本主题中的 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [回调项和回调掩码](../mfc/callback-items-and-the-callback-mask.md) 和 [回调项和回调掩码](http://msdn.microsoft.com/library/windows/desktop/bb774736)。  
  
 有关更多信息，请参见 [添加列表视图项和子项](http://msdn.microsoft.com/library/windows/desktop/bb774736)。  
  
## 请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)