---
title: 创建列表控件
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating control
- list controls [MFC]
ms.assetid: a4cb1729-31b6-4d2b-a44b-367474848a39
ms.openlocfilehash: c9ba379611c44b5eae8d02b908ba71e3dbd66481
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617100"
---
# <a name="creating-the-list-control"></a>创建列表控件

如何创建列表控件（[CListCtrl](reference/clistctrl-class.md)）取决于是直接使用控件还是使用类[CListView](reference/clistview-class.md) 。 如果使用 `CListView` ，则框架会将视图构造为其文档/视图创建序列的一部分。 创建列表视图也会创建列表控件（这两者都是相同的）。 在视图的[OnCreate](reference/cwnd-class.md#oncreate)处理程序函数中创建控件。 在这种情况下，控件可通过调用[GetListCtrl](reference/clistview-class.md#getlistctrl)来添加项。

### <a name="to-use-clistctrl-directly-in-a-dialog-box"></a>直接在对话框中使用 CListCtrl

1. 在对话框编辑器中，将列表控件添加到对话框模板资源。 指定其控件 ID。

1. 使用 "[添加成员变量向导](../ide/adding-a-member-variable-visual-cpp.md)" 可以添加具有控件属性的类型的成员变量 `CListCtrl` 。 您可以使用此成员调用 `CListCtrl` 成员函数。

1. 使用[类向导](reference/mfc-class-wizard.md)可以在对话框类中映射您需要处理的任何列表控件通知消息（请参阅将[消息映射到函数](reference/mapping-messages-to-functions.md)）。

1. 在[OnInitDialog](reference/cdialog-class.md#oninitdialog)中，设置的样式 `CListCtrl` 。 请参阅[更改列表控件样式](changing-list-control-styles.md)。 这会确定在控件中获得的 "视图" 类型，不过以后可以更改视图。

### <a name="to-use-clistctrl-in-a-nondialog-window"></a>在非对话框窗口中使用 CListCtrl

1. 在视图或窗口类中定义控件。

1. 调用控件的[Create](reference/clistctrl-class.md#create)成员函数，该函数可能在[OnInitialUpdate](reference/cview-class.md#oninitialupdate)中，可能早于父窗口的[OnCreate](reference/cwnd-class.md#oncreate)处理程序函数（如果是控件的子类）。 设置控件的样式。

## <a name="see-also"></a>另请参阅

[使用 CListCtrl](using-clistctrl.md)<br/>
[控件](controls-mfc.md)
