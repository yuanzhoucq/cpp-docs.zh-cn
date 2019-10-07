---
title: 经常重写的成员函数
ms.date: 09/06/2019
helpviewer_keywords:
- CDialog class [MFC], members
- OnInitDialog function
- dialog classes [MFC], commonly overridden member functions
- OnCancel function
- overriding, dialog class members
- OnOK function
- MFC dialog boxes [MFC], overriding member functions
ms.assetid: 78eb566c-e361-4c86-8db5-c7e2791b249a
ms.openlocfilehash: 51a647bb50415af71d6d148d3139f906f503ee2a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685816"
---
# <a name="commonly-overridden-member-functions"></a>经常重写的成员函数

下表列出了最有可能在 `CDialog` 派生类中重写的成员函数。

### <a name="commonly-overridden-member-functions-of-class-cdialog"></a>类 CDialog 的常用已重写成员函数

|成员函数|其响应的消息|重写目的|
|---------------------|----------------------------|-----------------------------|
|`OnInitDialog`|**WM_INITDIALOG**|初始化对话框的控件。|
|`OnOK`|按钮**IDOK**的**BN_CLICKED**|当用户单击“确定”按钮时响应。|
|`OnCancel`|按钮**IDCANCEL**的**BN_CLICKED**|当用户单击“取消”按钮时响应。|

`OnInitDialog`、`OnOK` 和 `OnCancel` 是虚拟函数。 若要重写它们，请使用[MFC 类向导](reference/mfc-class-wizard.md)在派生对话框类中声明重写函数。

在显示此对话框之前调用 `OnInitDialog`。 您必须通过重写调用默认 `OnInitDialog` 处理程序 - 一般作为处理程序的第一个操作。 默认情况下`OnInitDialog` ，返回**TRUE**以指示应将焦点设置到对话框中的第一个控件。

通常将为无模式对话框而不是模式对话框重写 `OnOK`。 如果为模式对话框重写此处理程序，则通过您的重写调用基类 - 以确保调用 `EndDialog` — 或调用 `EndDialog` 本身。

通常将为无模式对话框重写 `OnCancel`。

有关这些成员函数的详细信息，请参阅*Mfc 参考*中的[CDialog](../mfc/reference/cdialog-class.md)类和有关在[mfc 中使用对话框](../mfc/life-cycle-of-a-dialog-box.md)的讨论。

## <a name="see-also"></a>请参阅

[对话框](../mfc/dialog-boxes.md)<br/>
[经常添加的成员函数](../mfc/commonly-added-member-functions.md)
