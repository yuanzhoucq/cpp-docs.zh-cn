---
title: 树控件项状态概述
ms.date: 11/04/2016
helpviewer_keywords:
- states, CTreeCtrl items
- tree controls [MFC], item states overview
- CTreeCtrl class [MFC], item states
ms.assetid: 2db11ae0-0d87-499d-8c1f-5e0dbe9e94c8
ms.openlocfilehash: 389c273f7c8727ecbb4ed5455987126e21e26a63
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467946"
---
# <a name="tree-control-item-states-overview"></a>树控件项状态概述

树控件中的每个项 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 具有一个当前状态。 例如，可以选择、禁用、展开项等等。 在大多数情况下，树控件将自动设置项的状态以反映用户操作，例如选择了某个项。 但是，您还可以通过设置项的状态[SetItemState](../mfc/reference/ctreectrl-class.md#setitemstate)成员函数，并检索使用的项的当前状态[GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate)成员函数。 项状态的完整列表，请参阅[树视图控件常量](/windows/desktop/Controls/tree-view-control-item-states)Windows SDK 中。

通过指定项的当前状态*nState*参数。 树控件可能更改项的状态以反映用户操作，例如选择该项或将焦点设置为该项。 此外，应用程序可能更改项的状态来禁用或隐藏项，或指定覆盖图像或状态图像。

指定或更改项的状态时*nStateMask*参数指定的状态位，若要设置，并*nState*参数包含这些位的新值。 例如，下面的示例更改父项的当前状态 (由指定*hParentItem*) 中`CTreeCtrl`对象 (`m_treeCtrl`) 到`TVIS_EXPANDPARTIAL`:

[!code-cpp[NVC_MFCControlLadenDialog#71](../mfc/codesnippet/cpp/tree-control-item-states-overview_1.cpp)]

更改状态的另一个示例是设置项的覆盖图像。 若要完成此操作，请*nStateMask*必须包括`TVIS_OVERLAYMASK`值，和*nState*必须包含一个基于移动该覆盖图像左索引八位使用[INDEXTOOVERLAYMASK](/windows/desktop/api/commctrl/nf-commctrl-indextooverlaymask)宏。 索引可以为 0 以表示没有覆盖图像。 覆盖图像必须具有已添加到树控件的列表覆盖图像通过以前调用[cimagelist:: Setoverlayimage](../mfc/reference/cimagelist-class.md#setoverlayimage)函数。 此函数指定要添加; 的图像的基于 1 的索引这是使用与 INDEXTOOVERLAYMASK 宏保持一致的索引。 一个树控件最多可拥有四个覆盖图像。

若要设置项的状态图像*nStateMask*必须包括`TVIS_STATEIMAGEMASK`值，和*nState*必须包含一个基于移动的状态图像左索引 12 位使用[INDEXTOSTATEIMAGEMASK](/windows/desktop/api/commctrl/nf-commctrl-indextostateimagemask)宏。 索引可以为 0 以表示没有状态图像。 有关覆盖区上并状态映像的详细信息，请参阅[树控件图像列表](../mfc/tree-control-image-lists.md)。

## <a name="see-also"></a>请参阅

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控件](../mfc/controls-mfc.md)

