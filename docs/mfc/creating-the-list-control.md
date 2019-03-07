---
title: 创建列表控件
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating control
- list controls [MFC]
ms.assetid: a4cb1729-31b6-4d2b-a44b-367474848a39
ms.openlocfilehash: 7b2cb47699339dd413dc1bfae7623069da56e7a4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303640"
---
# <a name="creating-the-list-control"></a>创建列表控件

如何控制列表 ([CListCtrl](../mfc/reference/clistctrl-class.md)) 创建取决于是否要直接使用该控件或使用类[CListView](../mfc/reference/clistview-class.md)相反。 如果使用`CListView`，该框架构造视图作为其文档/视图创建序列的一部分。 创建列表视图中创建列表控件还 （两个是相同的操作）。 在视图中创建该控件[OnCreate](../mfc/reference/cwnd-class.md#oncreate)处理程序函数。 在这种情况下，该控件已准备就绪，若要添加项，通过调用[GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl)。

### <a name="to-use-clistctrl-directly-in-a-dialog-box"></a>若要在对话框中直接使用 CListCtrl

1. 在对话框编辑器中，将添加到对话框模板资源的列表控件。 指定其控件 ID。

1. 使用[添加成员变量向导](../ide/adding-a-member-variable-visual-cpp.md)若要添加的成员变量的类型`CListCtrl`与控件属性。 您可以使用此成员调用 `CListCtrl` 成员函数。

1. 使用属性窗口的任何列表控件通知消息映射对话框类中的处理程序函数需要处理 (请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md))。

1. 在中[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)，为设置样式`CListCtrl`。 请参阅[更改列表控件样式](../mfc/changing-list-control-styles.md)。 这可确定类型的"视图"，获取在控件中，尽管您可以更改视图更高版本。

### <a name="to-use-clistctrl-in-a-nondialog-window"></a>若要在非对话框窗口中使用 CListCtrl

1. 在视图或窗口类中定义控件。

1. 调用控件的[创建](../mfc/reference/clistctrl-class.md#create)成员函数，这有可能在[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)，作为父窗口可能早[OnCreate](../mfc/reference/cwnd-class.md#oncreate)处理程序函数 （如果已连接将控件子类化）。 设置控件的样式。

## <a name="see-also"></a>请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
