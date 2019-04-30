---
title: 使用工具栏控件
ms.date: 11/04/2016
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
ms.openlocfilehash: 88c00bf60f2ce1fccecd757d13b2f814e3a18be4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399494"
---
# <a name="working-with-the-toolbar-control"></a>使用工具栏控件

此文章介绍了如何访问[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)对象基础[CToolBar](../mfc/reference/ctoolbar-class.md)更好地控制您的工具栏。 这是一个高级的主题。

## <a name="procedures"></a>过程

#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>若要访问基础 CToolBar 对象工具栏公共控件

1. 调用[CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl)。

`GetToolBarCtrl` 返回的引用[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)对象。 可以使用引用来调用工具栏控件类的成员函数。

> [!CAUTION]
>  虽然通过调用`CToolBarCtrl`**获取**函数的安全，如果调用要格外小心**设置**函数。 这是一个高级的主题。 通常情况下不应需要访问基础工具栏控件。

### <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [控件 （Windows 公共控件）](../mfc/controls-mfc.md)

- [工具栏基础知识](../mfc/toolbar-fundamentals.md)

- [停靠和浮动工具栏](../mfc/docking-and-floating-toolbars.md)

- [动态调整大小的工具栏](../mfc/docking-and-floating-toolbars.md)

- [工具栏工具提示](../mfc/toolbar-tool-tips.md)

- [越过状态栏更新](../mfc/toolbar-tool-tips.md)

- [处理工具提示通知](../mfc/handling-tool-tip-notifications.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md)并[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)类

- [处理自定义通知](../mfc/handling-customization-notifications.md)

- [多个工具栏](../mfc/toolbar-fundamentals.md)

- [使用您的旧工具栏](../mfc/using-your-old-toolbars.md)

- [控件条](../mfc/control-bars.md)

有关使用 Windows 公共控件的常规信息，请参阅[公共控件](/windows/desktop/Controls/common-controls-intro)。

## <a name="see-also"></a>请参阅

[MFC 工具栏实现](../mfc/mfc-toolbar-implementation.md)
