---
title: 更改列表控件样式
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
ms.openlocfilehash: 5f45e0549c3fc0f5747f8dd12a6310fafd7dd7bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370804"
---
# <a name="changing-list-control-styles"></a>更改列表控件样式

创建列表控件 （[CListCtrl](../mfc/reference/clistctrl-class.md)） 的窗口样式后，您可以随时更改它的窗口样式。 通过更改窗口样式，可以更改控件使用的视图类型。 例如，要模拟资源管理器，可以提供菜单项或工具栏按钮，以便在不同视图之间切换控件：图标视图、列表视图等。

例如，当用户选择菜单项时，您可以调用[GetWindowLong](/windows/win32/api/winuser/nf-winuser-getwindowlongw)以检索控件的当前样式，然后调用[SetWindowLong](/windows/win32/api/winuser/nf-winuser-setwindowlongw)重置样式。 有关详细信息，请参阅在 Windows SDK 中使用[列表视图控件](/windows/win32/Controls/using-list-view-controls)。

可用样式列在["创建](../mfc/reference/clistctrl-class.md#create)" 中。 **样式**LVS_ICON、LVS_SMALLICON、LVS_LIST**LVS_LIST**和**LVS_REPORT**指定四个列表控件视图。 **LVS_SMALLICON**

## <a name="extended-styles"></a>扩展样式

除了列表控件的标准样式外，还有另一个集，称为扩展样式。 这些样式在 Windows SDK 中的[扩展列表视图样式](/windows/win32/Controls/extended-list-view-styles)中讨论，提供了自定义列表控件行为的各种有用功能。 要实现特定样式的行为（如悬停选择），请调用[CListCtrl：：set 扩展样式](../mfc/reference/clistctrl-class.md#setextendedstyle)，传递所需的样式。 以下示例演示函数调用：

[!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]

> [!NOTE]
> 要使悬停选择正常工作，还必须**LVS_EX_ONECLICKACTIVATE或****LVS_EX_TWOCLICKACTIVATE**打开。

## <a name="see-also"></a>另请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
