---
title: 使用工具栏控件中的下拉按钮
ms.date: 11/04/2016
f1_keywords:
- TBN_DROPDOWN
- TBSTYLE_EX_DRAWDDARROWS
helpviewer_keywords:
- CToolBarCtrl class [MFC], drop-down buttons
- toolbars [MFC], drop-down buttons
- drop-down buttons in toolbars
- TBSTYLE_EX_DRAWDDARROWS
- TBN_DROPDOWN notification [MFC]
ms.assetid: b859f758-d2f6-40d9-9c26-0ff61993b9b2
ms.openlocfilehash: 0bc4df4c07ec4b8bc5b488925cbb140609302186
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365069"
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>使用工具栏控件中的下拉按钮

除了标准按钮外，工具栏还可以具有下拉按钮。 下拉按钮通常由附加的下箭头指示。

> [!NOTE]
> 仅当设置了TBSTYLE_EX_DRAWDDARROWS扩展样式时，才会显示附加的向下箭头。

当用户单击此箭头（或按钮本身，如果没有箭头），TBN_DROPDOWN通知消息发送到工具栏控件的父级。 然后，您可以处理此通知并显示一个弹出式菜单;例如，您可以处理此通知并显示一个弹出式菜单。类似于 Internet 资源管理器的行为。

以下过程演示如何使用弹出式菜单实现下拉工具栏按钮：

### <a name="to-implement-a-drop-down-button"></a>实现下拉按钮

1. 创建`CToolBarCtrl`对象后，请使用以下代码设置TBSTYLE_EX_DRAWDDARROWS样式：

   [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]

1. 设置任何新 （[插入按钮](../mfc/reference/ctoolbarctrl-class.md#insertbutton)或[附加按钮](../mfc/reference/ctoolbarctrl-class.md#addbuttons)） 或将成为下拉按钮的现有[（SetButtonInfo）](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)按钮的TBSTYLE_DROPDOWN样式。 以下示例演示了修改`CToolBarCtrl`对象中的现有按钮：

   [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]

1. 将TBN_DROPDOWN处理程序添加到工具栏对象的父类。

   [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]

1. 在新处理程序中，显示相应的弹出菜单。 以下代码演示了一种方法：

   [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]

## <a name="see-also"></a>另请参阅

[使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
