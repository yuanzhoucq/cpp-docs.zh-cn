---
title: 创建月历控件
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], creating
- month calendar controls [MFC], creating
- month calendar controls [MFC]
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
ms.openlocfilehash: 9e430a86c2ac08bde0f031a4c91b9ae5c6f570f3
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907495"
---
# <a name="creating-the-month-calendar-control"></a>创建月历控件

月历控件的创建方式取决于您将在对话框中使用此控件还是将在非对话框窗口中创建此控件。

### <a name="to-use-cmonthcalctrl-directly-in-a-dialog-box"></a>在对话框中直接使用 CMonthCalCtrl

1. 在对话框编辑器中，将月历控件添加到对话框模板资源。 指定其控件 ID。

1. 使用月历控件的“属性”对话框指定任何所需样式。

1. 使用 "[添加成员变量向导](../ide/adding-a-member-variable-visual-cpp.md)" 可使用 Control 属性添加类型为[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)的成员变量。 您可以使用此成员调用 `CMonthCalCtrl` 成员函数。

1. 使用[类向导](reference/mfc-class-wizard.md)可以在对话框类中映射您需要处理的任何月份日历控件通知消息（请参阅[将消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)）。

1. 在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)中，为`CMonthCalCtrl`对象设置任何其他样式。

### <a name="to-use-cmonthcalctrl-in-a-nondialog-window"></a>在非对话框窗口中使用 CMonthCalCtrl

1. 在视图或窗口类中定义控件。

1. 调用控件的[Create](../mfc/reference/cmonthcalctrl-class.md#create)成员函数，该函数可能在[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)中，可能早于父窗口的[OnCreate](../mfc/reference/cwnd-class.md#oncreate)处理程序函数（如果是控件的子类）。 设置控件的样式。

## <a name="see-also"></a>请参阅

[使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
