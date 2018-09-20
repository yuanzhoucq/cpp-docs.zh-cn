---
title: 创建日期和时间选取器控件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DateTimePicker control [MFC], creating
- CDateTimeCtrl class [MFC], creating
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 864d6cfef599da61238baa92f7ab01a8ad82229d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393290"
---
# <a name="creating-the-date-and-time-picker-control"></a>创建日期和时间选择器控件

日期和时间选取器控件的创建方式取决于您是在对话框中使用控件还是在非对话框窗口中创建它。

### <a name="to-use-cdatetimectrl-directly-in-a-dialog-box"></a>若要在对话框中直接使用 CDateTimeCtrl

1. 在对话框编辑器中，将添加到对话框模板资源的日期和时间选取器控件。 指定其控件 ID。

1. 指定任何所需，使用属性对话框中的日期和时间选取器控件的样式。

1. 使用[添加成员变量向导](../ide/adding-a-member-variable-visual-cpp.md)若要添加的成员变量的类型[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)与控件属性。 您可以使用此成员调用 `CDateTimeCtrl` 成员函数。

1. 使用属性窗口将映射任何日期时间选取器控件的对话框类中的处理程序函数[通知](../mfc/processing-notification-messages-in-date-and-time-picker-controls.md)需要处理的消息 (请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md))。

1. 在中[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)，设置为任何其他样式`CDateTimeCtrl`对象。

### <a name="to-use-cdatetimectrl-in-a-nondialog-window"></a>若要在非对话框窗口中使用 CDateTimeCtrl

1. 声明中的视图或窗口类的控件。

1. 调用控件的[创建](../mfc/reference/ctabctrl-class.md#create)成员函数，这有可能在[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)，作为父窗口可能早[OnCreate](../mfc/reference/cwnd-class.md#oncreate)处理程序函数 （如果已连接将控件子类化）。 设置控件的样式。

## <a name="see-also"></a>请参阅

[使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[控件](../mfc/controls-mfc.md)

