---
title: 向控件添加项
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding items
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
ms.openlocfilehash: 5cc1c7a921cf6d6ba2c0f968012b48bfcaef0658
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623369"
---
# <a name="adding-items-to-the-control"></a>向控件添加项

若要将项添加到列表控件（[CListCtrl](reference/clistctrl-class.md)），请调用[InsertItem](reference/clistctrl-class.md#insertitem)成员函数的多个版本中的一个，具体取决于所拥有的信息。 一个版本采用您准备的[LVITEM](/windows/win32/api/commctrl/ns-commctrl-lvitemw)结构。 因为 `LVITEM` 结构包含很多成员，所以您更容易控制列表控件项的特性。

`LVITEM` 结构的两个重要成员（与报表视图有关）是 `iItem` 和 `iSubItem` 成员。 `iItem` 成员是结构正在引用的项的从零开始的索引，而 `iSubItem` 成员是子项的从零开始的索引或为零（如果结构包含有关项的信息）。 利用这两个成员，您可以为每个项确定在列表控件位于报表视图中时显示的子项信息的类型和值。 有关详细信息，请参阅[CListCtrl：： SetItem](reference/clistctrl-class.md#setitem)。

其他成员指定项的文本、图标、状态和项数据。 “项数据”是应用程序定义与列表视图项关联的值。 有关结构的详细信息 `LVITEM` ，请参阅[CListCtrl：： GetItem](reference/clistctrl-class.md#getitem)。

其他版本的 `InsertItem` 采用一个或多个单独值（与 `LVITEM` 结构中的成员对应），这样，您便可以只初始化您想支持的成员。 通常，列表控件管理列表项的存储，但您可以改为使用“回调项”在应用程序中存储某些信息。 有关详细信息，请参阅本主题中的[回调项和回调掩码](callback-items-and-the-callback-mask.md)和 Windows SDK 中的[回调项和回调掩码](/windows/win32/Controls/using-list-view-controls)。

有关详细信息，请参阅[添加列表视图项和子项](/windows/win32/Controls/using-list-view-controls)。

## <a name="see-also"></a>另请参阅

[使用 CListCtrl](using-clistctrl.md)<br/>
[控件](controls-mfc.md)
