---
title: 使用 CImageList
ms.date: 11/04/2016
helpviewer_keywords:
- image list control
- CImageList class [MFC], using
ms.assetid: 3d2a909e-d641-46b7-aada-81cab1a29b41
ms.openlocfilehash: 09fd0e95ce2981afbebbfe10d87b26f88a7b5e13
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447235"
---
# <a name="using-cimagelist"></a>使用 CImageList

由[CImageList](../mfc/reference/cimagelist-class.md)类表示的图像列表是大小相同的图像的集合，其中每个图像都可以通过其索引来引用。 图像列表用于有效地管理大的图标或位图集。 图像列表本身并不是控件，因为它们不是 windows;但是，它们用于多种不同类型的控件，包括列表控件（[CListCtrl](../mfc/reference/clistctrl-class.md)）、树控件（[CTreeCtrl](../mfc/reference/ctreectrl-class.md)）和选项卡控件（[CTabCtrl](../mfc/reference/ctabctrl-class.md)）。

图像列表中的所有图像包含在一个采用屏幕设备格式的宽位图中。 图像列表可能包含一个单色位图，该位图包含用于透明地绘制图像的蒙板（图标样式）。 `CImageList` 提供可让您绘制图像、创建和销毁图像列表、添加和移除图像、替换图像、合并图像以及拖动图像的成员函数。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [图像列表类型](../mfc/types-of-image-lists.md)

- [使用图像列表](../mfc/using-an-image-list.md)

- [操作图像列表](../mfc/manipulating-image-lists.md)

- [通过图像列表绘制图像](../mfc/drawing-images-from-an-image-list.md)

- [图像列表中的图像覆盖](../mfc/image-overlays-in-image-lists.md)

- [从图像列表中拖动图像](../mfc/dragging-images-from-an-image-list.md)

- [图像列表中的图像信息](../mfc/image-information-in-image-lists.md)

## <a name="see-also"></a>另请参阅

[控件](../mfc/controls-mfc.md)
