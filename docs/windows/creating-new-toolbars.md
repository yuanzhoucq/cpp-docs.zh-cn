---
title: "Creating New Toolbars | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.toolbar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "toolbars [C++], creating"
  - "Toolbar editor, creating new toolbars"
  - "Insert Resource"
ms.assetid: 1b28264b-0718-4df8-9f65-979805d2efef
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Creating New Toolbars
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 创建新工具栏  
  
1.  在**资源**视图中，右击 .rc 文件，然后从快捷菜单中选择**“添加资源”**。  （如果 .rc 文件中有一个现有工具栏，则右击“工具栏”文件夹，并从快捷菜单中选择“插入 Toolbar”即可。）  
  
     **注意** 如果您的项目尚未包含 .rc 文件，请参见[创建新资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在**“添加资源”**对话框中，选择**“资源类型”**列表中的**“Toolbar”**，然后单击**“新建”**。  
  
     如果“Toolbar”资源类型旁边出现加号 \(\+\)，它表示工具栏模板可用。  单击加号展开模板列表，选择一个模板，然后单击**“新建”**。  
  
     \- 或 \-  
  
3.  [将现有位图转换为工具栏](../mfc/converting-bitmaps-to-toolbars.md)。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 MFC 或 ATL  
  
## 请参阅  
 [Toolbar Editor](../mfc/toolbar-editor.md)