---
title: 为反射消息定义消息处理程序
ms.date: 09/07/2019
f1_keywords:
- vc.codewiz.defining.msg.msghandler
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
ms.openlocfilehash: 1e38c63464cacf445688a1d431a65af21eac86f4
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907933"
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>为反射消息定义消息处理程序

创建新的 MFC 控件类后，可以为其定义消息处理程序。 反射的消息处理程序允许控件类在父消息收到消息之前处理自己的消息。 可以使用 MFC [CWnd：： SendMessage](../../mfc/reference/cwnd-class.md#sendmessage)函数将来自控件的消息发送到父窗口。

例如，利用此功能，您可以创建一个将重绘自身的列表框，而不是依赖于父窗口来执行此操作（由所有者描述）。 有关反射消息的详细信息，请参阅[处理反射的消息](../../mfc/handling-reflected-messages.md)。

若要创建具有相同功能的[activex 控件](../../mfc/activex-controls-on-the-internet.md)，必须创建 activex 控件的项目。

> [!NOTE]
>  你无法使用类向导为 ActiveX 控件添加反射消息（OCM_*消息*），如下所述。 您必须手动添加这些消息。

### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-class-wizard"></a>从类向导为反射消息定义消息处理程序

1. 向 MFC 项目添加控件，例如列表、rebar 控件、工具栏或树控件。

1. 在类视图中，单击控件类的名称。

1. 在[类向导](mfc-class-wizard.md)中，控件类名称出现在 "**类名称**" 列表中。

1. 单击 "**消息**" 选项卡以显示可添加到控件的 Windows 消息。

1. 选择要为其定义处理程序的反射消息。 反射消息标记为等号（=）。

1. 单击类向导右栏中的单元格，以将建议的处理程序名称显示为\<add >*HandlerName*。 （例如， **= WM_CTLCOLOR**消息处理程序建议\<add >**CTLCOLOR**）。

1. 单击建议的名称以接受。 处理程序将添加到你的项目中。

1. 若要编辑或删除消息处理程序，请重复步骤4到步骤7。 单击包含要编辑或删除的处理程序名称的单元格，然后单击相应的任务。

## <a name="see-also"></a>请参阅

[将消息映射到函数](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[添加类](../../ide/adding-a-class-visual-cpp.md)<br/>
[添加成员函数](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[添加成员变量](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[重写虚函数](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC 消息处理程序](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[导航类结构](../../ide/navigate-code-cpp.md)
