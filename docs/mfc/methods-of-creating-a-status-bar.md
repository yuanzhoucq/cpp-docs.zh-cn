---
title: 创建状态栏的方法
ms.date: 11/04/2016
helpviewer_keywords:
- CStatusBar class [MFC], vs. CStatusBarCtrl
- methods [MFC], creating status bars
- CStatusBarCtrl class [MFC], vs. CStatusBar
- CStatusBarCtrl class [MFC], creating
- methods [MFC]
- status bars [MFC], creating
ms.assetid: 9aeaf290-7099-4762-a5ba-9c26705333c9
ms.openlocfilehash: a2301301d0012bd93ffedd0452dec140174402e0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276879"
---
# <a name="methods-of-creating-a-status-bar"></a>创建状态栏的方法

MFC 提供了两个类，创建状态条：[CStatusBar](../mfc/reference/cstatusbar-class.md)并[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) （其包装 Windows 公共控件 API）。 `CStatusBar` 提供的所有功能的公共控件状态栏，它会自动与交互菜单和工具栏，和它为你; 处理许多必需的常用控制设置和结构但是，生成可执行文件通常会比使用创建的大`CStatusBarCtrl`。

`CStatusBarCtrl` 通常会导致较小的可执行文件，以及你可能更愿意使用`CStatusBarCtrl`如果不想将状态栏集成到 MFC 体系结构。 如果你打算使用`CStatusBarCtrl`和将状态栏集成到 MFC 体系结构，必须采取额外注意将控制操作传送到 MFC 状态栏。 此通信并不困难;但是，它是在使用时是不需要的额外工作`CStatusBar`。

Visual c + + 提供了两种方式利用状态栏常见控件。

- 创建使用状态栏`CStatusBar`，然后调用[CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl)若要访问`CStatusBarCtrl`成员函数。

- 创建使用状态栏[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)的构造函数。

这两种方法将让你访问状态栏控件的成员函数。 当您调用 `CStatusBar::GetStatusBarCtrl` 时，它将返回对 `CStatusBarCtrl` 对象的引用，以便您可以使用成员函数集。 请参阅[CStatusBar](../mfc/reference/cstatusbar-class.md)信息构造和创建状态栏使用`CStatusBar`。

## <a name="see-also"></a>请参阅

[使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
