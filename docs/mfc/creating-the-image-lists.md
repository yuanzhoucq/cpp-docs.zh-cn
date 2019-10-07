---
title: 创建图像列表
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: 6687b62b70103894d957a21019008e8781385feb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508780"
---
# <a name="creating-the-image-lists"></a>创建图像列表

无论你使用的是[CListView](../mfc/reference/clistview-class.md)还是[CListCtrl](../mfc/reference/clistctrl-class.md), 创建图像列表都是相同的。

> [!NOTE]
>  如果列表控件包含`LVS_ICON`样式, 则仅需要图像列表。

使用类`CImageList`创建一个或多个图像列表 (适用于全尺寸图标、小图标和状态)。 请参阅[CImageList](../mfc/reference/cimagelist-class.md), 然后查看 Windows SDK 中的[列表视图图像列表](/windows/win32/Controls/using-list-view-controls)。

为每个图像列表调用[CListCtrl:: SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) ;将指针传递到适当`CImageList`的对象。

## <a name="see-also"></a>请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
