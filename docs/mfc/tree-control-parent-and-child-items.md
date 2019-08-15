---
title: 树控件父项和子项
ms.date: 11/04/2016
helpviewer_keywords:
- parent items in CTreeCtrl [MFC]
- child items in tree control [MFC]
- CTreeCtrl class [MFC], parent and child items
- tree controls [MFC], parent and child items
ms.assetid: abcea1e4-fe9b-40d9-86dc-1db235f8f103
ms.openlocfilehash: 5a02194ccef8eca81971bb4e8ae24d859e578bcc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513973"
---
# <a name="tree-control-parent-and-child-items"></a>树控件父项和子项

树控件 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 中的任何项都可以具有子项列表 (这些子项称为子项目)。 具有一个或多个子项的项称为“父项”。 子项显示在其父项下，可能指示其是父级的下属。 没有父级的项位于层次结构顶部，称为“根项”。

在任何给定时间，子项的父项列表的状态都可以为展开或折叠。 在状态为展开时，子项将显示在父项下。 当状态为折叠时，子项不会显示。 当用户双击父项时, 列表自动在展开和折叠状态之间切换; 如果父项具有**TVS_HASBUTTONS**样式, 则在用户单击与父项关联的按钮时自动切换。 应用程序可以通过使用[展开](../mfc/reference/ctreectrl-class.md#expand)成员函数来展开或折叠子项目。

可以通过调用[InsertItem](../mfc/reference/ctreectrl-class.md#insertitem)成员函数向树控件添加项。 此函数返回一个**HTREEITEM**类型的句柄, 它唯一地标识项。 添加项时，您必须为新项的父项指定句柄。 如果在[TVINSERTSTRUCT](/windows/win32/api/commctrl/ns-commctrl-tvinsertstructw)结构或*hParent*参数中指定**NULL**或**TVI_ROOT**值, 而不是父项句柄, 则该项将添加为根项。

当父项的子项列表将要展开或折叠时, 树控件将发送[TVN_ITEMEXPANDING](/windows/win32/Controls/tvn-itemexpanding)通知消息。 此通知为您提供了阻止更改或设置依赖于子项列表状态的父项的任何特性。 更改列表的状态后, 树控件将发送[TVN_ITEMEXPANDED](/windows/win32/Controls/tvn-itemexpanded)通知消息。

子项列表展开后，则将相对于父项缩进。 您可以使用[SetIndent](../mfc/reference/ctreectrl-class.md#setindent)成员函数设置缩进量, 或使用[GetIndent](../mfc/reference/ctreectrl-class.md#getindent)成员函数检索当前数量。

## <a name="see-also"></a>请参阅

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控件](../mfc/controls-mfc.md)
