---
title: "Previewing Resources | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.resvw.resource.previewing"
  - "vs.resvw.resource.previewing"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resources [Visual Studio], viewing"
  - "resource previews"
  - "code, viewing"
ms.assetid: d6abda66-0e2b-4ac3-a59a-a57b8c6fb70b
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Previewing Resources
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

预览资源允许在不打开图形资源的情况下查看它们。  预览对编译完的可执行文件也有用，因为资源标识符已改成数字。  由于这些数字标识符通常不提供足够的信息，因此预览资源有助于快速识别它们。  
  
 可以预览下列资源类型的可视化布局：  
  
-   位图  
  
-   对话框  
  
-   图标  
  
-   Menu  
  
-   光标  
  
-   工具栏  
  
 可视预览功能不适用于“快捷键”、“清单”、“字符串表”和“版本信息”资源。  
  
### 预览资源  
  
1.  在[资源视图](../windows/resource-view-window.md)或文档窗口中，选择资源（如 IDD\_ABOUTBOX）。  
  
     **注意** 如果您的项目尚未包含 .rc 文件，请参见[创建新资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在[“属性”窗口](../Topic/Properties%20Window.md)中单击**“属性页”**按钮。  
  
     \- 或 \-  
  
3.  在**“视图”**菜单上，单击**“属性页”**。  
  
     资源的“属性页”打开，显示该资源的预览。  然后可以使用上、下箭头键在“资源视图”或文档窗口中浏览树控件。  “属性页”将保持打开并显示具有焦点且可以预览的任何资源。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **要求**  
  
 Win32  
  
## 请参阅  
 [How to: Open a Resource Script File Outside of a Project \(Standalone\)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)   
 [Resource Editors](../mfc/resource-editors.md)