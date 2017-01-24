---
title: "树控件项状态概述 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTreeCtrl 类, 项状态"
  - "states, CTreeCtrl 项"
  - "树控件, 项状态概述"
ms.assetid: 2db11ae0-0d87-499d-8c1f-5e0dbe9e94c8
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 树控件项状态概述
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在树控件 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) 中的每个项都具有一个当前状态。  例如，项可以选择禁用，展开等等。  在很大程度上，树控件自动设置项的状态以反映用户操作，例如项的选择。  但是，可以使用 [GetItemState](../Topic/CTreeCtrl::GetItemState.md) 成员函数，还可以通过使用 [SetItemState](../Topic/CTreeCtrl::SetItemState.md) 成员函数设置项的状态和检索项的当前状态。  有关状态项的完整列表，请参阅[!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [树视图控件常数](http://msdn.microsoft.com/library/windows/desktop/bb759985)。  
  
 项的当前状态由 `nState` 参数指定。  树控件可能更改项的状态以反映用户操作，例如选择项或将焦点设置到该项。  此外，应用程序可能更改项的状态，隐藏或禁用项，或指定是否覆盖图像或状态图像。  
  
 在指定或更改项的状态时，`nStateMask` 参数指定要设置的状态位和 `nState` 参数包含这些位的新值。  例如，下面的示例将父项的当前状态 \(由`hParentItem`指定\) 在一个 `CTreeCtrl` 对象 \(`m_treeCtrl`）的 **TVIS\_EXPANDPARTIAL**:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#71](../mfc/codesnippet/CPP/tree-control-item-states-overview_1.cpp)]  
  
 更改状态的另一个示例是设置项的覆盖图像。  为此，`nStateMask` 必须包括 `TVIS_OVERLAYMASK`值，`nState`必须包括基于的覆盖图像的索引左移八位，使用 [INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408) 宏。  索引可以为0，这表示无法覆盖图像。  覆盖图像被添加到覆盖图像的树控件列表中，供 [CImageList::SetOverlayImage](../Topic/CImageList::SetOverlayImage.md) 函数调用。  函数指定添加以1开始的图像索引；这是**INDEXTOOVERLAYMASK** 宏使用的索引。  树控件具有四个可覆盖图像。  
  
 若要设置项的状态图像，则 `nStateMask` 必须包括 `TVIS_STATEIMAGEMASK`，`nState` 必须包含值，并且状态图像的基于1的索引左移 12 位，使用 [INDEXTOSTATEIMAGEMASK](http://msdn.microsoft.com/library/windows/desktop/bb775597) 宏。  索引可以为0，这表示无状态图像。  有关状态和覆盖图像的更多信息，请参见 [树控件图像的列表](../mfc/tree-control-image-lists.md)。  
  
## 请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)