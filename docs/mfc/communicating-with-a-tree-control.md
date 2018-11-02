---
title: 与树控件通信
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
ms.openlocfilehash: a5749b76468a7ba30cd48dc3a9b61f2de7ac67b9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654176"
---
# <a name="communicating-with-a-tree-control"></a>与树控件通信

用于调用成员函数使用不同的方法[CTreeCtrl](../mfc/reference/ctreectrl-class.md)具体取决于该对象的创建方式的对象：

- 如果树控件位于对话框中，请使用你在对话框类中创建的 `CTreeCtrl` 类型的成员变量。

- 如果树控件是子窗口，请使用用于构造对象的 `CTreeCtrl` 对象（或指针）。

- 如果您使用的`CTreeView`对象，请使用函数[ctreeview:: Gettreectrl](../mfc/reference/ctreeview-class.md#gettreectrl)若要获取对树控件的引用。 您可以使用此值初始化其他引用或将引用的地址分配给 `CTreeCtrl` 指针。

## <a name="see-also"></a>请参阅

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控件](../mfc/controls-mfc.md)

