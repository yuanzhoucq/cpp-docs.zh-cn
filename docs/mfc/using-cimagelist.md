---
title: "使用 CImageList |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CImageList
dev_langs: C++
helpviewer_keywords:
- image list control
- CImageList class [MFC], using
ms.assetid: 3d2a909e-d641-46b7-aada-81cab1a29b41
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 053e670b5a6d932c50e2f967ee38cf9191710ff4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-cimagelist"></a>使用 CImageList
图像列表，表示由类[CImageList](../mfc/reference/cimagelist-class.md)，是相同大小的图像，其中每个可以按其索引引用的集合。 图像列表用于有效地管理大的图标或位图集。 图像列表本身不是控件由于它们不是 windows;但是，它们用于多种不同类型的控件，包括列表控件 ([CListCtrl](../mfc/reference/clistctrl-class.md))，树控件 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md))，和选项卡控件 ([CTabCtrl](../mfc/reference/ctabctrl-class.md))。  
  
 图像列表中的所有图像包含在一个采用屏幕设备格式的宽位图中。 图像列表可能包含一个单色位图，该位图包含用于透明地绘制图像的蒙板（图标样式）。 `CImageList` 提供可让您绘制图像、创建和销毁图像列表、添加和移除图像、替换图像、合并图像以及拖动图像的成员函数。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [图像列表类型](../mfc/types-of-image-lists.md)  
  
-   [使用图像列表](../mfc/using-an-image-list.md)  
  
-   [操作图像列表](../mfc/manipulating-image-lists.md)  
  
-   [通过图像列表绘制图像](../mfc/drawing-images-from-an-image-list.md)  
  
-   [图像列表中的图像覆盖](../mfc/image-overlays-in-image-lists.md)  
  
-   [从图像列表中拖动图像](../mfc/dragging-images-from-an-image-list.md)  
  
-   [图像列表中的图像信息](../mfc/image-information-in-image-lists.md)  
  
## <a name="see-also"></a>请参阅  
 [控件](../mfc/controls-mfc.md)

