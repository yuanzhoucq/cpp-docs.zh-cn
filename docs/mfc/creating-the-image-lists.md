---
title: "创建图像列表 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bfb42dc2c14b5092aeb667ea22008abe4d581a6f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="creating-the-image-lists"></a>创建图像列表
创建图像列表是相同，无论你使用[CListView](../mfc/reference/clistview-class.md)或[CListCtrl](../mfc/reference/clistctrl-class.md)。  
  
> [!NOTE]
>  你仅需要图像列表如果列表控件包含`LVS_ICON`样式。  
  
 使用类`CImageList`创建 （用于完全尺寸的图标、 小图标和状态） 的一个或多个图像列表。 请参阅[CImageList](../mfc/reference/cimagelist-class.md)，请参阅和[列表视图图像列表](http://msdn.microsoft.com/library/windows/desktop/bb774736)Windows SDK 中。  
  
 调用[CListCtrl::SetImageList](../mfc/reference/clistctrl-class.md#setimagelist)每个映像列表; 将指针传递到相应`CImageList`对象。  
  
## <a name="see-also"></a>请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)

