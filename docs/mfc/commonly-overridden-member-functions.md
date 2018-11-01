---
title: 经常重写的成员函数
ms.date: 11/04/2016
helpviewer_keywords:
- CDialog class [MFC], members
- OnInitDialog function
- dialog classes [MFC], commonly overridden member functions
- OnCancel function
- overriding, dialog class members
- OnOK function
- MFC dialog boxes [MFC], overriding member functions
ms.assetid: 78eb566c-e361-4c86-8db5-c7e2791b249a
ms.openlocfilehash: 163da1ee6e98e974af0fd1a6b27e1b2df85e9ce0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439569"
---
# <a name="commonly-overridden-member-functions"></a>经常重写的成员函数

下表列出了最有可能在 `CDialog` 派生类中重写的成员函数。

### <a name="commonly-overridden-member-functions-of-class-cdialog"></a>类 CDialog 的常用已重写成员函数

|成员函数|其响应的消息|重写目的|
|---------------------|----------------------------|-----------------------------|
|`OnInitDialog`|**WM_INITDIALOG**|初始化对话框的控件。|
|`OnOK`|**BN_CLICKED**按钮**IDOK**|当用户单击“确定”按钮时响应。|
|`OnCancel`|**BN_CLICKED**按钮**IDCANCEL**|当用户单击“取消”按钮时响应。|

`OnInitDialog`、`OnOK` 和 `OnCancel` 是虚拟函数。 若要重写它们，重写函数中声明派生的对话框类使用[属性窗口](/visualstudio/ide/reference/properties-window)。

在显示此对话框之前调用 `OnInitDialog`。 您必须通过重写调用默认 `OnInitDialog` 处理程序 - 一般作为处理程序的第一个操作。 默认情况下`OnInitDialog`将返回**TRUE**以指示应在对话框中的第一个空间设置焦点。

通常将为无模式对话框而不是模式对话框重写 `OnOK`。 如果为模式对话框重写此处理程序，则通过您的重写调用基类 - 以确保调用 `EndDialog` — 或调用 `EndDialog` 本身。

通常将为无模式对话框重写 `OnCancel`。

有关这些成员函数的详细信息，请参阅类[CDialog](../mfc/reference/cdialog-class.md)中*MFC 参考*上的所有讨论[对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)。

## <a name="see-also"></a>请参阅

[对话框](../mfc/dialog-boxes.md)<br/>
[经常添加的成员函数](../mfc/commonly-added-member-functions.md)
