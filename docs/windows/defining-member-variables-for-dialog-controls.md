---
title: "Defining Member Variables for Dialog Controls | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "member variables, defining for controls"
  - "variables, dialog box control member variables"
  - "controls [C++], member variables"
  - "Dialog editor, defining member variables for controls"
ms.assetid: 84347c63-c33c-4b04-91f5-6d008c45ba58
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Defining Member Variables for Dialog Controls
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

要定义除按钮外的任何对话框控件的成员变量，可以使用以下方法。  
  
> [!NOTE]
>  本文仅适用于 MFC 项目中的对话框控件。  ATL 项目应使用“新建 Windows 消息和事件处理程序”对话框。  
  
### 定义（非按钮）对话框控件的成员变量  
  
1.  在[对话框编辑器](../mfc/dialog-editor.md)中选择一个控件。  
  
2.  按 **CTRL** 键的同时双击对话框控件。  
  
     将出现[添加成员变量向导](../ide/add-member-variable-wizard.md)。  
  
3.  在“添加成员变量”向导中键入相应信息。  有关详细信息，请参阅[对话框数据交换](../mfc/dialog-data-exchange.md)。  
  
4.  单击“确定”以返回到对话框编辑器。  
  
    > [!TIP]
    >  若要从任何对话框控件跳转到其现有的处理程序，请双击该控件。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。 有关手动将资源文件添加到托管项目、访问资源、显示静态资源以及将资源字符串分配给属性的信息，请参阅[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 也可以使用“MFC 类向导”中的“成员变量”选项卡为指定的类添加新成员变量，并查看已定义的变量。  
  
 要求  
  
 MFC  
  
## 请参阅  
 [将消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)   
 [用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [MFC 类向导](../mfc/reference/mfc-class-wizard.md)   
 [添加类](../ide/adding-a-class-visual-cpp.md)   
 [添加成员函数](../ide/adding-a-member-function-visual-cpp.md)   
 [添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)   
 [重写虚函数](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 消息处理程序](../mfc/reference/adding-an-mfc-message-handler.md)