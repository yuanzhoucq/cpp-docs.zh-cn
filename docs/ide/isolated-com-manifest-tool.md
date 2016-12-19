---
title: "“&lt;项目名&gt; 属性页”对话框 -&gt;“配置属性”-&gt;“清单工具”-&gt;“独立 COM” | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCManifestTool.RegistrarScriptFile"
  - "VC.Project.VCManifestTool.ComponentFileName"
  - "VC.Project.VCManifestTool.TypeLibraryFile"
  - "VC.Project.VCManifestTool.ReplacementsFile"
dev_langs: 
  - "C++"
ms.assetid: 457582b8-cfde-49c0-92e3-3a6b9e8c08eb
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# “&lt;项目名&gt; 属性页”对话框 -&gt;“配置属性”-&gt;“清单工具”-&gt;“独立 COM”
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用此对话框可以指定 [Mt.exe](http://msdn.microsoft.com/library/aa375649) 的**“独立 COM”**选项。  
  
 若要访问此属性页对话框，请打开项目或属性表的属性页。  展开**“通用属性”**下的**“清单工具”**节点，然后选择**“独立 COM”**。  
  
## 任务列表  
  
-   [如何：生成独立应用程序以使用 COM 组件](../build/how-to-build-isolated-applications-to-consume-com-components.md)  
  
## UIElement 列表  
 **类型库文件**  
 使用 \/tlb 选项指定类型库文件（.tlb 文件）的名称，清单工具将使用该文件生成清单文件。  
  
 **注册器脚本文件**  
 使用 \/rgs 选项指定注册器脚本文件（.rgs 文件）的名称，清单工具将使用该文件生成清单文件。  
  
 **组件文件名**  
 使用 \/dll 选项指定清单工具将生成的资源名称。  如果指定了**“类型库文件”**或**“注册器脚本文件”**的值，则必须为此属性输入值。  
  
 **替换文件**  
 使用 \/replacements 选项指定包含 rgs 文件中可替换字符串值的文件的完整路径。  
  
## 请参阅  
 [独立应用程序](http://msdn.microsoft.com/library/aa375190)   
 [并行程序集](_win32_side_by_side_assemblies)   
 [ClickOnce 应用程序清单](../Topic/ClickOnce%20Application%20Manifest.md)   
 [清单工具属性页](../ide/manifest-tool-property-pages.md)   
 [如何：打开项目属性页](../misc/how-to-open-project-property-pages.md)   
 [如何：编辑项目属性表](../misc/how-to-edit-project-property-sheets.md)