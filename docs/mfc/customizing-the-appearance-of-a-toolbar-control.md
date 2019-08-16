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
ms.openlocfilehash: 590f0dce6c50ee6d0ca30c4c68e21787563bd686
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508726"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>自定义工具栏控件的外观

类`CToolBarCtrl`提供许多样式, 它们会影响 toolbar 对象的外观 (有时也是行为)。 首次创建 toolbar 控件时, `dwCtrlStyle`可以通过设置`CToolBarCtrl::Create` (或`CToolBar::CreateEx`) 成员函数的参数来修改 toolbar 对象。

以下样式会影响工具栏按钮的 "三维" 方面以及按钮文本的位置:

- **TBSTYLE_FLAT**创建一个平面工具栏, 其中的工具栏和按钮都是透明的。 按钮文本显示在 "按钮位图" 下。 使用此样式时, 将自动突出显示光标下的按钮。

- **TBSTYLE_TRANSPARENT**创建透明工具栏。 在透明工具栏中, 工具栏是透明的, 但按钮不透明。 按钮文本显示在 "按钮位图" 下。

- **TBSTYLE_LIST**将按钮文本置于按钮位图的右侧。

> [!NOTE]
>  若要防止重绘问题, 应在工具栏对象可见之前设置**TBSTYLE_FLAT**和**TBSTYLE_TRANSPARENT**样式。

以下样式确定工具栏是否允许用户使用拖放操作在工具栏对象内重新定位单个按钮:

- **TBSTYLE_ALTDRAG**允许用户通过在按住 ALT 的同时拖动工具栏按钮来更改工具栏按钮的位置。 如果未指定此样式, 则用户必须在拖动按钮时按住 SHIFT 键。

    > [!NOTE]
    >  若要拖动工具栏按钮, 必须指定**CCS_ADJUSTABLE**样式。

- **TBSTYLE_REGISTERDROP**当鼠标指针移到工具栏按钮上时, 将生成**TBN_GETOBJECT**通知消息, 以请求删除目标对象。

其余样式影响 toolbar 对象的视觉和非可视方面:

- **TBSTYLE_WRAPABLE**创建一个工具栏, 该工具栏可以具有多行按钮。 当工具栏变得太窄, 无法在同一行上包含所有按钮时, 工具栏按钮可以 "换行" 到下一行。 环绕和 nongroup 边界进行包装。

- **TBSTYLE_CUSTOMERASE**当处理**WM_ERASEBKGND**消息时, 将生成**NM_CUSTOMDRAW**通知消息。

- **TBSTYLE_TOOLTIPS**创建一个工具提示控件, 应用程序可以使用该控件在工具栏中显示按钮的描述性文本。

有关工具栏样式和扩展样式的完整列表, 请参阅 Windows SDK 中的[工具栏控件和按钮样式](/windows/win32/Controls/toolbar-control-and-button-styles)和[工具栏扩展样式](/windows/win32/Controls/toolbar-extended-styles)。

## <a name="see-also"></a>请参阅

[使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
