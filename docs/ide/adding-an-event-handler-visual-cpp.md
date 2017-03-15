---
title: "添加事件处理程序 (Visual C++) | Microsoft Docs"
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
  - "vc.codewiz.eventhandler.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "事件处理程序, 添加"
  - "MSBuild, 属性"
  - "属性 [Visual Studio], MSBuild"
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 添加事件处理程序 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从资源编辑器中，可以使用[事件处理程序向导](../ide/event-handler-wizard.md)为对话框控件添加新的事件处理程序，或编辑现有的事件处理程序。  
  
 可以使用[“属性”窗口](../Topic/Properties%20Window.md)向实现对话框的类添加事件。  如果要向对话框类以外的类添加事件，请使用“事件处理程序向导”。  
  
### 向对话框控件添加事件处理程序  
  
1.  在[资源视图](../windows/resource-view-window.md)中双击对话框资源，以打开包含[对话框编辑器](../mfc/dialog-editor.md)中的控件的对话框资源。  
  
2.  右击要为其处理通知事件的控件。  
  
3.  在快捷菜单上，单击**“添加事件处理程序”**以显示事件处理程序向导。  
  
4.  在“消息类型”框中选择要添加到“类列表”框中的选定类的事件。  
  
5.  接受“函数处理程序名称”框中的默认名称，或提供自己选择的名称。  
  
6.  单击“添加并编辑”，向项目中添加事件处理程序，并在新函数处打开文本编辑器，添加适当的事件处理程序代码。  
  
     如果选定的消息类型已经具有选定类的事件处理程序，则“添加并编辑”不可用，而“编辑代码”可用。  单击“编辑代码”以现有函数打开文本编辑器。  
  
 或者，可以从[“属性”窗口](../Topic/Properties%20Window.md)添加事件处理程序。  有关更多信息，请参见[添加对话框控件的事件处理程序](../mfc/adding-event-handlers-for-dialog-box-controls.md)。  
  
## 请参阅  
 [用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [添加类](../ide/adding-a-class-visual-cpp.md)   
 [添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)   
 [添加成员函数](../ide/adding-a-member-function-visual-cpp.md)   
 [MFC 消息处理程序](../mfc/reference/adding-an-mfc-message-handler.md)   
 [导航类结构](../ide/navigating-the-class-structure-visual-cpp.md)