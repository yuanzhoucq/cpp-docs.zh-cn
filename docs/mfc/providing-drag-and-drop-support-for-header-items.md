---
title: 为标题项提供拖放支持
ms.date: 11/04/2016
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
ms.openlocfilehash: 21ff14982baac93fac1cf3ee441353c079f4f760
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602964"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>为标题项提供拖放支持

若要为标题项提供拖放支持，请指定 HDS_DRAGDROP 样式。 标题项的拖放支持使用户能够对标题控件的标题项进行重新排序。 默认行为将提供要拖动的标题项的半透明化拖动图像和新位置的可视指示器（如果已拖动标题项）。

为常见的拖放功能，在处理 HDN_BEGINDRAG 和 HDN_ENDDRAG 通知，可以将扩展默认拖放行为。 你还可以通过重写定义拖动图像的外观[cheaderctrl:: Createdragimage](../mfc/reference/cheaderctrl-class.md#createdragimage)成员函数。

> [!NOTE]
>  如果要为列表控件中的一个嵌入标头控件来提供拖放支持，请参阅中的扩展样式部分[更改列表控件样式](../mfc/changing-list-control-styles.md)主题。

## <a name="see-also"></a>请参阅

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)

