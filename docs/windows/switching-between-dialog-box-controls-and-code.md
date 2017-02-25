---
title: "Switching Between Dialog Box Controls and Code | Microsoft Docs"
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
  - "events [C++], viewing for controls"
  - "Windows messages [C++], controls"
  - "messages [C++], viewing for dialog boxes"
  - "Dialog editor, accessing code"
  - "code [C++], switching from Dialog Editor"
  - "controls [C++], jumping to code"
  - "Dialog editor, switching between controls and code"
ms.assetid: 7da73815-b853-4203-ba45-bbe570695122
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Switching Between Dialog Box Controls and Code
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 MFC 应用程序中，可以双击对话框控件跳转到它们的处理程序代码或快速创建存根 \(stub\) 处理函数。  
  
 选定控件后，单击[“属性”窗口](../Topic/Properties%20Window.md)中的“控件事件”按钮或“消息”按钮查看可用于选定项的 Windows 消息和事件的完整列表。  从列表中选择以创建或编辑处理函数。  
  
### 从对话框编辑器跳转到代码  
  
1.  双击对话框中的控件以跳转到其最新实现的消息处理函数的声明。  （对于基于 ATL 的对话框类，总是跳转到构造函数定义。）  
  
### 查看控件的事件  
  
1.  选定控件后，单击[“属性”窗口](../Topic/Properties%20Window.md)中的“控件事件”按钮。  
  
    > [!NOTE]
    >  当对话框具有焦点时，单击**“控件事件”**按钮将公开对话框中所有控件的列表，然后可以展开该列表以编辑个别控件的事件。  
  
     当对话框中的单个控件具有焦点时，可右击该控件并从快捷菜单中选择**“添加事件处理程序”**。  这使您能够指定将处理程序添加到的类。  有关更多信息，请参见[添加事件处理程序](../ide/adding-an-event-handler-visual-cpp.md)。  
  
### 查看对话框的消息  
  
1.  选定对话框后，单击[“属性”窗口](../Topic/Properties%20Window.md)中的“消息”按钮。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 Win32  
  
## 请参阅  
 [Dialog Editor](../mfc/dialog-editor.md)