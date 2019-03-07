---
title: 自定义工具栏控件的外观
ms.date: 11/04/2016
f1_keywords:
- TBSTYLE_
helpviewer_keywords:
- flat toolbars
- CToolBar class [MFC], styles
- transparent toolbars
- TBSTYLE_ styles [MFC]
- CToolBarCtrl class [MFC], object styles
- toolbar controls [MFC], style
ms.assetid: fd0a73db-7ad1-4fe4-889b-02c3980f49e8
ms.openlocfilehash: 8a0db3299ebb54d226edc1434dedbc6a04eb9b00
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302333"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>自定义工具栏控件的外观

类`CToolBarCtrl`提供了许多影响外观 （和，有时，行为） 的工具栏对象的样式。 通过设置来修改工具栏对象`dwCtrlStyle`的参数`CToolBarCtrl::Create`(或`CToolBar::CreateEx`) 成员函数，首次创建工具栏控件时。

工具栏按钮的"3D"方面和按钮文本的位置会影响以下样式：

- **TBSTYLE_FLAT**创建透明工具栏和按钮是一个平面工具栏。 按钮文本会显示下按钮位图。 使用此样式时，将自动突出显示光标下的按钮。

- **TBSTYLE_TRANSPARENT**创建透明工具栏。 在透明工具栏中，工具栏是透明的但不是按钮。 按钮文本会显示下按钮位图。

- **TBSTYLE_LIST**位置按钮右侧的按钮位图的文本。

> [!NOTE]
>  若要避免重新绘制问题**TBSTYLE_FLAT**并**TBSTYLE_TRANSPARENT**工具栏对象才会显示应设置样式。

以下样式确定工具栏是否允许用户重新定位各个按钮在工具栏对象使用拖放：

- **TBSTYLE_ALTDRAG**允许用户通过按住 ALT 的同时拖动来更改工具栏按钮的位置。 如果未指定此样式，用户必须按下 SHIFT 的同时拖动按钮。

    > [!NOTE]
    >  **CCS_ADJUSTABLE**必须指定样式以启用要拖动的工具栏按钮。

- **TBSTYLE_REGISTERDROP**生成**TBN_GETOBJECT**通知消息来请求删除目标对象，当鼠标指针经过工具栏按钮。

剩余样式影响 visual 和非可视方面的工具栏对象：

- **TBSTYLE_WRAPABLE**创建可以具有多个行的按钮的工具栏。 工具栏按钮可以"包装"到下一行时工具栏变得过窄而无法包含在同一行上的所有按钮。 分离和行会边界上会发生换行。

- **TBSTYLE_CUSTOMERASE**生成**NM_CUSTOMDRAW**通知消息处理时**WM_ERASEBKGND**消息。

- **TBSTYLE_TOOLTIPS**创建工具提示控件的应用程序可以使用工具栏中显示按钮的描述性文本。

Toolbar 样式和扩展的样式的完整列表，请参阅[工具栏控件和按钮样式](/windows/desktop/Controls/toolbar-control-and-button-styles)并[工具栏上的扩展样式](/windows/desktop/Controls/toolbar-extended-styles)Windows SDK 中。

## <a name="see-also"></a>请参阅

[使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
