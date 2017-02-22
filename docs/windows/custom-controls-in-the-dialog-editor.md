---
title: "Custom Controls in the Dialog Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Custom Control"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controls [C++], templates"
  - "custom controls [Visual Studio], dialog boxes"
  - "custom controls [Visual Studio]"
  - "dialog box controls, custom (user) controls"
  - "Dialog editor, custom controls"
ms.assetid: f494b314-4000-4bbe-bbd0-4b18fb71ede1
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Custom Controls in the Dialog Editor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对话框编辑器使您可以在对话框模板中使用现有的“自定义”或“用户”控件。  
  
> [!NOTE]
>  这种意义上的自定义控件不能与 ActiveX 控件混淆。  ActiveX 控件有时称为 OLE 自定义控件。  此外，也不要将这些控件与 Windows 中的所有者描述控件混淆。  
  
 此功能旨在使您可以使用 Windows 所提供控件以外的控件。  在运行时，控件与窗口类（与 C\+\+ 类不同）关联。  完成该任务的一个更常用的方法是在对话框中安装任何控件，如静态控件。  然后，在运行时，在 [OnInitDialog](../Topic/CDialog::OnInitDialog.md) 函数中移除该控件并用自己的自定义控件替换它。  
  
 这是一个老方法。  现在，建议在大多数情况下编写 ActiveX 控件或创建 Windows 公共控件的子类。  
  
 对于这些自定义控件，仅限于：  
  
-   设置对话框中的位置。  
  
-   键入标题。  
  
-   标识控件的 Windows 类的名称（应用程序代码必须使用该名称注册控件）。  
  
-   键入设置控件样式的 32 位十六进制值。  
  
-   设置扩展样式。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 Win32  
  
## 请参阅  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [控件](../mfc/controls-mfc.md)