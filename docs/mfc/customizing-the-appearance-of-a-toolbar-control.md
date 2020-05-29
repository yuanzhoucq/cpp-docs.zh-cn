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
ms.openlocfilehash: 9f4f9d90113d5074555d1b0cc411f854abc67fe5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377467"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>自定义工具栏控件的外观

类`CToolBarCtrl`提供了许多样式，这些样式会影响工具栏对象的外观（偶尔也会影响行为）。 在首次创建工具栏控件时，通过`dwCtrlStyle`设置`CToolBarCtrl::Create`（或`CToolBar::CreateEx`） 成员函数的参数来修改工具栏对象。

以下样式会影响工具栏按钮的"3D"方面和按钮文本的位置：

- **TBSTYLE_FLAT**创建工具栏和按钮都透明的平面工具栏。 按钮文本显示在按钮位图下。 使用此样式时，光标下方的按钮将自动突出显示。

- **TBSTYLE_TRANSPARENT**创建透明工具栏。 在透明工具栏中，工具栏是透明的，但按钮不是。 按钮文本显示在按钮位图下。

- **TBSTYLE_LIST**将按钮文本放在按钮位图的右侧。

> [!NOTE]
> 为了防止重新绘制问题，应在工具栏对象可见之前设置**TBSTYLE_FLAT**和**TBSTYLE_TRANSPARENT**样式。

以下样式确定工具栏是否允许用户使用拖放重新定位工具栏对象中的单个按钮：

- **TBSTYLE_ALTDRAG**允许用户通过按住 ALT 时拖动工具栏按钮的位置来更改它的位置。 如果未指定此样式，则用户必须在拖动按钮时按住 SHIFT。

    > [!NOTE]
    >  必须指定**CCS_ADJUSTABLE**样式才能拖动工具栏按钮。

- **TBSTYLE_REGISTERDROP**生成**TBN_GETOBJECT**通知消息，当鼠标指针通过工具栏按钮时请求放置目标对象。

其余样式会影响工具栏对象的可视和非可视方面：

- **TBSTYLE_WRAPABLE**创建可以具有多行按钮的工具栏。 当工具栏变得太窄而无法包含同一行上的所有按钮时，工具栏按钮可以"换行"到下一行。 换行发生在分离和非组边界上。

- **TBSTYLE_CUSTOMERASE**在**NM_CUSTOMDRAW处理****WM_ERASEBKGND**消息时生成通知消息。

- **TBSTYLE_TOOLTIPS**创建工具提示控件，应用程序可以使用该控件在工具栏中显示按钮的描述性文本。

有关工具栏样式和扩展样式的完整列表，请参阅 Windows SDK 中的[工具栏控件和按钮样式](/windows/win32/Controls/toolbar-control-and-button-styles)以及[工具栏扩展样式](/windows/win32/Controls/toolbar-extended-styles)。

## <a name="see-also"></a>另请参阅

[使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
