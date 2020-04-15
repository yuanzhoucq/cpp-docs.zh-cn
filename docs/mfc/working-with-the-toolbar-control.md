---
title: 使用工具栏控件
ms.date: 11/04/2016
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
ms.openlocfilehash: 371f1944fae655556bbc9f89d7ffcce7cc326e5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365251"
---
# <a name="working-with-the-toolbar-control"></a>使用工具栏控件

本文介绍如何访问[CToolBar](../mfc/reference/ctoolbar-class.md)基础的[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)对象，以便更好地控制工具栏。 这是一个高级主题。

## <a name="procedures"></a>过程

#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>访问 CToolBar 对象基础的工具栏公共控件

1. 调用[CToolBar：获取工具栏](../mfc/reference/ctoolbar-class.md#gettoolbarctrl)。

`GetToolBarCtrl`返回对[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)对象的引用。 可以使用引用调用工具栏控件类的成员函数。

> [!CAUTION]
> 虽然调用`CToolBarCtrl` **Get**函数是安全的，但如果您调用**Set**函数，请谨慎。 这是一个高级主题。 通常，您不需要访问基础工具栏控件。

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [控件（Windows 常见控件）](../mfc/controls-mfc.md)

- [工具栏基础知识](../mfc/toolbar-fundamentals.md)

- [停靠和浮动工具栏](../mfc/docking-and-floating-toolbars.md)

- [动态调整工具栏大小](../mfc/docking-and-floating-toolbars.md)

- [工具栏工具提示](../mfc/toolbar-tool-tips.md)

- [飞天状态栏更新](../mfc/toolbar-tool-tips.md)

- [处理工具提示通知](../mfc/handling-tool-tip-notifications.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)类

- [处理自定义通知](../mfc/handling-customization-notifications.md)

- [多个工具栏](../mfc/toolbar-fundamentals.md)

- [使用旧工具栏](../mfc/using-your-old-toolbars.md)

- [控制条](../mfc/control-bars.md)

有关使用 Windows 常见控件的一般信息，请参阅[常见控件](/windows/win32/Controls/common-controls-intro)。

## <a name="see-also"></a>另请参阅

[MFC 工具栏实现](../mfc/mfc-toolbar-implementation.md)
