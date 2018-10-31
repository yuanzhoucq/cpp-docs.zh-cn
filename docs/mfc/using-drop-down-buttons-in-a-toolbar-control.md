---
title: 使用工具栏控件中的下拉列表按钮 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TBN_DROPDOWN
- TBSTYLE_EX_DRAWDDARROWS
dev_langs:
- C++
helpviewer_keywords:
- CToolBarCtrl class [MFC], drop-down buttons
- toolbars [MFC], drop-down buttons
- drop-down buttons in toolbars
- TBSTYLE_EX_DRAWDDARROWS
- TBN_DROPDOWN notification [MFC]
ms.assetid: b859f758-d2f6-40d9-9c26-0ff61993b9b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e58b6b9d64111e021586fc23a985f31c0edf9de
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063765"
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>使用工具栏控件中的下拉按钮

除了标准按钮，工具栏也可以有下拉按钮。 通常由存在附加下的箭头指示下拉按钮。

> [!NOTE]
>  仅当已设置扩展样式 TBSTYLE_EX_DRAWDDARROWS，将显示附加向下箭头。

当用户单击此箭头 （或本身，如果存在则没有箭头的按钮） 时，TBN_DROPDOWN 通知消息发送到工具栏控件的父级。 然后可以处理此通知，并显示一个弹出菜单;类似于 Internet Explorer 的行为。

以下过程演示如何实现一个弹出菜单的下拉工具栏按钮：

### <a name="to-implement-a-drop-down-button"></a>若要实现下拉按钮

1. 一次你`CToolBarCtrl`创建对象、 设置 TBSTYLE_EX_DRAWDDARROWS 样式，使用以下代码：

   [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]

1. 为任何新设置 TBSTYLE_DROPDOWN 样式 ([InsertButton](../mfc/reference/ctoolbarctrl-class.md#insertbutton)或[AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)) 的或现有的 ([SetButtonInfo](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)) 将为下拉按钮的按钮。 下面的示例演示如何修改中的现有按钮`CToolBarCtrl`对象：

   [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]

1. 将 TBN_DROPDOWN 处理程序添加到工具栏对象的父类。

   [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]

1. 在新的处理程序，显示相应的弹出菜单。 下面的代码演示了一种方法：

   [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]

## <a name="see-also"></a>请参阅

[使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

