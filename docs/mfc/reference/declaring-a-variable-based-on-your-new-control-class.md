---
title: 声明基于新控件类的变量
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.control.variable
helpviewer_keywords:
- variables [MFC], control classes
- control classes [MFC], variables
- classes [MFC], declaring variables based on
ms.assetid: 5722dc38-c0eb-40bd-93da-67a808140d03
ms.openlocfilehash: 994f81524001a80d1cf0dd3783b9de742d61e84d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365847"
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>声明基于新控件类的变量

创建 MFC 控制类后，可以基于它声明变量。 要为新变量提供上下文，必须打开对话框编辑器并编辑要在其中使用可重用控件的对话框。 此外，对话框必须已具有与其关联的类。 有关使用对话框编辑器的信息，请参阅[对话框编辑器](../../windows/dialog-editor.md)。

### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>基于可重用类声明变量

1. 编辑对话框时，将与新控件的基类相同的控件从"控件"工具栏拖动到对话框中。

1. 将鼠标指针放在丢弃的控件上。

1. 按下 CTRL 键时，双击控件。

   将显示"[添加成员变量"](../../ide/add-member-variable-wizard.md)对话框。

1. 在 **"访问"** 框中，为控件选择正确的访问。

1. 单击 **"控制变量**"复选框。

1. 在 **"变量名称"** 框中，键入名称。

1. 在**类别**下，单击 **"控制**"。

1. 在 **"控件 ID"** 列表中，选择添加的控件。 **变量类型**列表应显示正确的变量类型，**控件类型**框应显示正确的控件类型。

1. 在 **"注释"** 框中，添加要在代码中显示的任何注释。

1. 单击“确定”。 

## <a name="see-also"></a>另请参阅

[将消息映射到函数](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[添加类](../../ide/adding-a-class-visual-cpp.md)<br/>
[添加成员函数](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[添加成员变量](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[重写虚函数](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC 消息处理程序](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[导航类结构](../../ide/navigate-code-cpp.md)
