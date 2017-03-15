---
title: "How to: Import and Export Resources | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.resvw.resource.importing"
  - "vc.resvw.resource.importing"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resources [Visual Studio], exporting"
  - "graphics [C++], exporting"
  - "graphics [C++], importing"
  - "resources [Visual Studio], importing"
  - "bitmaps [C++], importing and exporting"
  - "toolbars [C++], importing"
  - "images [C++], importing"
  - "toolbars [C++], exporting"
  - "cursors [C++], importing and exporting"
  - "images [C++], exporting"
ms.assetid: 3c9329dc-dcb8-4edd-a600-78e3e572bd89
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# How to: Import and Export Resources
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以导入图形资源（位图、图标、光标和工具栏）、HTML 文件和自定义资源以便在 Visual C\+\+ 中使用。  可以从 Visual C\+\+ 项目导出相同类型的文件以分隔可以在开发环境外部使用的文件。  
  
> [!NOTE]
>  无法导入或导出资源类型（如加速器、对话框和字符串表），因为它们不是独立的文件类型。  
  
### 将一个单独的资源导入到当前资源文件中  
  
1.  在[资源视图](../windows/resource-view-window.md)中，右键单击要向其添加资源的资源脚本 \(\*.rc\) 文件的对应节点。  
  
2.  在快捷菜单上，单击**“导入”**。  
  
3.  找到并选择位图 \(.bmp\)、图标 \(.ico\)、光标 \(.cur\)、Html 文件 \(.htm\) 或要导入的其他文件的文件名。  
  
4.  单击**“确定”**以将资源添加到在**“资源”**视图中选择的文件。  
  
    > [!NOTE]
    >  无论选择哪种特定资源类型，导入过程的工作方式都是相同的。  导入的资源会自动添加到该资源类型的正确节点。  
  
### 导出位图、图标或光标作为单独的文件（以便在 Visual C\+\+ 外部使用）  
  
1.  在**“资源”**视图中，右键单击要导出的资源。  
  
2.  在快捷菜单上，单击**“导出”**。  
  
3.  在**“导出资源”**对话框中，接受当前文件名或输入新文件名。  
  
4.  导航到要用于保存文件的文件夹，然后单击**“导出”**。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。 有关手动将资源文件添加到托管项目、访问资源、显示静态资源以及将资源字符串分配给属性的信息，请参阅[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 Win32  
  
## 请参阅  
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)