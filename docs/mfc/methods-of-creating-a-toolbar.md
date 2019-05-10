---
title: 创建工具栏的方法
ms.date: 11/04/2016
helpviewer_keywords:
- CToolBarCtrl class [MFC], and CToolBar class [MFC]
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- toolbar controls [MFC]
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: f19d8d65-d49f-445c-abe8-d47d3e4101c8
ms.openlocfilehash: f269ad990042f51554ec598b0bddbe5a6d7776b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383901"
---
# <a name="methods-of-creating-a-toolbar"></a>创建工具栏的方法

MFC 提供了两个类来创建工具栏：[CToolBar](../mfc/reference/ctoolbar-class.md)并[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) （其包装 Windows 公共控件 API）。 `CToolBar` 提供了所有工具栏公共控件的功能，还可以处理许多必需的常用控制设置和结构为您;但是，生成可执行文件通常会比使用创建的大`CToolBarCtrl`。

`CToolBarCtrl` 通常会导致较小的可执行文件，以及你可能更愿意使用`CToolBarCtrl`如果你不想要将工具栏集成到 MFC 体系结构。 如果你打算使用`CToolBarCtrl`和将工具栏集成到 MFC 体系结构，必须采取额外注意将工具栏控制操作传送到 MFC。 此通信并不困难;但是，它是在使用时是不需要的额外工作`CToolBar`。

VisualC++提供两种方法，以利用工具栏公共控件。

- 创建工具栏使用`CToolBar`，然后调用[CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl)若要访问`CToolBarCtrl`成员函数。

- 创建工具栏使用[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)的构造函数。

这两种方法将让你访问工具栏控件的成员函数。 当您调用 `CToolBar::GetToolBarCtrl` 时，它将返回对 `CToolBarCtrl` 对象的引用，以便您可以使用成员函数集。 请参阅[CToolBar](../mfc/reference/ctoolbar-class.md)信息构造和创建工具栏使用`CToolBar`。

## <a name="see-also"></a>请参阅

[使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
