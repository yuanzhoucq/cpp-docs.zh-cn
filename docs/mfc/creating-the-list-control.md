---
title: 创建列表控件
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating control
- list controls [MFC]
ms.assetid: a4cb1729-31b6-4d2b-a44b-367474848a39
ms.openlocfilehash: f1c5d8db93421e1d3ae0e39aec82bdf0f5529f1f
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907929"
---
# <a name="creating-the-list-control"></a>创建列表控件

如何创建列表控件（[CListCtrl](../mfc/reference/clistctrl-class.md)）取决于是直接使用控件还是使用类[CListView](../mfc/reference/clistview-class.md) 。 如果使用`CListView`，则框架会将视图构造为其文档/视图创建序列的一部分。 创建列表视图也会创建列表控件（这两者都是相同的）。 在视图的[OnCreate](../mfc/reference/cwnd-class.md#oncreate)处理程序函数中创建控件。 在这种情况下，控件可通过调用[GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl)来添加项。

### <a name="to-use-clistctrl-directly-in-a-dialog-box"></a>直接在对话框中使用 CListCtrl

1. 在对话框编辑器中，将列表控件添加到对话框模板资源。 指定其控件 ID。

1. 使用 "[添加成员变量向导](../ide/adding-a-member-variable-visual-cpp.md)" 可以添加具有控件属性的`CListCtrl`类型的成员变量。 您可以使用此成员调用 `CListCtrl` 成员函数。

1. 使用[类向导](reference/mfc-class-wizard.md)可以在对话框类中映射您需要处理的任何列表控件通知消息（请参阅将[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)）。

1. 在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)中，设置的`CListCtrl`样式。 请参阅[更改列表控件样式](../mfc/changing-list-control-styles.md)。 这会确定在控件中获得的 "视图" 类型，不过以后可以更改视图。

### <a name="to-use-clistctrl-in-a-nondialog-window"></a>在非对话框窗口中使用 CListCtrl

1. 在视图或窗口类中定义控件。

1. 调用控件的[Create](../mfc/reference/clistctrl-class.md#create)成员函数，该函数可能在[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)中，可能早于父窗口的[OnCreate](../mfc/reference/cwnd-class.md#oncreate)处理程序函数（如果是控件的子类）。 设置控件的样式。

## <a name="see-also"></a>请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
