---
title: 创建工具提示的方法
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], creating tool tips
- tool tips [MFC], tool tip controls
- tool tips [MFC], creating
ms.assetid: b015e9f4-ddfb-49a4-a5a6-fa2d45e4d328
ms.openlocfilehash: 26f31705068df009e906d50451efa9ea6572d7e6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625460"
---
# <a name="methods-of-creating-tool-tips"></a>创建工具提示的方法

MFC 提供了三个类来创建和管理工具提示控件： [CWnd](reference/cwnd-class.md)、 [CToolBarCtrl](reference/ctoolbarctrl-class.md)、 [CToolTipCtrl](reference/ctooltipctrl-class.md)和[CMFCToolTipCtrl](reference/cmfctooltipctrl-class.md)。 这些类中的工具提示成员函数包装 Windows 公共控件 API。 类 `CToolBarCtrl` 和类 `CToolTipCtrl` 类派生自类 `CWnd`。

`CWnd`提供四个成员函数来创建和管理工具提示： [EnableToolTips](reference/cwnd-class.md#enabletooltips)、 [CancelToolTips](reference/cwnd-class.md#canceltooltips)、 [FilterToolTipMessage](reference/cwnd-class.md#filtertooltipmessage)和[OnToolHitTest](reference/cwnd-class.md#ontoolhittest)。 有关它们如何实现工具提示的详细信息，请参阅这些单独的成员函数。

如果使用创建工具栏 `CToolBarCtrl` ，则可以使用以下成员函数直接为该工具栏实现工具提示： [GetToolTips](reference/ctoolbarctrl-class.md#gettooltips)和[SetToolTips](reference/ctoolbarctrl-class.md#settooltips)。 有关如何实现工具提示的详细信息，请参阅这些单独的成员函数和[处理工具提示通知](handling-tool-tip-notifications.md)。

`CToolTipCtrl` 类提供了 Windows 公共工具提示控件的功能。 一个工具提示控件可以提供多个工具的信息。 工具是一个窗口（如子窗口或控件）或窗口工作区中应用程序定义的矩形区域。 [CMFCToolTipCtrl](reference/cmfctooltipctrl-class.md)类派生自 `CToolTipCtrl` ，并提供其他视觉样式和功能。

## <a name="see-also"></a>另请参阅

[使用 CToolTipCtrl](using-ctooltipctrl.md)<br/>
[控件](controls-mfc.md)
