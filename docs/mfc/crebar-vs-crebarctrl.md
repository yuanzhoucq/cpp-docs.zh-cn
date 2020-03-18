---
title: CReBar 与 CReBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
ms.openlocfilehash: 94f889be453a17a55357a260bd2a0c07037f6ded
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445284"
---
# <a name="crebar-vs-crebarctrl"></a>CReBar 与 CReBarCtrl

MFC 提供了两个类来创建 rebar： [CReBar](../mfc/reference/crebar-class.md)和[CReBarCtrl](../mfc/reference/crebarctrl-class.md) （可包装 Windows 公共控件 API）。 `CReBar` 提供了 rebar 公共控件的所有功能，并且它会为你处理许多必需的公共控件设置和结构。

`CReBarCtrl` 是 Win32 rebar 控制的包装器类，因此如果您不打算将 rebar 集成到 MFC 体系结构中，则这可能更易于实现。 如果您计划使用 `CReBarCtrl` 并计划将 rebar 集成到 MFC 体系结构中，则必须额外注意将 rebar 控制操作传送到 MFC。 这种通信并不难;但是，当你使用 `CReBar`时，不需要执行其他操作。

Visual C++ 提供了两种利用 rebar 常用控制的方式。

- 使用 `CReBar`创建 rebar，然后调用[CReBar：： GetReBarCtrl](../mfc/reference/crebar-class.md#getrebarctrl)以获取对 `CReBarCtrl` 成员函数的访问权限。

    > [!NOTE]
    >  `CReBar::GetReBarCtrl` 是强制转换 rebar 对象的**this**指针的内联成员函数。 这意味着，函数调用在运行时没有开销。

- 使用[CReBarCtrl](../mfc/reference/crebarctrl-class.md)的构造函数创建 rebar。

任一方法都将为您提供对 rebar 控制的成员函数的访问权限。 当您调用 `CReBar::GetReBarCtrl` 时，它将返回对 `CReBarCtrl` 对象的引用，以便您可以使用成员函数集。 请参阅[CReBar](../mfc/reference/crebar-class.md) ，了解如何使用 `CReBar`构造和创建 rebar。

## <a name="see-also"></a>另请参阅

[使用 CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
