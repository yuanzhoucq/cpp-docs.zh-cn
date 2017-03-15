---
title: "为反射消息定义消息处理程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.defining.msg.msghandler
dev_langs:
- C++
helpviewer_keywords:
- messages, reflected
- message handling, reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 0033c75d351aa201a0c18e81395d764b9d45761b
ms.lasthandoff: 02/24/2017

---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>为反射消息定义消息处理程序
一旦创建新的 MFC 控件类后，您可以为其定义消息处理程序。 反射的消息处理程序允许您控制的类来处理其自己的消息之前由父接收消息。 您可以使用 MFC [CWnd::SendMessage](../../mfc/reference/cwnd-class.md#sendmessage)函数以将从您的控件的消息发送到父窗口。  
  
 利用此功能，例如，创建一个列表框，将重绘其自身，而不是依赖于父窗口完成此操作 （所有者描述）。 有关反射的消息的详细信息，请参阅[处理反射消息](../../mfc/handling-reflected-messages.md)。  
  
 若要创建[ActiveX 控件](../../mfc/activex-controls-on-the-internet.md)具有相同的功能，必须创建 ActiveX 控件项目。  
  
> [!NOTE]
>  您不能添加反射的消息 (OCM_*消息*) 为 ActiveX 控件并使用属性窗口中，如下所述。 您必须手动添加这些消息。  
  
### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-properties-window"></a>若要定义的消息处理程序属性窗口中的反射消息  
  
1.  将一个控件，如列表、 rebar 控件、 一个工具栏或树控件中，添加到 MFC 项目中。  
  
2.  在类视图中，单击您的控件类的名称。  
  
3.  在[属性窗口](/visualstudio/ide/reference/properties-window)，控件类名出现在**类名**列表。  
  
4.  单击**消息**按钮以显示可添加到该控件的 Windows 消息。  
  
5.  向下滚动直到您看到标题属性窗口中的消息列表**反映**。 或者，单击**类别**按钮和折叠视图以查看**反映**标题。  
  
6.  选择你想要定义一个处理程序的反射的消息。 用等号 （=） 进行标记反映的消息。  
  
7.  单击属性窗口来作为处理程序的建议的名称显示在右列中的单元格\<添加&1;>*HandlerName*。 (例如， **= WM_CTLCOLOR**消息处理程序建议\<添加&1;>**CtlColor**)。  
  
8.  单击建议的名称以接受。 将处理程序添加到你的项目。  
  
     已添加的消息处理程序名称显示在反映的消息窗口右列中。  
  
9. 若要编辑或删除消息处理程序，请重复步骤 4 到 7。 单击包含要编辑或删除，然后单击合适的任务的处理程序名称的单元格。  
  
## <a name="see-also"></a>另请参阅  
 [消息映射到函数](../../mfc/reference/mapping-messages-to-functions.md)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [添加类](../../ide/adding-a-class-visual-cpp.md)   
 [添加成员函数](../../ide/adding-a-member-function-visual-cpp.md)   
 [添加成员变量](../../ide/adding-a-member-variable-visual-cpp.md)   
 [重写虚函数](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 消息处理程序](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [导航类结构](../../ide/navigating-the-class-structure-visual-cpp.md)

