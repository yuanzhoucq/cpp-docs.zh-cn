---
title: 向控件添加项
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding items
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
ms.openlocfilehash: 6c03be6f04746ec2e3146916d72cad637a204187
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509325"
---
# <a name="adding-items-to-the-control"></a>向控件添加项

若要将项添加到列表控件 ([CListCtrl](../mfc/reference/clistctrl-class.md)), 请调用[InsertItem](../mfc/reference/clistctrl-class.md#insertitem)成员函数的多个版本中的一个, 具体取决于所拥有的信息。 一个版本采用您准备的[LVITEM](/windows/win32/api/commctrl/ns-commctrl-lvitemw)结构。 因为 `LVITEM` 结构包含很多成员，所以您更容易控制列表控件项的特性。

          `LVITEM` 结构的两个重要成员（与报表视图有关）是 `iItem` 和 `iSubItem` 成员。           `iItem` 成员是结构正在引用的项的从零开始的索引，而 `iSubItem` 成员是子项的从零开始的索引或为零（如果结构包含有关项的信息）。 利用这两个成员，您可以为每个项确定在列表控件位于报表视图中时显示的子项信息的类型和值。 有关详细信息, 请参阅[CListCtrl:: SetItem](../mfc/reference/clistctrl-class.md#setitem)。

其他成员指定项的文本、图标、状态和项数据。 “项数据”是应用程序定义与列表视图项关联的值。 有关`LVITEM`结构的详细信息, 请参阅[CListCtrl:: GetItem](../mfc/reference/clistctrl-class.md#getitem)。

其他版本的 `InsertItem` 采用一个或多个单独值（与 `LVITEM` 结构中的成员对应），这样，您便可以只初始化您想支持的成员。 通常，列表控件管理列表项的存储，但您可以改为使用“回调项”在应用程序中存储某些信息。 有关详细信息, 请参阅本主题中的[回调项和回调掩码](../mfc/callback-items-and-the-callback-mask.md)和 Windows SDK 中的[回调项和回调掩码](/windows/win32/Controls/using-list-view-controls)。

有关详细信息, 请参阅[添加列表视图项和子项](/windows/win32/Controls/using-list-view-controls)。

## <a name="see-also"></a>请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
