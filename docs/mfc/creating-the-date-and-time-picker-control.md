---
title: "创建日期和时间选择器控件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDateTimeCtrl 类, 创建"
  - "DateTimePicker 控件 [MFC], 创建"
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 创建日期和时间选择器控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

日期时间选择器和控件如何创建根据您是在对话框中使用控件还是在nondialog 窗口创建。  
  
### 使用 CDateTimeCtrl 直接在对话框  
  
1.  在对话框编辑器中，添加日期时间选择器控件添加到对话框模板资源。  指定其控件的ID .  
  
2.  指定所有需要的样式，使用日期和时间选择器控件的属性对话框。  
  
3.  使用 [添加成员变量向导](../ide/adding-a-member-variable-visual-cpp.md)添加带有控件属性[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md) 类型的成员变量。  可以使用此成员调用 `CDateTimeCtrl` 成员函数。  
  
4.  使用属性窗口映射在对话框类的处理程序函数需要处理的所有日期选择器控件[通知](../mfc/processing-notification-messages-in-date-and-time-picker-controls.md)消息 \(参见 [指向函数的信息映射](../mfc/reference/mapping-messages-to-functions.md) \)。  
  
5.  在 [OnInitDialog](../Topic/CDialog::OnInitDialog.md)，设置所有 `CDateTimeCtrl` 对象的附加样式。  
  
### 在非对话框窗口使用 CDateTimeCtrl  
  
1.  在视图或窗口类中定义控件。  
  
2.  \(如果要把控件子类化\)，请在父窗口[OnCreate](../Topic/CWnd::OnCreate.md) 处理程序函数调用时，调用控件的[Create](../Topic/CTabCtrl::Create.md) 成员函数，在 [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md)中。  设置控件的样式。  
  
## 请参阅  
 [使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [控件](../mfc/controls-mfc.md)