---
title: "Editing Control Properties | Microsoft Docs"
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
  - "controls [C++], undoing changes"
  - "controls [C++], editing properties"
  - "dialog box controls, editing properties"
ms.assetid: 9bdae21d-6dec-4344-a197-2ca4fc46d040
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Editing Control Properties
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 编辑控件的属性  
  
1.  在对话框中，选择要修改的控件。  
  
    > [!NOTE]
    >  如果选择多个控件，则只能编辑所选控件的共同属性。  
  
2.  在[“属性”窗口](../Topic/Properties%20Window.md)中，更改控件的属性。  
  
    > [!NOTE]
    >  将按钮、单选按钮或复选框控件的 **Bitmap** 属性设置为 **True** 后，将为控件实现样式 BS\_BITMAP。  有关更多信息，请参见[按钮样式](../mfc/reference/button-styles.md)。  有关将位图与控件相关联的示例，请参见 [CButton::SetBitmap](../Topic/CButton::SetBitmap.md)。  在对话框资源编辑器中时，位图不会出现在控件上。  
  
### 撤消对控件属性的更改  
  
1.  确保控件在对话框编辑器中具有焦点。  
  
2.  从“编辑”菜单中选择“撤消”（如果焦点不在控件上，“撤消”命令将不可用）。  
  
 有关将资源添加到托管项目的信息，请参见“NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 Win32  
  
## 请参阅  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)