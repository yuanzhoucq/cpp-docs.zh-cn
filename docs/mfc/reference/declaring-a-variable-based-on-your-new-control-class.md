---
title: "声明基于新控件类的变量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.classes.control.variable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "类 [C++], 声明变量基于"
  - "控件类, 变量"
  - "变量, 控件类"
ms.assetid: 5722dc38-c0eb-40bd-93da-67a808140d03
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 声明基于新控件类的变量
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建了 MFC 控件类后，可以声明基于它的变量。  若要为新变量提供上下文，必须打开对话框编辑器，编辑要在其中使用可重用控件的对话框。  而且，对话框必须已经有与它相关联的类。  有关使用对话框编辑器的信息，请参见[对话框编辑器](../../mfc/dialog-editor.md)。  
  
### 声明基于可重用类的变量  
  
1.  在编辑对话框时，将与新控件的基类具有相同类型的控件从“控件”工具栏拖到对话框上。  
  
2.  将鼠标指针放在拖动的控件上。  
  
3.  按下 Ctrl 键，同时双击该控件。  
  
     出现[添加成员变量](../../ide/add-member-variable-wizard.md)对话框。  
  
4.  在“访问权限”框中，为控件选择正确的访问。  
  
5.  单击“控件变量”复选框。  
  
6.  在“变量名”框中，键入名称。  
  
7.  在“类别”下，单击“控件”。  
  
8.  在“控件 ID”列表中，选取已添加的控件。  “变量类型”列表应显示正确的变量类型，而“控件类型”框应显示正确的控件类型。  
  
9. 在“注释”框中，添加希望在代码中出现的注释。  
  
10. 单击**“确定”**。  
  
## 请参阅  
 [将消息映射到函数](../../mfc/reference/mapping-messages-to-functions.md)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [添加类](../../ide/adding-a-class-visual-cpp.md)   
 [添加成员函数](../../ide/adding-a-member-function-visual-cpp.md)   
 [添加成员变量](../../ide/adding-a-member-variable-visual-cpp.md)   
 [重写虚函数](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 消息处理程序](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [导航类结构](../../ide/navigating-the-class-structure-visual-cpp.md)