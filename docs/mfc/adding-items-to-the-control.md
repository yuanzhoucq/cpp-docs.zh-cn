---
title: 向控件添加项
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding items
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
ms.openlocfilehash: 88e008f06fb669db1c13872b1a58555eeb357d86
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304595"
---
# <a name="adding-items-to-the-control"></a>向控件添加项

若要将项添加到列表控件 ([CListCtrl](../mfc/reference/clistctrl-class.md))，调用多个版本之一[InsertItem](../mfc/reference/clistctrl-class.md#insertitem)成员函数，具体取决于您所了解哪些信息。 一个版本采用[LV_ITEM](/windows/desktop/api/commctrl/ns-commctrl-taglvitema)您准备的结构。 因为 `LV_ITEM` 结构包含很多成员，所以您更容易控制列表控件项的特性。

`LV_ITEM` 结构的两个重要成员（与报表视图有关）是 `iItem` 和 `iSubItem` 成员。 `iItem` 成员是结构正在引用的项的从零开始的索引，而 `iSubItem` 成员是子项的从零开始的索引或为零（如果结构包含有关项的信息）。 利用这两个成员，您可以为每个项确定在列表控件位于报表视图中时显示的子项信息的类型和值。 有关详细信息，请参阅[clistctrl:: Setitem](../mfc/reference/clistctrl-class.md#setitem)。

其他成员指定项的文本、图标、状态和项数据。 “项数据”是应用程序定义与列表视图项关联的值。 有关详细信息`LV_ITEM`结构，请参阅[clistctrl:: Getitem](../mfc/reference/clistctrl-class.md#getitem)。

其他版本的 `InsertItem` 采用一个或多个单独值（与 `LV_ITEM` 结构中的成员对应），这样，您便可以只初始化您想支持的成员。 通常，列表控件管理列表项的存储，但您可以改为使用“回调项”在应用程序中存储某些信息。 有关详细信息，请参阅[回调项和回调掩码](../mfc/callback-items-and-the-callback-mask.md)本主题中以及[回调项和回调掩码](/windows/desktop/Controls/using-list-view-controls)Windows SDK 中。

有关详细信息，请参阅[添加列表视图项和子项](/windows/desktop/Controls/using-list-view-controls)。

## <a name="see-also"></a>请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
