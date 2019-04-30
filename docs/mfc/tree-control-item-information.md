---
title: 树控件项信息
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item information
- CTreeCtrl class [MFC], item information
ms.assetid: 8dcab855-27de-49e9-95d8-f78ba963ea71
ms.openlocfilehash: e0eb8af4fbbb6f59c0dda75ec3705183ce916350
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407856"
---
# <a name="tree-control-item-information"></a>树控件项信息

树控件 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 具有一些成员函数，用于检索有关控件中的项的信息。 [GetItem](../mfc/reference/ctreectrl-class.md#getitem)成员函数将检索部分或全部与项关联的数据。 此数据可以包括项目的文本、状态、图像、子项目计数和应用程序定义的 32 位数据值。 此外，还有[SetItem](../mfc/reference/ctreectrl-class.md#setitem)可以设置某些或全部与项关联的数据的函数。

[GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate)， [GetItemText](../mfc/reference/ctreectrl-class.md#getitemtext)， [GetItemData](../mfc/reference/ctreectrl-class.md#getitemdata)，以及[GetItemImage](../mfc/reference/ctreectrl-class.md#getitemimage)成员函数将检索的独立特性项。 其中每个函数都有一个对应的为项目设置特性的 Set 函数。

[GetNextItem](../mfc/reference/ctreectrl-class.md#getnextitem)成员函数将检索具有与当前项的指定的关系的树控件项。 此函数可检索项目的父级、下一或上一可见项目、第一个子项目等等。 还有成员函数来遍历树：[GetRootItem](../mfc/reference/ctreectrl-class.md#getrootitem)， [GetFirstVisibleItem](../mfc/reference/ctreectrl-class.md#getfirstvisibleitem)， [GetNextVisibleItem](../mfc/reference/ctreectrl-class.md#getnextvisibleitem)， [GetPrevVisibleItem](../mfc/reference/ctreectrl-class.md#getprevvisibleitem)， [GetChildItem](../mfc/reference/ctreectrl-class.md#getchilditem)，[GetNextSiblingItem](../mfc/reference/ctreectrl-class.md#getnextsiblingitem)， [GetPrevSiblingItem](../mfc/reference/ctreectrl-class.md#getprevsiblingitem)， [GetParentItem](../mfc/reference/ctreectrl-class.md#getparentitem)， [GetSelectedItem](../mfc/reference/ctreectrl-class.md#getselecteditem)，和[GetDropHilightItem](../mfc/reference/ctreectrl-class.md#getdrophilightitem)。

[GetItemRect](../mfc/reference/ctreectrl-class.md#getitemrect)成员函数将检索树控件项的边框。 [GetCount](../mfc/reference/ctreectrl-class.md#getcount)并[GetVisibleCount](../mfc/reference/ctreectrl-class.md#getvisiblecount)成员函数将检索树控件中项的计数和当前可见在树控件的窗口中，分别是项的计数。 你可以确保特定的项是通过调用可见[EnsureVisible](../mfc/reference/ctreectrl-class.md#ensurevisible)成员函数。

## <a name="see-also"></a>请参阅

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控件](../mfc/controls-mfc.md)
