---
title: "使用 CImageList | Microsoft Docs"
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
  - "CImageList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CImageList 类, using"
  - "图像列表控件"
ms.assetid: 3d2a909e-d641-46b7-aada-81cab1a29b41
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 CImageList
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

图像列表，类由 [CImageList](../mfc/reference/cimagelist-class.md)，相同大小的图像的集合，每一对可以通过索引引用。  图像列表用于有效地管理大量图标或位图。  因为它们不是窗口，图像列表不是其各自控件；但是，这些控件使用的几种不同类型，包括列表控件 \([CListCtrl](../mfc/reference/clistctrl-class.md)\)，树控件 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) 和选项卡控件 \(\)。[CTabCtrl](../mfc/reference/ctabctrl-class.md)  
  
 在图像列表中的所有图像在屏幕设备格式包含一个宽，位图。  图像列表可能包含透明蒙板使用地绘制图像的纯色位图 \(图标\) 样式。  `CImageList` 提供可以绘制图像，并销毁生成图像列表，添加和移除图像，替换图像，图像组合的成员函数和拖动图像。  
  
## 您想进一步了解什么？  
  
-   [图像列表类型](../mfc/types-of-image-lists.md)  
  
-   [使用图像列表](../mfc/using-an-image-list.md)  
  
-   [操作图像列表](../mfc/manipulating-image-lists.md)  
  
-   [从图像列表绘制图像](../mfc/drawing-images-from-an-image-list.md)  
  
-   [图像列表中的图像覆盖](../mfc/image-overlays-in-image-lists.md)  
  
-   [从图像列表拖动图像](../mfc/dragging-images-from-an-image-list.md)  
  
-   [图像列表中的图像信息](../mfc/image-information-in-image-lists.md)  
  
## 请参阅  
 [控件](../mfc/controls-mfc.md)