---
title: 为标题项提供拖放支持
ms.date: 11/04/2016
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
ms.openlocfilehash: 8dfaabf3da62c216d3da662f59c57b63e695d9ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371163"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>为标题项提供拖放支持

要为标头项提供拖放支持，请指定HDS_DRAGDROP样式。 标题项的拖放支持使用户能够对标题控件的标题项进行重新排序。 默认行为将提供要拖动的标题项的半透明化拖动图像和新位置的可视指示器（如果已拖动标题项）。

利用常见的拖放功能，您可以通过处理 HDN_BEGINDRAG 和 HDN_ENDDRAG 通知来扩展默认的拖放行为。 您还可以通过重写[CHeaderCtrl：：CreateDragImage](../mfc/reference/cheaderctrl-class.md#createdragimage)成员函数来自定义拖动图像的外观。

> [!NOTE]
> 如果要在列表控件中为嵌入标头控件提供拖放支持，请参阅["更改列表控件样式"](../mfc/changing-list-control-styles.md)主题中的"扩展样式"部分。

## <a name="see-also"></a>另请参阅

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)
