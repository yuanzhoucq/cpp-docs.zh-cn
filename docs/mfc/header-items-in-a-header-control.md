---
title: 标题控件中的标题项
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], header items in
- header items in header controls [MFC]
- CHeaderCtrl class [MFC], header items in
- controls [MFC], header
ms.assetid: ac79ef1f-a671-4ab2-93e9-b1aa016a48bf
ms.openlocfilehash: a70d1d9225d2ac8ef2f7ed3ad9f603a64a937bc7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620087"
---
# <a name="header-items-in-a-header-control"></a>标题控件中的标题项

您对构成标题控件（[CHeaderCtrl](reference/cheaderctrl-class.md)）的标头项的外观和行为具有相当大的控制权。 每个标题项可以有一个字符串、一个位图化图像、一个关联图像列表中的图像或一个与之关联的应用程序定义的 32 位值。 字符串、位图或图像显示在标题项中。

在创建新项时，可以通过调用[CHeaderCtrl：： InsertItem](reference/cheaderctrl-class.md#insertitem)或通过修改现有项来自定义新项的外观和内容，同时调用[CHeaderCtrl：： GetItem](reference/cheaderctrl-class.md#getitem)和[CHeaderCtrl：： SetItem](reference/cheaderctrl-class.md#setitem)。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [自定义标题项的外观](customizing-the-header-item-s-appearance.md)

- [对标头控件中的项进行排序](ordering-items-in-the-header-control.md)

- [为标题项提供拖放支持](providing-drag-and-drop-support-for-header-items.md)

- [对标题控件使用图像列表](using-image-lists-with-header-controls.md)

## <a name="see-also"></a>另请参阅

[使用 CHeaderCtrl](using-cheaderctrl.md)
