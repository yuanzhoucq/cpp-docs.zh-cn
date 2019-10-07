---
title: 树控件项状态概述
ms.date: 11/04/2016
helpviewer_keywords:
- states, CTreeCtrl items
- tree controls [MFC], item states overview
- CTreeCtrl class [MFC], item states
ms.assetid: 2db11ae0-0d87-499d-8c1f-5e0dbe9e94c8
ms.openlocfilehash: bbeabf69f174fcf172808ff71f07ed05f1dc9675
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511041"
---
# <a name="tree-control-item-states-overview"></a>树控件项状态概述

树控件 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 中的每一项都具有当前状态。 例如，可以选择、禁用、展开项等等。 在大多数情况下，树控件将自动设置项的状态以反映用户操作，例如选择了某个项。 不过, 还可以使用[SetItemState](../mfc/reference/ctreectrl-class.md#setitemstate)成员函数设置项的状态, 并使用[GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate)成员函数检索项的当前状态。 有关项状态的完整列表, 请参阅 Windows SDK 中的[树视图控件常量](/windows/win32/Controls/tree-view-control-item-states)。

项的当前状态由*nState*参数指定。 树控件可能更改项的状态以反映用户操作，例如选择该项或将焦点设置为该项。 此外，应用程序可能更改项的状态来禁用或隐藏项，或指定覆盖图像或状态图像。

当你指定或更改项的状态时, *nStateMask*参数指定要设置的状态位, 而*nState*参数包含这些位的新值。 例如, 下面的示例将`CTreeCtrl`对象 (`m_treeCtrl`) 中的父项 (由 hParentItem 指定) 的当前状态更改为: `TVIS_EXPANDPARTIAL`

[!code-cpp[NVC_MFCControlLadenDialog#71](../mfc/codesnippet/cpp/tree-control-item-states-overview_1.cpp)]

更改状态的另一个示例是设置项的覆盖图像。 若要实现此目的, *nStateMask*必须`TVIS_OVERLAYMASK`包含值, *nState*必须包含覆盖图像的从1开始的索引, 该索引使用[INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask)宏向左移动了八位。 索引可以为 0 以表示没有覆盖图像。 必须通过对[CImageList:: SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage)函数的上一个调用将覆盖映像添加到树控件的覆盖图像列表中。 函数指定要添加的图像的从1开始的索引;这是与 INDEXTOOVERLAYMASK 宏一起使用的索引。 一个树控件最多可拥有四个覆盖图像。

若要设置项的状态图像, *nStateMask*必须包含`TVIS_STATEIMAGEMASK`该值, 并且*nState*必须包含通过使用[INDEXTOSTATEIMAGEMASK](/windows/win32/api/commctrl/nf-commctrl-indextostateimagemask)宏向左移动12位的状态图像的从1开始的索引。 索引可以为 0 以表示没有状态图像。 有关覆盖和状态图像的详细信息, 请参阅[树控件图像列表](../mfc/tree-control-image-lists.md)。

## <a name="see-also"></a>请参阅

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控件](../mfc/controls-mfc.md)
