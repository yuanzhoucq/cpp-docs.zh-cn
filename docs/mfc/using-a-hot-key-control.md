---
title: 使用热键控件
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: cdd6524b-cc43-447f-b151-164273559685
ms.openlocfilehash: 335489011076b1e30a9c36720a3bf2e94c7918b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542189"
---
# <a name="using-a-hot-key-control"></a>使用热键控件

热键控件的典型用法遵循以下模式：

- 创建滑块控件。 如果滑块控件是在对话框模板中指定的，则在创建对话框时自动进行创建。 (您应该[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)对应于热键控件在对话框类中的成员。)或者，可以使用[创建](../mfc/reference/chotkeyctrl-class.md#create)成员函数来创建控件用作子窗口的任何窗口。

- 如果你想要设置控件的默认值，调用[SetHotKey](../mfc/reference/chotkeyctrl-class.md#sethotkey)成员函数。 如果你想要禁止某些移位状态，调用[设置规则](../mfc/reference/chotkeyctrl-class.md#setrules)。 对于控件在对话框中，执行此操作的好时机是在对话框中[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)函数。

- 用户通过按热键组合热键控件具有焦点时与控件交互。 用户然后以某种方式表明此任务已完成，也许是通过单击对话框中的按钮。

- 当您的程序通知用户所选热键时，应使用此成员函数[GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey)从热键控件中检索虚拟键和 shift 状态值。

- 一旦您知道哪个键选定的用户，就可以设置热键使用中所述的方法之一[设置热键](../mfc/setting-a-hot-key.md)。

- 热键控件是在对话框中，如果它和`CHotKeyCtrl`对象将自动被销毁。 否则，您需要确保正确地销毁控件和 `CHotKeyCtrl` 对象。

## <a name="see-also"></a>请参阅

[使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

