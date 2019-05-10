---
title: 树控件父项和子项
ms.date: 11/04/2016
helpviewer_keywords:
- parent items in CTreeCtrl [MFC]
- child items in tree control [MFC]
- CTreeCtrl class [MFC], parent and child items
- tree controls [MFC], parent and child items
ms.assetid: abcea1e4-fe9b-40d9-86dc-1db235f8f103
ms.openlocfilehash: 2961009e3f1b21c3caacec001c53f5e52740dd67
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62181659"
---
# <a name="tree-control-parent-and-child-items"></a>树控件父项和子项

树控件中的任意项 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 可以具有一组称为子项目，与之关联的子项。 具有一个或多个子项的项称为“父项”。 子项显示在其父项下，可能指示其是父级的下属。 没有父级的项位于层次结构顶部，称为“根项”。

在任何给定时间，子项的父项列表的状态都可以为展开或折叠。 在状态为展开时，子项将显示在父项下。 当状态为折叠时，子项不会显示。 列表会自动切换展开和折叠状态之间或在用户双击父项时如果父任务具有**TVS_HASBUTTONS**样式，当用户单击与父项关联的按钮。 应用程序可以展开或折叠子项目通过使用[展开](../mfc/reference/ctreectrl-class.md#expand)成员函数。

通过调用添加到树控件项[InsertItem](../mfc/reference/ctreectrl-class.md#insertitem)成员函数。 此函数返回的句柄**HTREEITEM**唯一标识项的类型。 添加项时，您必须为新项的父项指定句柄。 如果指定**NULL**或**TVI_ROOT**值而不是中的父项句柄[TVINSERTSTRUCT](/windows/desktop/api/commctrl/ns-commctrl-tagtvinsertstructa)结构或*hParent*参数，该项将添加作为根项。

树控件将发送[TVN_ITEMEXPANDING](/windows/desktop/Controls/tvn-itemexpanding)通知消息来展开或折叠父项的子项列表时。 此通知为您提供了阻止更改或设置依赖于子项列表状态的父项的任何特性。 更改后的状态的列表，树控件将发送[TVN_ITEMEXPANDED](/windows/desktop/Controls/tvn-itemexpanded)通知消息。

子项列表展开后，则将相对于父项缩进。 可以通过设置缩进量[SetIndent](../mfc/reference/ctreectrl-class.md#setindent)成员函数或检索当前使用量[GetIndent](../mfc/reference/ctreectrl-class.md#getindent)成员函数。

## <a name="see-also"></a>请参阅

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控件](../mfc/controls-mfc.md)
