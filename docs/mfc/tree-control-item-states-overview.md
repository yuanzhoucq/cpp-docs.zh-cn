---
title: 树控件项状态概述 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- states, CTreeCtrl items
- tree controls [MFC], item states overview
- CTreeCtrl class [MFC], item states
ms.assetid: 2db11ae0-0d87-499d-8c1f-5e0dbe9e94c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3bc62308642492aa00a139fb15cc9e6cdcfc3247
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="tree-control-item-states-overview"></a>树控件项状态概述
树控件中的每个项 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 具有一个当前状态。 例如，可以选择、禁用、展开项等等。 在大多数情况下，树控件将自动设置项的状态以反映用户操作，例如选择了某个项。 但是，你还可以通过使用设置项的状态[SetItemState](../mfc/reference/ctreectrl-class.md#setitemstate)成员函数，并检索项使用的当前状态[GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate)成员函数。 有关项状态的完整列表，请参阅[树视图控件常量](http://msdn.microsoft.com/library/windows/desktop/bb759985)Windows SDK 中。  
  
 项的当前状态由 `nState` 参数指定。 树控件可能更改项的状态以反映用户操作，例如选择该项或将焦点设置为该项。 此外，应用程序可能更改项的状态来禁用或隐藏项，或指定覆盖图像或状态图像。  
  
 在指定或更改项的状态时，`nStateMask` 参数指定要设置的状态位，而 `nState` 参数则包含这些位的新值。 例如，下面的示例更改父项的当前状态 (通过指定`hParentItem`) 中`CTreeCtrl`对象 (`m_treeCtrl`) 到**TVIS_EXPANDPARTIAL**:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#71](../mfc/codesnippet/cpp/tree-control-item-states-overview_1.cpp)]  
  
 更改状态的另一个示例是设置项的覆盖图像。 若要实现此目的，`nStateMask`必须包括`TVIS_OVERLAYMASK`值，和`nState`必须包括一个基于移动该覆盖图像左索引八位通过[INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408)宏。 索引可以为 0 以表示没有覆盖图像。 将覆盖图像必须具有已添加到树控件的覆盖图像列表的以前调用到[cimagelist:: Setoverlayimage](../mfc/reference/cimagelist-class.md#setoverlayimage)函数。 此函数指定要添加; 的图像的基于 1 的索引这是用于索引**INDEXTOOVERLAYMASK**宏。 一个树控件最多可拥有四个覆盖图像。  
  
 若要设置项的状态图像`nStateMask`必须包括`TVIS_STATEIMAGEMASK`值，和`nState`必须包括一个基于移动的状态图像左 12 位索引使用[INDEXTOSTATEIMAGEMASK](http://msdn.microsoft.com/library/windows/desktop/bb775597)宏。 索引可以为 0 以表示没有状态图像。 有关覆盖图像和状态图像的详细信息，请参阅[树控件图像列表](../mfc/tree-control-image-lists.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)

