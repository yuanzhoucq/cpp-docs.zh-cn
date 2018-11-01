---
title: 使用 CHotKeyCtrl
ms.date: 11/04/2016
f1_keywords:
- CHotKeyCtrl
helpviewer_keywords:
- keys, hot and CHotKeyCtrl
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: 9b207117-d848-4224-8888-c3d197bb0c95
ms.openlocfilehash: bf6ad9c8ea1b1a66f5a8abbf61f78c942ffda2fa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483767"
---
# <a name="using-chotkeyctrl"></a>使用 CHotKeyCtrl

热键控件，由类[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)，是一个窗口，显示的文本表示形式在用户键入到其中，例如 CTRL + SHIFT + Q 键组合。 它还保留以虚拟键代码的形式呈现的此键的内部表示形式和一组表示切换状态的标志。 热键控件实际上并不设置热键 - 是否执行此操作取决于您的程序。 （有关标准虚拟键代码的列表，请参见 Winuser.h。）

使用热键控件获取用户对要与窗口或线程关联的热键的输入。 热键控件通常用于对话框中，例如，您可能显示何时要求用户分配热键。 您的程序负责从热键控件中检索描述热键的值并调用适当的函数以将热键与窗口或线程相关联。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [使用热键控件](../mfc/using-a-hot-key-control.md)

- [设置热键](../mfc/setting-a-hot-key.md)

- [全局热键](../mfc/global-hot-keys.md)

- [线程特定的热键](../mfc/thread-specific-hot-keys.md)

## <a name="see-also"></a>请参阅

[控件](../mfc/controls-mfc.md)

