---
title: CReBar 与CReBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
ms.openlocfilehash: d58efa3c0dfb888f0802a84b11ec597dd1267de6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228630"
---
# <a name="crebar-vs-crebarctrl"></a>CReBar 与CReBarCtrl

MFC 提供了两个类来创建 rebar： [CReBar](reference/crebar-class.md)和[CReBarCtrl](reference/crebarctrl-class.md) （可包装 Windows 公共控件 API）。 `CReBar`提供 rebar 公共控件的所有功能，并为你处理许多必需的公共控件设置和结构。

`CReBarCtrl` 是 Win32 rebar 控制的包装器类，因此如果您不打算将 rebar 集成到 MFC 体系结构中，则这可能更易于实现。 如果您计划使用 `CReBarCtrl` 并计划将 rebar 集成到 MFC 体系结构中，则必须额外注意将 rebar 控制操作传送到 MFC。 这种通信并不难;但是，当你使用时，它是不必要的其他工作 `CReBar` 。

Visual C++ 提供了两种利用 rebar 常用控制的方式。

- 使用创建 rebar `CReBar` ，然后调用[CReBar：： GetReBarCtrl](reference/crebar-class.md#getrebarctrl)以获取对成员函数的访问权限 `CReBarCtrl` 。

    > [!NOTE]
    >  `CReBar::GetReBarCtrl`是强制转换 **`this`** rebar 对象指针的内联成员函数。 这意味着，函数调用在运行时没有开销。

- 使用[CReBarCtrl](reference/crebarctrl-class.md)的构造函数创建 rebar。

任一方法都将为您提供对 rebar 控制的成员函数的访问权限。 当您调用 `CReBar::GetReBarCtrl` 时，它将返回对 `CReBarCtrl` 对象的引用，以便您可以使用成员函数集。 请参阅[CReBar](reference/crebar-class.md) ，了解如何使用构造和创建 rebar `CReBar` 。

## <a name="see-also"></a>另请参阅

[使用 CReBarCtrl](using-crebarctrl.md)<br/>
[控制](controls-mfc.md)
