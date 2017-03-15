---
title: "将控件添加到属性表 | Microsoft Docs"
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
  - "控件 [MFC], 添加到属性表"
  - "属性表, 添加控件"
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 将控件添加到属性表
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

默认情况下，属性表将为属性页、选项卡索引和OK，取消，应用按钮分配窗口区域。\(处于非模式属性表没有OK,取消，和应用按钮。\)您可以添加其他控件到属性表。  例如，您可以在属性页区域右侧添加该预览窗口显示用户当前设置将会是什么样子，如果应用到外部对象。  
  
 可以将控件添加到在 `OnCreate` 处理程序的属性表对话框。  包容的附加控件通常需要扩展属性表对话框的大小。  在调用基类**CPropertySheet::OnCreate**之后,调用 [GetWindowRect](../Topic/CWnd::GetWindowRect.md) 获取当前分配的属性表窗口的宽度和高度，展开矩形的尺寸，同时调用 [MoveWindow](../Topic/CWnd::MoveWindow.md) 更改属性表窗口的大小。  
  
## 请参阅  
 [属性表](../mfc/property-sheets-mfc.md)   
 [CPropertyPage Class](../mfc/reference/cpropertypage-class.md)   
 [CPropertySheet Class](../mfc/reference/cpropertysheet-class.md)