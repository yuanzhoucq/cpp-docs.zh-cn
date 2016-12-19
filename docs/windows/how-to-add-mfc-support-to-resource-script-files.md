---
title: "How to: Add MFC Support to Resource Script Files | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.resvw.add.MFC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rc files, adding MFC support"
  - ".rc files, adding MFC support"
  - "MFC, adding support to resource scripts files"
  - "resource script files, adding MFC support"
ms.assetid: 599dfe9d-ad26-4e34-899c-49b56599e37f
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Add MFC Support to Resource Script Files
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通常情况下，当使用 [MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)针对 Windows 生成 MFC 应用程序时，该向导会生成一组基本文件（包括资源脚本 \(.rc\) 文件），这些文件包含 Microsoft 基础类 \(MFC\) 的核心功能。  但是，如果在为不基于 MFC 的 Windows 应用程序编辑 .rc 文件，则无法使用以下特定于 MFC 框架的功能：  
  
-   MFC 代码向导（以前称为“[MFC ClassWizard](http://msdn.microsoft.com/zh-cn/98dc2434-ba93-4e0b-b084-1a4bc26cdf1e)”）  
  
-   菜单提示字符串  
  
-   组合框控件的列表内容  
  
-   ActiveX 控件承载  
  
 但是，可以向没有 MFC 支持的现有 .rc 文件添加这种支持。  
  
### 向 .rc 文件添加 MFC 支持  
  
1.  打开资源脚本文件。  
  
    > [!NOTE]
    >  如果你的项目尚未包含 .rc 文件，请参阅[创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在[“资源视图”](../windows/resource-view-window.md)中，突出显示资源文件夹（例如，MFC.rc）。  
  
3.  在[“属性”窗口](../Topic/Properties%20Window.md)中，将**“MFC Mode”**属性设置为**“True”**。  
  
    > [!NOTE]
    >  除了设置此标志之后，.rc 文件还必须是 MFC 项目的一部分。  例如，仅仅在 Win32 项目中的 .rc 文件上将**“MFC Mode”**设置为**“True”**不会为你提供任何 MFC 功能。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。 有关手动将资源文件添加到托管项目、访问资源、显示静态资源以及将资源字符串分配给属性的信息，请参阅[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **要求**  
  
 MFC  
  
## 请参阅  
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)