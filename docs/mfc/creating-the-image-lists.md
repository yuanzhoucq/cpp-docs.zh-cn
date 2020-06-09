---
title: 创建图像列表
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: bbba01a6a8e08ea53e164656733aa06e03dd87a7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625947"
---
# <a name="creating-the-image-lists"></a>创建图像列表

无论你使用的是[CListView](reference/clistview-class.md)还是[CListCtrl](reference/clistctrl-class.md)，创建图像列表都是相同的。

> [!NOTE]
> 如果列表控件包含样式，则仅需要图像列表 `LVS_ICON` 。

使用类 `CImageList` 创建一个或多个图像列表（适用于全尺寸图标、小图标和状态）。 请参阅[CImageList](reference/cimagelist-class.md)，然后查看 Windows SDK 中的[列表视图图像列表](/windows/win32/Controls/using-list-view-controls)。

为每个图像列表调用[CListCtrl：： SetImageList](reference/clistctrl-class.md#setimagelist) ;将指针传递到适当的 `CImageList` 对象。

## <a name="see-also"></a>另请参阅

[使用 CListCtrl](using-clistctrl.md)<br/>
[控件](controls-mfc.md)
