---
title: "创建扩展组合框控件 | Microsoft Docs"
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
  - "CComboBoxEx 类, 创建扩展组合框控件"
  - "扩展组合框"
  - "扩展组合框, 创建"
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 创建扩展组合框控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如何扩张组合框控件是根据您在对话框中使用控件还是在无对话框窗口中创建它。。  
  
### 使用 CComboBoxEx 直接在对话框  
  
1.  在对话框编辑器中，添加扩展组合框控件添加到对话框模板资源。  指定其控件的ID .  
  
2.  指定使用扩展组合框控件的属性对话框，所有需要的样式。  
  
3.  使用 [添加成员变量向导](../ide/adding-a-member-variable-visual-cpp.md)添加带有控件属性[CComboBoxEx](../mfc/reference/ccomboboxex-class.md) 类型的成员变量。  可以使用此成员调用 `CComboBoxEx` 成员函数。  
  
4.  使用属性窗口在对话框类的处理程序函数需要映射处理的所有扩展组合框控件通知消息 \(参见 [指向函数的信息映射](../mfc/reference/mapping-messages-to-functions.md)\)。  
  
5.  在 [OnInitDialog](../Topic/CDialog::OnInitDialog.md)，设置所有 `CComboBoxEx` 对象的附加样式。  
  
### 在非对话框窗口使用 CComboBoxEx  
  
1.  在视图或窗口类中定义控件。  
  
2.  早在父窗口中 [OnCreate](../Topic/CWnd::OnCreate.md) 处理程序函数调用控件的函数 [创建](../Topic/CTabCtrl::Create.md) 成员，可以在 [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md)，可能。  设置控件的样式。  
  
## 请参阅  
 [使用 CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [控件](../mfc/controls-mfc.md)