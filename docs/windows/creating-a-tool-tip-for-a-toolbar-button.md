---
title: "Creating a Tool Tip for a Toolbar Button | Microsoft Docs"
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
  - "tool tips [C++], adding to toolbar buttons"
  - "\n in tool tip"
  - "toolbar buttons [C++], tool tips"
  - "buttons [C++], tool tips"
  - "Toolbar editor, creating tool tips"
ms.assetid: 0af65342-fd78-4e78-8d0d-dc68f7fc462e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Creating a Tool Tip for a Toolbar Button
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 创建工具提示  
  
1.  选择工具栏按钮。  
  
2.  在[“属性”窗口](../Topic/Properties%20Window.md)的“提示”属性字段中，为状态栏添加按钮说明；在该消息后添加 \\n 和工具提示名。  
  
 工具提示的常见示例是“写字板”中的“打印”按钮：  
  
 1.  打开“写字板”。  
  
 2.  将鼠标指针悬停在**“打印”**工具栏按钮上方。  
  
 3.  注意，现在单词“打印”将浮动在鼠标指针下方。  
  
 4.  查看状态栏（在“写字板”窗口的正底部），请注意，现在它显示文本“打印活动文档”。  
  
 步骤 3 中的“打印”是“工具提示名”，步骤 4 中的“打印活动文档”是“状态栏中的按钮说明”。  
  
 如果希望使用工具栏编辑器获得此效果，请将“提示”属性设置为“打印活动文档\\n打印”。  
  
> [!NOTE]
>  可以使用[“属性”窗口](../Topic/Properties%20Window.md)编辑提示文本。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 MFC 或 ATL  
  
## 请参阅  
 [Creating, Moving, and Editing Toolbar Buttons](../mfc/creating-moving-and-editing-toolbar-buttons.md)   
 [Toolbar Editor](../mfc/toolbar-editor.md)