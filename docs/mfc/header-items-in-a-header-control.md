---
title: "标题控件中的标题项 | Microsoft Docs"
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
  - "CHeaderCtrl 类, 标题项"
  - "控件 [MFC], 标题"
  - "标题控件, 标题项"
  - "标题控件中的标题项"
ms.assetid: ac79ef1f-a671-4ab2-93e9-b1aa016a48bf
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 标题控件中的标题项
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可对外观严重的组成个标题控件的标题项控件和行为 \([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)\)。  每个标题项可以有一个字符串、一位图的图像、图像从关联列表或图像由应用程序定义的 32 位值与其关联。  字符串、位图或图像在标题项显示。  
  
 可以自定义新项的外观和内容，在创建时通过调用 [CHeaderCtrl::InsertItem](../Topic/CHeaderCtrl::InsertItem.md) 或通过修改现有项，并与 [CHeaderCtrl::GetItem](../Topic/CHeaderCtrl::GetItem.md) [CHeaderCtrl::SetItem](../Topic/CHeaderCtrl::SetItem.md)的调用。  
  
## 您想进一步了解什么？  
  
-   [自定义标题项的外观](../mfc/customizing-the-header-item-s-appearance.md)  
  
-   [对标题控件中的项排序](../mfc/ordering-items-in-the-header-control.md)  
  
-   [为标题项提供拖放支持](../mfc/providing-drag-and-drop-support-for-header-items.md)  
  
-   [对标题控件使用图像列表](../mfc/using-image-lists-with-header-controls.md)  
  
## 请参阅  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)