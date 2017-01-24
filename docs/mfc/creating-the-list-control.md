---
title: "创建列表控件 | Microsoft Docs"
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
  - "CListCtrl 类, 创建控件"
  - "列表控件"
ms.assetid: a4cb1729-31b6-4d2b-a44b-367474848a39
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 创建列表控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

列表控件 \([CListCtrl](../mfc/reference/clistctrl-class.md)\) 如何创建了取决于是否直接使用控件或使用类。[CListView](../mfc/reference/clistview-class.md) 如果您使用 `CListView`，则在其文档\/视图创建序列的一部分，框架使用视图。  创建列表视图创建列表控件 \(两个相同意义\)。  控件视图中处理 [OnCreate](../Topic/CWnd::OnCreate.md) 函数创建。  在此情况下，控件准备要添加项，通过调用为 [GetListCtrl](../Topic/CListView::GetListCtrl.md)。  
  
### 使用 CListCtrl 直接在对话框  
  
1.  在对话框编辑器中，将添加列表控件添加到对话框模板资源。  指定其控件的ID .  
  
2.  使用 [添加成员变量向导](../ide/adding-a-member-variable-visual-cpp.md)添加带有控件属性`CListCtrl` 类型的成员变量。  可以使用此成员调用 `CListCtrl` 成员函数。  
  
3.  使用属性窗口映射在对话框类的处理程序函数需要处理的所有列表控件通知消息 \(参见 [指向函数的信息映射](../mfc/reference/mapping-messages-to-functions.md)\)。  
  
4.  在 [OnInitDialog](../Topic/CDialog::OnInitDialog.md)，设置 `CListCtrl`的样式。  参见[更改列表控件样式 \(MFC\)](../mfc/changing-list-control-styles.md)。  这将确定这“视图”在控件的手指，但您以后可以更改视图。  
  
### 在非对话框窗口使用 CListCtrl  
  
1.  在视图或窗口类中定义控件。  
  
2.  \(如果要把控件子类化\)，请在父窗口[OnCreate](../Topic/CWnd::OnCreate.md) 处理程序函数调用时，调用控件的[Create](../Topic/CListCtrl::Create.md) 成员函数，在 [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md)中。  设置控件的样式。  
  
## 请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)