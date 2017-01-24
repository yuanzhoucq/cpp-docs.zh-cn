---
title: "对话栏 | Microsoft Docs"
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
  - "CDialogBar 类, 对话栏"
  - "控件条, 对话栏"
  - "对话栏"
  - "对话栏, 关于对话栏"
  - "MFC, 控件条"
ms.assetid: 485c8055-6bb0-4051-8417-dd2971499321
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 对话栏
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对话栏是工具栏，可以包含任何控件的 [控件条](../mfc/control-bars.md)。  由于具有无模式对话框，[CDialogBar](../mfc/reference/cdialogbar-class.md) 对象提供更强大的工具栏。  
  
 工具栏和 `CDialogBar` 对象之间有一些重要差异。  `CDialogBar` 对象从对话框模板资源创建，可以使用 Visual C\+\+ 对话框编辑器创建，并且可包含任何窗口控件。  用户可以控件间切换。  并且您可以指定对齐样式来对齐对话栏到父框架窗口的任何部分或者让其不懂在父窗口调整后。  下图演示各种各样控件的对话栏。  
  
 ![VC 对话栏](../mfc/media/vc378t1.png "vc378T1")  
对话栏  
  
 在其他方面，使用 `CDialogBar` 对象与使用无模式对话框一样。  使用对话框编辑器来设计和创建对话框资源。  
  
 对话栏的优点之一是不仅可以包括按钮，也可以包含控件。  
  
 当从 `CDialog` 正常派生自己的对话框类时，您通常不为对话栏派生您自己的类。  对话栏为主窗口的扩展，并且所有对话栏控件通知信息，如 **BN\_CLICKED** 或 **EN\_CHANGE**，将被传送到对话栏的父级，主窗口。  
  
## 请参阅  
 [用户界面元素](../mfc/user-interface-elements-mfc.md)   
 [示例](../top/visual-cpp-samples.md)