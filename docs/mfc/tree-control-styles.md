---
title: 树控件样式
ms.date: 11/04/2016
f1_keywords:
- TVS_SINGLEEXPAND
- TVS_LINESATROOT
- TVS_HASBUTTONS
- TVS_NOTOOLTIPS
- TVS_HASLINES
helpviewer_keywords:
- TVS_LINESATROOT [MFC]
- styles [MFC], CTreeCtrl
- styles [MFC], tree control
- TVS_HASLINES
- TVS_SINGLEEXPAND
- CTreeCtrl class [MFC], styles
- TVS_EDITLABELS [MFC]
- TVS_NOTOOLTIPS [MFC]
- TVS_HASBUTTONS [MFC]
- tree controls [MFC], styles
ms.assetid: f43faebd-a355-479e-888a-bf0673d5e1b4
ms.openlocfilehash: f5f28025d0349e9bcd95aba50d4110d304fed376
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510936"
---
# <a name="tree-control-styles"></a>树控件样式

树控件 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 样式控制树控件外观的各个方面。 您可以在创建树控件时设置初始样式。 可以通过使用[GetWindowLong](/windows/win32/api/winuser/nf-winuser-getwindowlongw)和[SetWindowLong](/windows/win32/api/winuser/nf-winuser-setwindowlongw) Windows 函数来检索和更改样式, 并为*nIndex*参数指定**GWL_STYLE** 。 有关样式的完整列表, 请参阅 Windows SDK 中的[树视图控件窗口样式](/windows/win32/Controls/tree-view-control-window-styles)。

**TVS_HASLINES**样式通过绘制将子项链接到相应父项的线条, 增强了树控件层次结构的图形表示。 此样式不链接层次结构根位置的项。 为此, 需要将**TVS_HASLINES**和**TVS_LINESATROOT**样式组合在一起。

用户可以通过双击父项来展开或折叠父项的子项列表。 具有**TVS_SINGLEEXPAND**样式的树控件将导致选定项展开并取消选择要折叠的项。 如果使用鼠标单击选定项并且该项已关闭, 则将其展开。 如果选择的项是打开的, 则会被折叠。

具有**TVS_HASBUTTONS**样式的树控件向每个父项的左侧添加一个按钮。 用户可以单击该按钮展开或折叠子项, 作为双击父项的替代方法。 **TVS_HASBUTTONS**不会将按钮添加到位于层次结构的根处的项。 为此, 必须将**TVS_HASLINES**、 **TVS_LINESATROOT**和**TVS_HASBUTTONS**组合在一起。

**TVS_EDITLABELS**样式使用户可以编辑树控件项的标签。 有关编辑标签的详细信息, 请参阅本主题后面的[树控件标签编辑](../mfc/tree-control-label-editing.md)。

**TVS_NOTOOLTIPS**样式禁用树视图控件的自动工具提示功能。 如果整个标题当前不可见, 则此功能会自动显示工具提示, 其中包含鼠标光标下的项的标题。

## <a name="see-also"></a>请参阅

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控件](../mfc/controls-mfc.md)
