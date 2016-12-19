---
title: "创建标题控件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "CHeaderCtrl 类, 创建"
  - "标题控件, 创建"
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 创建标题控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

标题控件没有直接可用在对话框编辑器 \(尽管可以向列表控件，包含一个标题控件\)。  
  
### 放置在对话框标题控件  
  
1.  请手动嵌入类型 [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) 中的成员变量。对话框类。  
  
2.  在 [OnInitDialog](../Topic/CDialog::OnInitDialog.md)，请创建一个并设置 `CHeaderCtrl`的样式，它确定，并显示它。  
  
3.  向标题控件添加项  
  
4.  使用属性窗口映射在对话框类的处理程序函数需要处理的所有头控件通知消息 \(参见 [指向函数的信息映射](../mfc/reference/mapping-messages-to-functions.md)\)。  
  
### 将标题控件不包括在视图 \(并非 CListView\)  
  
1.  嵌入视图类的 [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) 一个对象。  
  
2.  样式，位置，并显示视图中 [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) 成员函数控制窗口的标题。  
  
3.  向标题控件添加项  
  
4.  使用属性窗口映射在试图类的处理程序函数需要处理的所有头控件通知消息 \(参见 [指向函数的信息映射](../mfc/reference/mapping-messages-to-functions.md)\)。  
  
 在任何情况下，视图，当或对话框创建对象时，嵌入的控件对象。  然后必须调用 [CHeaderCtrl::Create](../Topic/CHeaderCtrl::Create.md) 创建控制窗口。  定位控件，调用 [CHeaderCtrl::Layout](../Topic/CHeaderCtrl::Layout.md) 确定控件的初始设置所需位置的大小以及定位和 [SetWindowPos](../Topic/CWnd::SetWindowPos.md)。  再添加项。[标题控件添加项。](../mfc/adding-items-to-the-header-control.md)所述。  
  
 有关详细信息，请参阅[创建头控件](http://msdn.microsoft.com/library/windows/desktop/bb775238) in the [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]。  
  
## 请参阅  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控件](../mfc/controls-mfc.md)