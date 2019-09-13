---
title: 创建日期和时间选择器控件
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], creating
- CDateTimeCtrl class [MFC], creating
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
ms.openlocfilehash: de9baf63577d163b82da1c5977a6ccba6539c73a
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907593"
---
# <a name="creating-the-date-and-time-picker-control"></a>创建日期和时间选择器控件

创建日期和时间选取器控件的方式取决于您使用的是对话框中的控件，还是在非对话框窗口中创建控件。

### <a name="to-use-cdatetimectrl-directly-in-a-dialog-box"></a>直接在对话框中使用 CDateTimeCtrl

1. 在对话框编辑器中，将日期和时间选取器控件添加到对话框模板资源。 指定其控件 ID。

1. 使用 "日期和时间选择器" 控件的 "属性" 对话框指定所需的任何样式。

1. 使用 "[添加成员变量向导](../ide/adding-a-member-variable-visual-cpp.md)" 可使用 Control 属性添加类型为[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)的成员变量。 您可以使用此成员调用 `CDateTimeCtrl` 成员函数。

1. 使用[类向导](reference/mfc-class-wizard.md)可以在对话框类中映射处理程序函数，以获取需要处理的任何日期时间选取器控件[通知](../mfc/processing-notification-messages-in-date-and-time-picker-controls.md)消息（请参阅[将消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)）。

1. 在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)中，为`CDateTimeCtrl`对象设置任何其他样式。

### <a name="to-use-cdatetimectrl-in-a-nondialog-window"></a>在非对话框窗口中使用 CDateTimeCtrl

1. 在视图或窗口类中声明控件。

1. 调用控件的[Create](../mfc/reference/ctabctrl-class.md#create)成员函数，该函数可能在[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)中，可能早于父窗口的[OnCreate](../mfc/reference/cwnd-class.md#oncreate)处理程序函数（如果是控件的子类）。 设置控件的样式。

## <a name="see-also"></a>请参阅

[使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[控件](../mfc/controls-mfc.md)
