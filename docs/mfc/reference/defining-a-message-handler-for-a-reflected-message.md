---
title: "为反射消息定义消息处理程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.defining.msg.msghandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "消息处理, 反映的消息"
  - "消息, 已反映"
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 为反射消息定义消息处理程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建了新的 MFC 控件类后，可为其定义消息处理程序。  反射消息处理程序允许控件类在父级收到消息之前处理自己的消息。  可使用 MFC [CWnd::SendMessage](../Topic/CWnd::SendMessage.md) 函数将消息从控件发送到父窗口。  
  
 利用此功能，比如可创建重绘自身而不是依赖父窗口完成此操作（所有者描述的）的列表框。  有关反射消息的更多信息，请参见[处理反射消息](../../mfc/handling-reflected-messages.md)。  
  
 若要创建具有相同功能的 [ActiveX 控件](../../mfc/activex-controls-on-the-internet.md)，必须为 ActiveX 控件创建项目。  
  
> [!NOTE]
>  不能用“属性”窗口为 ActiveX 控件添加反射消息 \(OCM\_*Message*\)，如下所述。  必须手动添加这些消息。  
  
### 从“属性”窗口中为反射消息定义消息处理程序  
  
1.  向 MFC 项目添加控件，如列表控件 \(List Control\)、rebar 控件、工具栏 \(ToolBar\) 控件或树控件 \(Tree Control\)。  
  
2.  在“类视图”中，单击控件类的名称。  
  
3.  在[“属性”窗口](../Topic/Properties%20Window.md)中，控件类名出现在**“类名”**列表中。  
  
4.  单击“消息”按钮显示可用于添加到控件的 Windows 消息。  
  
5.  在“属性”窗口中向下滚动消息列表，直到可以看到标题“已反映”。  或者，单击**“类别”**按钮并折叠视图以看到“已反映”标题。  
  
6.  选择要为其定义处理程序的反射消息。  反射消息用等号 \(\=\) 标记。  
  
7.  在“属性”窗口中，单击右列中的单元格以将建议的处理程序名称显示为\<add\>*HandlerName*。（例如，**\=WM\_CTLCOLOR** 消息处理程序建议 \<add\>**CtlColor** 名称。）  
  
8.  单击建议的名称以接受。  处理程序被添加到项目中。  
  
     已添加的消息处理程序名称出现在反射消息窗口的右列中。  
  
9. 若要编辑或删除消息处理程序，请重复第 4 到第 7 步。  单击包含要编辑或删除的处理程序名称的单元格并单击适当的任务。  
  
## 请参阅  
 [将消息映射到函数](../../mfc/reference/mapping-messages-to-functions.md)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [添加类](../../ide/adding-a-class-visual-cpp.md)   
 [添加成员函数](../../ide/adding-a-member-function-visual-cpp.md)   
 [添加成员变量](../../ide/adding-a-member-variable-visual-cpp.md)   
 [重写虚函数](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 消息处理程序](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [导航类结构](../../ide/navigating-the-class-structure-visual-cpp.md)