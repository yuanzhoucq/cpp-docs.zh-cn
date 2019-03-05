---
title: 对标题控件中的项排序
ms.date: 11/04/2016
f1_keywords:
- DS_DRAGDROP
helpviewer_keywords:
- sequence [MFC]
- sequence [MFC], header control items
- OrderToIndex method [MFC]
- DS_DRAGDROP notification [MFC]
- GetOrderArray method [MFC]
- SetOrderArray method [MFC]
- header controls [MFC], ordering items
ms.assetid: 5aaef872-75b5-49c5-8fed-6f9a81fca812
ms.openlocfilehash: bae351d921c25993d6b7029f9052e1938179673b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282011"
---
# <a name="ordering-items-in-the-header-control"></a>对标题控件中的项排序

后[项添加到标头控件](../mfc/adding-items-to-the-header-control.md)，可以对操作或获取有关它们的顺序使用以下函数的信息：

- [Cheaderctrl:: Getorderarray](../mfc/reference/cheaderctrl-class.md#getorderarray)和[cheaderctrl:: Setorderarray](../mfc/reference/cheaderctrl-class.md#setorderarray)

   检索和设置标题项的从左到右的顺序。

- [CHeaderCtrl::OrderToIndex](../mfc/reference/cheaderctrl-class.md#ordertoindex)。

   检索特定标题项的索引值。

除了前面成员函数，HDS_DRAGDROP 样式也可以让用户拖放到标头控件中的标头项。 有关详细信息，请参阅[提供的标头项的拖放支持](../mfc/providing-drag-and-drop-support-for-header-items.md)。

## <a name="see-also"></a>请参阅

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)
