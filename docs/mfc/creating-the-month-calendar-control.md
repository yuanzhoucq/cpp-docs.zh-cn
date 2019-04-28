---
title: 创建月历控件
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], creating
- month calendar controls [MFC], creating
- month calendar controls [MFC]
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
ms.openlocfilehash: 809bc9fdf6b4477363d0a43d007a2884bb43a049
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242180"
---
# <a name="creating-the-month-calendar-control"></a>创建月历控件

月历控件的创建方式取决于您将在对话框中使用此控件还是将在非对话框窗口中创建此控件。

### <a name="to-use-cmonthcalctrl-directly-in-a-dialog-box"></a>在对话框中直接使用 CMonthCalCtrl

1. 在对话框编辑器中，将月历控件添加到对话框模板资源。 指定其控件 ID。

1. 使用月历控件的“属性”对话框指定任何所需样式。

1. 使用[添加成员变量向导](../ide/adding-a-member-variable-visual-cpp.md)若要添加的成员变量的类型[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)与控件属性。 您可以使用此成员调用 `CMonthCalCtrl` 成员函数。

1. 使用属性窗口对于任何月历控件通知消息您映射对话框类中的处理程序函数需要处理 (请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md))。

1. 在中[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)，设置为任何其他样式`CMonthCalCtrl`对象。

### <a name="to-use-cmonthcalctrl-in-a-nondialog-window"></a>在非对话框窗口中使用 CMonthCalCtrl

1. 在视图或窗口类中定义控件。

1. 调用控件的[创建](../mfc/reference/cmonthcalctrl-class.md#create)成员函数，这有可能在[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)，作为父窗口可能早[OnCreate](../mfc/reference/cwnd-class.md#oncreate)处理程序函数 （如果已连接将控件子类化）。 设置控件的样式。

## <a name="see-also"></a>请参阅

[使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
