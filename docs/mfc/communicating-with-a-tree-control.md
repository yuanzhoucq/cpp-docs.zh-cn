---
title: 与树控件通信
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
ms.openlocfilehash: 920608724ebb362b91efdcb3eab50b80acd20474
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151249"
---
# <a name="communicating-with-a-tree-control"></a>与树控件通信

用于调用成员函数使用不同的方法[CTreeCtrl](../mfc/reference/ctreectrl-class.md)具体取决于该对象的创建方式的对象：

- 如果树控件位于对话框中，请使用你在对话框类中创建的 `CTreeCtrl` 类型的成员变量。

- 如果树控件是子窗口，请使用用于构造对象的 `CTreeCtrl` 对象（或指针）。

- 如果您使用的`CTreeView`对象，请使用函数[ctreeview:: Gettreectrl](../mfc/reference/ctreeview-class.md#gettreectrl)若要获取对树控件的引用。 您可以使用此值初始化其他引用或将引用的地址分配给 `CTreeCtrl` 指针。

## <a name="see-also"></a>请参阅

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控件](../mfc/controls-mfc.md)
