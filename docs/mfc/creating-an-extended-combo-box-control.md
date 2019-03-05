---
title: 创建扩展组合框控件
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
ms.openlocfilehash: bfc201fbb10c3caa3eaabd0e81206b9493ff7196
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281611"
---
# <a name="creating-an-extended-combo-box-control"></a>创建扩展组合框控件

如何创建扩展的组合框控件取决于您是在对话框中使用控件还是在非对话框窗口中创建它。

### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>若要在对话框中直接使用 CComboBoxEx

1. 在对话框编辑器中，将添加到对话框模板资源的一个扩展组合框控件。 指定其控件 ID。

1. 指定任何所需，使用属性对话框中的扩展的组合框控件样式。

1. 使用[添加成员变量向导](../ide/adding-a-member-variable-visual-cpp.md)若要添加的成员变量的类型[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)与控件属性。 您可以使用此成员调用 `CComboBoxEx` 成员函数。

1. 使用属性窗口映射您需要处理任何扩展的组合框控件通知消息的对话框类中的处理程序函数 (请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md))。

1. 在中[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)，设置为任何其他样式`CComboBoxEx`对象。

### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>若要在非对话框窗口中使用 CComboBoxEx

1. 在视图或窗口类中定义控件。

1. 调用控件的[创建](../mfc/reference/ctabctrl-class.md#create)成员函数，这有可能在[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)，作为父窗口可能早[OnCreate](../mfc/reference/cwnd-class.md#oncreate)处理程序函数。 设置控件的样式。

## <a name="see-also"></a>请参阅

[使用 CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[控件](../mfc/controls-mfc.md)
