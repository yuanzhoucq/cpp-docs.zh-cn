---
title: 更改列表控件样式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dfe08e9e1be0c7473cdf9a5ca040730423006906
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427051"
---
# <a name="changing-list-control-styles"></a>更改列表控件样式

可以更改列表控件的窗口样式 ([CListCtrl](../mfc/reference/clistctrl-class.md)) 在任何时间在创建后。 通过更改窗口样式，您可以更改该控件使用的视图的种类。 例如，若要模拟在资源管理器，可能会提供不同的视图之间切换控件的工具栏按钮或菜单项： 图标视图、 列表视图中，依次类推。

例如，当用户选择菜单项，您可以进行调用[GetWindowLong](/windows/desktop/api/winuser/nf-winuser-getwindowlonga)来检索控件的当前样式，然后调用[SetWindowLong](/windows/desktop/api/winuser/nf-winuser-setwindowlonga)重置样式。 有关详细信息，请参阅[使用列表视图控件](/windows/desktop/Controls/using-list-view-controls)Windows SDK 中。

中列出了可用样式[创建](../mfc/reference/clistctrl-class.md#create)。 样式**LVS_ICON**， **LVS_SMALLICON**， **LVS_LIST**，以及**LVS_REPORT**指定四个列表的控件视图。

## <a name="extended-styles"></a>扩展的样式

除了列表控件的标准样式，还有另一组，称为扩展样式。 这些样式中, 所述[扩展列表视图样式](/windows/desktop/Controls/extended-list-view-styles)Windows SDK 中提供了各种有用的功能，自定义列表控件的行为。 若要实现的行为的某些样式 （如悬停选择），请调用[CListCtrl::SetExtendedStyle](../mfc/reference/clistctrl-class.md#setextendedstyle)，并传递所需的样式。 下面的示例演示了函数调用：

[!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]

> [!NOTE]
>  若要运行的悬停时选择，您还必须是**LVS_EX_ONECLICKACTIVATE**或**LVS_EX_TWOCLICKACTIVATE**开启。

## <a name="see-also"></a>请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

