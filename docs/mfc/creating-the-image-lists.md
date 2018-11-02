---
title: 创建图像列表
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: 52f375c98b5f73e0f5721c951c94e4b24f0bc224
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608671"
---
# <a name="creating-the-image-lists"></a>创建图像列表

不管您是使用创建图像列表都相同[CListView](../mfc/reference/clistview-class.md)或[CListCtrl](../mfc/reference/clistctrl-class.md)。

> [!NOTE]
>  您仅需要图像列表如果列表控件包含`LVS_ICON`样式。

使用类`CImageList`若要创建一个或多个图像列表 （用于全尺寸图标、 小图标和状态）。 请参阅[CImageList](../mfc/reference/cimagelist-class.md)，并查看[列表视图图像列表](/windows/desktop/Controls/using-list-view-controls)Windows SDK 中。

调用[CListCtrl::SetImageList](../mfc/reference/clistctrl-class.md#setimagelist)每个图像列表; 将指针传递到相应`CImageList`对象。

## <a name="see-also"></a>请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

