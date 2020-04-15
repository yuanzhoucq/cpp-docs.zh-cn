---
title: 创建图像列表
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: 440ab6fdfe7663557f6c6a6607e617c793d26674
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371571"
---
# <a name="creating-the-image-lists"></a>创建图像列表

无论您使用[CListView](../mfc/reference/clistview-class.md)还是[CListCtrl，](../mfc/reference/clistctrl-class.md)创建图像列表都是相同的。

> [!NOTE]
> 仅当列表控件包含样式时，`LVS_ICON`才需要图像列表。

使用类`CImageList`创建一个或多个图像列表（对于全尺寸图标、小图标和状态）。 请参阅[CImageList](../mfc/reference/cimagelist-class.md)，并查看 Windows SDK 中的[列表视图映像列表](/windows/win32/Controls/using-list-view-controls)。

调用[CListCtrl：为每个图像列表设置图像列表](../mfc/reference/clistctrl-class.md#setimagelist);将指针传递给相应的`CImageList`对象。

## <a name="see-also"></a>另请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
