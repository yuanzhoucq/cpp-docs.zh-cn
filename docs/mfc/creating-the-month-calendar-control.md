---
title: "创建月历控件 | Microsoft Docs"
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
  - "CMonthCalCtrl 类, 创建"
  - "月历控件"
  - "月历控件, 创建"
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 创建月历控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

月历控件如何创建是根据您在是对话框中使用控件还是在对话框窗口中无创建它。  
  
### 在对话框中直接使用 CMonthCalCtrl  
  
1.  在对话框编辑器中，将月历控件添加到对话框模板资源。  指定其控件的ID .  
  
2.  指定所有需要的样式，使用月历控件的属性对话框。  
  
3.  使用 [添加成员变量向导](../ide/adding-a-member-variable-visual-cpp.md)添加带有控件属性[CDateTimeCtrl](../mfc/reference/cmonthcalctrl-class.md) 类型的成员变量。  可以使用此成员调用 `CMonthCalCtrl` 成员函数。  
  
4.  使用属性窗口映射在需要处理所有月历控件通知消息的对话类中处理程序函数 \(参见 [映射信息到函数](../mfc/reference/mapping-messages-to-functions.md)\)。  
  
5.  在 [OnInitDialog](../Topic/CDialog::OnInitDialog.md)，设置所有 `CMonthCalCtrl` 对象的附加样式。  
  
### 在非对话框窗口使用CMonthCalCtrl  
  
1.  在视图或窗口类中定义控件。  
  
2.  \(如果要把控件子类化\)，请在父窗口[OnCreate](../Topic/CWnd::OnCreate.md) 处理程序函数调用时，调用控件的[Create](../Topic/CMonthCalCtrl::Create.md) 成员函数，可能在 [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md)中。  设置控件的样式。  
  
## 请参阅  
 [使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [控件](../mfc/controls-mfc.md)