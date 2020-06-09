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
ms.openlocfilehash: b70e6f4dc15023b878bb58d6b7d0739eeb173d53
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624255"
---
# <a name="methods-of-creating-a-toolbar"></a>创建工具栏的方法

MFC 提供了两个用于创建工具栏的类： [CToolBar](reference/ctoolbar-class.md)和[CToolBarCtrl](reference/ctoolbarctrl-class.md) （用于包装 Windows 公共控件 API）。 `CToolBar`提供 toolbar 公共控件的所有功能，并为您处理许多必需的公共控件设置和结构。但是，生成的可执行文件通常会大于使用创建的 `CToolBarCtrl` 。

`CToolBarCtrl`通常会产生较小的可执行文件， `CToolBarCtrl` 如果不打算将工具栏集成到 MFC 体系结构中，则可能更倾向于使用。 如果计划使用 `CToolBarCtrl` 工具栏并将其集成到 mfc 体系结构中，则必须特别注意将工具栏控件操作传达给 mfc。 这种通信并不难;但是，当你使用时，它是不必要的其他工作 `CToolBar` 。

Visual C++ 提供了两种方法来利用工具栏公共控件。

- 使用创建工具栏 `CToolBar` ，然后调用[CToolBar：： GetToolBarCtrl](reference/ctoolbar-class.md#gettoolbarctrl)以获取对成员函数的访问权限 `CToolBarCtrl` 。

- 使用[CToolBarCtrl](reference/ctoolbarctrl-class.md)的构造函数创建工具栏。

任一方法都可让你访问 toolbar 控件的成员函数。 当您调用 `CToolBar::GetToolBarCtrl` 时，它将返回对 `CToolBarCtrl` 对象的引用，以便您可以使用成员函数集。 有关使用构造和创建工具栏的信息，请参阅[CToolBar](reference/ctoolbar-class.md) `CToolBar` 。

## <a name="see-also"></a>另请参阅

[使用 CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[控件](controls-mfc.md)
