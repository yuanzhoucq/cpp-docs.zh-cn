---
title: "树控件项信息 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], item information
- CTreeCtrl class [MFC], item information
ms.assetid: 8dcab855-27de-49e9-95d8-f78ba963ea71
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 16e4a707c4bc1f0fde76ab3a146424d2d34d5ec8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tree-control-item-information"></a>树控件项信息
树控件 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 具有大量检索有关控件中项的信息的成员函数。 [GetItem](../mfc/reference/ctreectrl-class.md#getitem)成员函数将检索的部分或全部与项关联的数据。 此数据可以包括项目的文本、状态、图像、子项目计数和应用程序定义的 32 位数据值。 此外，还有[SetItem](../mfc/reference/ctreectrl-class.md#setitem)可以设置某些或所有与项关联的数据的函数。  
  
 [GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate)， [GetItemText](../mfc/reference/ctreectrl-class.md#getitemtext)， [GetItemData](../mfc/reference/ctreectrl-class.md#getitemdata)，和[GetItemImage](../mfc/reference/ctreectrl-class.md#getitemimage)成员函数检索的独立特性项。 其中每个函数都有一个对应的为项目设置特性的 Set 函数。  
  
 [GetNextItem](../mfc/reference/ctreectrl-class.md#getnextitem)成员函数将检索具有与当前项目的指定的关系的树控件项目。 此函数可检索项目的父级、下一或上一可见项目、第一个子项目等等。 还有成员函数遍历树： [GetRootItem](../mfc/reference/ctreectrl-class.md#getrootitem)， [GetFirstVisibleItem](../mfc/reference/ctreectrl-class.md#getfirstvisibleitem)， [GetNextVisibleItem](../mfc/reference/ctreectrl-class.md#getnextvisibleitem)， [GetPrevVisibleItem](../mfc/reference/ctreectrl-class.md#getprevvisibleitem)， [GetChildItem](../mfc/reference/ctreectrl-class.md#getchilditem)， [GetNextSiblingItem](../mfc/reference/ctreectrl-class.md#getnextsiblingitem)， [GetPrevSiblingItem](../mfc/reference/ctreectrl-class.md#getprevsiblingitem)， [GetParentItem](../mfc/reference/ctreectrl-class.md#getparentitem)， [GetSelectedItem](../mfc/reference/ctreectrl-class.md#getselecteditem)，和[GetDropHilightItem](../mfc/reference/ctreectrl-class.md#getdrophilightitem)。  
  
 [GetItemRect](../mfc/reference/ctreectrl-class.md#getitemrect)成员函数将检索树控件项的边框。 [GetCount](../mfc/reference/ctreectrl-class.md#getcount)和[GetVisibleCount](../mfc/reference/ctreectrl-class.md#getvisiblecount)成员函数将检索树控件中的项的计数和当前可见在树控件的窗口中，分别是项的计数。 你可确保特定项通过调用中的可见[EnsureVisible](../mfc/reference/ctreectrl-class.md#ensurevisible)成员函数。  
  
## <a name="see-also"></a>请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)

