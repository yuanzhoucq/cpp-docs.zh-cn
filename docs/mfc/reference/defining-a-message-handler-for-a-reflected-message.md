---
title: 为反射消息定义消息处理程序
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.defining.msg.msghandler
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
ms.openlocfilehash: 970dd7072cb8391d76d39536e442d5aab8e0f61d
ms.sourcegitcommit: 65ed563a8a1d4d90f872a2a6edcb086f84ec9f77
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2019
ms.locfileid: "66741603"
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>为反射消息定义消息处理程序

创建新的 MFC 控件类后，可以为其定义消息处理程序。 反射的消息处理程序允许您控制的类来处理其自己的消息之前由父接收消息。 可以使用 MFC [CWnd::SendMessage](../../mfc/reference/cwnd-class.md#sendmessage)函数将从您的控件的消息发送到父窗口。

利用此功能，例如，创建一个列表框，将重绘自己，而不是依赖于父窗口来完成此操作 （所有者绘制）。 有关反射的消息的详细信息，请参阅[处理反射消息](../../mfc/handling-reflected-messages.md)。

若要创建[ActiveX 控件](../../mfc/activex-controls-on-the-internet.md)使用相同的功能，必须创建用于 ActiveX 控件的项目。

> [!NOTE]
>  无法添加反射的消息 (OCM_*消息*) 的 ActiveX 控件并使用属性窗口中，如下所述。 您必须手动添加这些消息。

### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-properties-window"></a>若要定义属性窗口中的反射消息的消息处理程序

1. 向 MFC 项目中添加一个控件，例如列表、 rebar 控件、 一个工具栏或树控件。

1. 在类视图中，单击你的控件类的名称。

1. 在中[属性窗口](/visualstudio/ide/reference/properties-window)，控件类名出现在**类名**列表。

1. 单击**消息**按钮以显示可添加到该控件的 Windows 消息。

1. 向下滚动直到您看到标题属性窗口中的消息列表**反映**。 或者，单击**类别**按钮，并折叠视图以查看**反映**标题。

1. 选择你想要定义一个处理程序的反射的消息。 反射的消息带有等号 （=）。

1. 单击属性窗口来作为处理程序的建议的名称显示在右侧的列中的单元格\<添加 >*HandlerName*。 (例如， **= WM_CTLCOLOR**消息处理程序建议\<添加 >**CtlColor**)。

1. 单击建议的名称以接受。 将处理程序添加到你的项目。

   反射的消息窗口的右侧列中显示已添加的消息处理程序名称。

9. 若要编辑或删除消息处理程序，请重复步骤 4 到 7。 单击包含要编辑或删除并单击相应的任务的处理程序名称的单元格。

## <a name="see-also"></a>请参阅

[将消息映射到函数](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[添加类](../../ide/adding-a-class-visual-cpp.md)<br/>
[添加成员函数](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[添加成员变量](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[重写虚函数](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC 消息处理程序](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[导航类结构](../../ide/navigate-code-cpp.md)
