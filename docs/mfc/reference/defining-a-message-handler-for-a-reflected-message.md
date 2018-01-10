---
title: "为反射消息定义消息处理程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.defining.msg.msghandler
dev_langs: C++
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d9f5e1c472cdbca177b91851f9b8104094c41047
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>为反射消息定义消息处理程序
创建新的 MFC 控件类后，你可以为其定义消息处理程序。 反映的消息处理程序允许你的控件类来处理其自己的消息之前父接收此消息。 你可以使用 MFC [CWnd::SendMessage](../../mfc/reference/cwnd-class.md#sendmessage)函数将从控件的消息发送到父窗口。  
  
 利用此功能，例如，创建一个列表框，将重绘自己，而不是依赖于父窗口完成此操作 （所有者描述）。 反映的消息的详细信息，请参阅[处理反射消息](../../mfc/handling-reflected-messages.md)。  
  
 若要创建[ActiveX 控件](../../mfc/activex-controls-on-the-internet.md)具有相同的功能，你必须创建 ActiveX 控件项目。  
  
> [!NOTE]
>  无法添加反射的消息 (OCM_*消息*) 为 ActiveX 控件并使用属性窗口中，如下所述。 您必须手动添加这些消息。  
  
### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-properties-window"></a>若要定义为反射消息从属性窗口消息处理程序  
  
1.  向 MFC 项目中添加一个控件，如列表、 rebar 控件、 一个工具栏或树控件。  
  
2.  在类视图中，单击你的控件类的名称。  
  
3.  在[属性窗口](/visualstudio/ide/reference/properties-window)，控件类名出现在**类名**列表。  
  
4.  单击**消息**按钮以显示可添加到控件的 Windows 消息。  
  
5.  向下滚动属性窗口之前查看的标题中的消息列表**反映**。 或者，单击**类别**按钮和折叠视图以查看**反映**标题。  
  
6.  选择你想要定义处理程序的反射的消息。 反映的消息都标有一个等号 （=）。  
  
7.  单击在属性窗口来显示为处理程序的建议的名称右侧列中的单元格\<添加 >*HandlerName*。 (例如， **= WM_CTLCOLOR**消息处理程序提供的建议\<添加 >**CtlColor**)。  
  
8.  单击要接受的建议的名称。 处理程序添加到你的项目。  
  
     已添加的消息处理程序名称显示在右侧列反映的消息窗口。  
  
9. 若要编辑或删除消息处理程序，请重复步骤 4 到 7。 单击包含要编辑或删除并单击相应的任务的处理程序名称的单元格。  
  
## <a name="see-also"></a>请参阅  
 [将消息映射到函数](../../mfc/reference/mapping-messages-to-functions.md)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [添加类](../../ide/adding-a-class-visual-cpp.md)   
 [添加成员函数](../../ide/adding-a-member-function-visual-cpp.md)   
 [添加成员变量](../../ide/adding-a-member-variable-visual-cpp.md)   
 [重写虚函数](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 消息处理程序](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [导航类结构](../../ide/navigating-the-class-structure-visual-cpp.md)
