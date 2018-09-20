---
title: 与树控件通信 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 78bb6a6d6421a5336f8efbffc7d24a6121e208e6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432147"
---
# <a name="communicating-with-a-tree-control"></a>与树控件通信

用于调用成员函数使用不同的方法[CTreeCtrl](../mfc/reference/ctreectrl-class.md)具体取决于该对象的创建方式的对象：

- 如果树控件位于对话框中，请使用您在对话框类中创建的 `CTreeCtrl` 类型的成员变量。

- 如果树控件是子窗口，请使用用于构造对象的 `CTreeCtrl` 对象（或指针）。

- 如果您使用的`CTreeView`对象，请使用函数[ctreeview:: Gettreectrl](../mfc/reference/ctreeview-class.md#gettreectrl)若要获取对树控件的引用。 您可以使用此值初始化其他引用或将引用的地址分配给 `CTreeCtrl` 指针。

## <a name="see-also"></a>请参阅

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控件](../mfc/controls-mfc.md)

