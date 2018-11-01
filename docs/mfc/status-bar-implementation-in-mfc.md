---
title: MFC 中的状态栏实现
ms.date: 11/04/2016
f1_keywords:
- COldStatusBar
helpviewer_keywords:
- status bars [MFC], implementing in MFC
- CStatusBarCtrl class [MFC], and MFC status bars
- CStatusBar class [MFC], and CStatusBarCtrl class [MFC]
- CStatusBarCtrl class [MFC], and CStatusBar class [MFC]
- status bars [MFC], backward compatibility
- status bars [MFC], old with COldStatusBar class [MFC]
- COldStatusBar class [MFC]
- status bars [MFC], and CStatusBarCtrl class
- CStatusBar class [MFC], and MFC status bars
- status indicators
- status bars [MFC], Windows 95 implementation
ms.assetid: be5cd876-38e3-4d5c-b8cb-16d57a16a142
ms.openlocfilehash: 25848e4467a0d767c40ffb00a1bd4d50a062d3a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496273"
---
# <a name="status-bar-implementation-in-mfc"></a>MFC 中的状态栏实现

一个[CStatusBar](../mfc/reference/cstatusbar-class.md)对象是具有一行文本输出窗格的控件条。 输出窗格通常用作消息行和状态指示器。 示例包括简要介绍所选的菜单命令的菜单帮助消息行和指示器显示 SCROLL LOCK、 NUM LOCK 和其他键的状态。

从 MFC 4.0 版，开始状态栏使用类实现[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)，它封装状态栏公共控件。 为了向后兼容，MFC 将保留在类中的较旧状态栏实现`COldStatusBar`。 早期版本的 MFC 的文档介绍`COldStatusBar`下`CStatusBar`。

[CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl)，成员函数新增到 MFC 4.0，让您充分利用状态栏自定义项和其他功能的 Windows 公共控件的支持。 `CStatusBar` 成员函数为您提供的大多数 Windows 公共控件; 功能但是，在调用`GetStatusBarCtrl`，您可以为您状态栏甚至多个状态栏的特征。 当您调用`GetStatusBarCtrl`，它将返回到引用`CStatusBarCtrl`对象。 该引用可用于操作状态栏控件。

下图显示了几个指示器的状态栏。

![状态栏](../mfc/media/vc37dy1.gif "vc37dy1")状态栏

工具栏上，如状态栏对象嵌入到其父框架窗口中，并构造框架窗口时，会自动构造。 状态栏等所有控件条，也被破坏自动与父框架时销毁。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [更新状态栏窗格的文本](../mfc/updating-the-text-of-a-status-bar-pane.md)

- MFC 类[CStatusBar](../mfc/reference/cstatusbar-class.md)和[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)

- [控件条](../mfc/control-bars.md)

- [对话栏](../mfc/dialog-bars.md)

- [工具栏 （MFC 工具栏实现）](../mfc/mfc-toolbar-implementation.md)

## <a name="see-also"></a>请参阅

[状态栏](../mfc/status-bars.md)

