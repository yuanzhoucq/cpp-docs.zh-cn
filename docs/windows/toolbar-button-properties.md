---
title: "Toolbar Button Properties | Microsoft Docs"
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
  - "size, toolbar buttons"
  - "toolbar buttons (in Toolbar editor), setting properties"
  - "Toolbar editor, toolbar button properties"
  - "status bars, active toolbar button text"
  - "command IDs, toolbar buttons"
  - "width, toolbar buttons"
ms.assetid: b2705814-7c5d-4f24-8f77-07559b0cdda2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Toolbar Button Properties
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

工具栏按钮的属性包括：  
  
|属性|说明|  
|--------|--------|  
|**ID**|定义按钮的 ID。  下拉列表提供通用 **ID** 名。|  
|**宽度**|设置按钮的宽度。  推荐使用 16 像素。|  
|**高度**|设置按钮的高度。  注意，一个按钮的高度更改工具栏上所有按钮的高度。  推荐使用 15 像素。|  
|**提示**|定义状态栏中显示的消息。  添加 \\n 和名称将会向工具栏按钮添加工具提示。  有关更多信息，请参见[创建工具提示](../mfc/creating-a-tool-tip-for-a-toolbar-button.md)。|  
  
 **“宽度”**和**“高度”**应用于所有按钮。  用于创建工具栏的位图的最大宽度为 2048。  因此，如果按钮宽度设置为 512，则只能有四个按钮，如果按钮宽度设置为 513，则只能有三个按钮。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 MFC 或 ATL  
  
## 请参阅  
 [Changing the Properties of a Toolbar Button](../mfc/changing-the-properties-of-a-toolbar-button.md)   
 [Toolbar Editor](../mfc/toolbar-editor.md)