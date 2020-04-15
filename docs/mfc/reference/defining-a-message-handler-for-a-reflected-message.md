---
title: 为反射消息定义消息处理程序
ms.date: 09/07/2019
f1_keywords:
- vc.codewiz.defining.msg.msghandler
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
ms.openlocfilehash: f7f90d3347ac61abcfcb48e77ef39aa2626ae5c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365859"
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>为反射消息定义消息处理程序

创建新的 MFC 控件类后，可以为其定义消息处理程序。 反射的消息处理程序允许控件类在父级收到消息之前处理其自己的消息。 您可以使用 MFC [CWnd：：SendMessage](../../mfc/reference/cwnd-class.md#sendmessage)函数将消息从控件发送到父窗口。

例如，借助此功能，您可以创建一个列表框，该列表框将重新绘制自身，而不是依赖父窗口来执行此操作（绘制所有者）。 有关反射邮件的详细信息，请参阅[处理反映的消息](../../mfc/handling-reflected-messages.md)。

要创建具有相同功能的[ActiveX 控件](../../mfc/activex-controls-on-the-internet.md)，必须为 ActiveX 控件创建项目。

> [!NOTE]
> 不能使用类向导为 ActiveX 控件添加反射消息 （OCM_*消息*），如下所述。 您必须手动添加这些消息。

### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-class-wizard"></a>为来自类向导的反射消息定义消息处理程序

1. 向 MFC 项目添加控件，如列表、钢筋控件、工具栏或树控件。

1. 在类视图中，单击控件类的名称。

1. 在[类向导](mfc-class-wizard.md)中，控件类名称将显示在**类名称**列表中。

1. 单击"**消息"** 选项卡以显示可用于添加到控件的 Windows 消息。

1. 选择要为其定义处理程序的反射消息。 反射的消息用等号 （*） 标记。

1. 单击类向导右列中的单元格，以添加>\<*处理程序名称*）显示处理程序的建议名称。 （例如 **，#WM_CTLCOLOR**消息处理程序建议\<添加>**CtlColor**。

1. 单击要接受的建议名称。 处理程序将添加到您的项目中。

1. 要编辑或删除消息处理程序，请重复步骤 4 到 7。 单击包含处理程序名称的单元格以编辑或删除，然后单击相应的任务。

## <a name="see-also"></a>另请参阅

[将消息映射到函数](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[添加类](../../ide/adding-a-class-visual-cpp.md)<br/>
[添加成员函数](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[添加成员变量](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[重写虚函数](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC 消息处理程序](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[导航类结构](../../ide/navigate-code-cpp.md)
