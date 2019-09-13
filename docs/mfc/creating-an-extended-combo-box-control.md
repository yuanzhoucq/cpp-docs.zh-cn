---
title: 创建扩展组合框控件
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
ms.openlocfilehash: 87e2e1cd3c29ba838a17c24ece4a89adda21db0c
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907727"
---
# <a name="creating-an-extended-combo-box-control"></a>创建扩展组合框控件

如何创建扩展组合框控件取决于您是在对话框中使用控件，还是在非对话框窗口中创建控件。

### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>直接在对话框中使用 CComboBoxEx

1. 在对话框编辑器中，将扩展组合框控件添加到对话框模板资源。 指定其控件 ID。

1. 使用扩展组合框控件的 "属性" 对话框指定所需的任何样式。

1. 使用 "[添加成员变量向导](../ide/adding-a-member-variable-visual-cpp.md)" 可使用 Control 属性添加类型为[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)的成员变量。 您可以使用此成员调用 `CComboBoxEx` 成员函数。

1. 使用[类向导](reference/mfc-class-wizard.md)可以在对话框类中为您需要处理的任何扩展组合框控件的通知消息映射处理程序函数（请参阅[将消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)）。

1. 在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)中，为`CComboBoxEx`对象设置任何其他样式。

### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>在非对话框窗口中使用 CComboBoxEx

1. 在视图或窗口类中定义控件。

1. 调用控件的[Create](../mfc/reference/ctabctrl-class.md#create)成员函数，该函数可能在[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)中，可能早于父窗口的[OnCreate](../mfc/reference/cwnd-class.md#oncreate)处理程序函数。 设置控件的样式。

## <a name="see-also"></a>请参阅

[使用 CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[控件](../mfc/controls-mfc.md)
