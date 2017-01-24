---
title: "“&lt;项目名&gt; 属性页”对话框 -&gt;“配置属性”-&gt;“清单工具”-&gt;“输入和输出” | Microsoft Docs"
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
  - "VC.Project.VCManifestTool.OutputManifestFile"
  - "VC.Project.VCManifestTool.InputResourceManifests"
  - "VC.Project.VCManifestTool.EmbedManifest"
  - "VC.Project.VCManifestTool.AdditionalManifestFiles"
  - "VC.Project.VCManifestTool.DependencyInformationFile"
  - "VC.Project.VCManifestTool.OutputResourceManifest"
  - "VC.Project.VCManifestTool.GenerateCatalogFiles"
dev_langs: 
  - "C++"
ms.assetid: a8bb20f6-7ace-45ca-bab0-b4f4a5caf170
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# “&lt;项目名&gt; 属性页”对话框 -&gt;“配置属性”-&gt;“清单工具”-&gt;“输入和输出”
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用此对话框可以指定 [Mt.exe](http://msdn.microsoft.com/library/aa375649) 的输入和输出选项。  
  
 若要访问此属性页对话框，请打开项目或属性表的属性页。  展开**“配置属性”**下的**“清单工具”**节点，然后选择**“输入和输出”**。  
  
## UIElement 列表  
 **附加清单文件**  
 使用 **\/manifest** 选项可以指定清单工具将处理或合并的附加清单文件的完整路径。  完整路径采用分号进行分隔。  
  
 **输入资源清单**  
 使用 **\/inputresource** 选项可以指定输入到清单工具中的 RT\_MANIFEST 类型的资源的完整路径。  该路径的后面可以是指定的资源 ID。  例如：  
  
 `dll_with_manifest.dll;#1`  
  
 资源 ID 是可选的，并且默认为 winuser.h 中的 CREATEPROCESS\_MANIFEST\_RESOURCE\_ID。  
  
 **嵌入清单**  
 **“是”**指定项目系统将应用程序清单文件嵌入到程序集中。  
  
 **“否”**指定项目系统将应用程序清单文件作为独立文件进行创建。  
  
 **输出清单文件**  
 指定输出清单文件的名称。  如果清单工具所操作的只有一个清单文件，则此属性是可选的。  
  
 **清单资源文件**  
 指定用于将清单嵌入到项目输出的输出资源文件。  
  
 **生成目录文件**  
 使用 **\/makecdfs** 选项可以指定清单工具将生成目录定义文件（.cdf 文件），这些文件用于制作目录。  
  
 **从 ManagedAssembly 生成清单**  
 从托管程序集生成清单。  \(**\-managedassemblyname:***文件*\)。  
  
 **禁止依赖项元素**  
 与 **\-managedassembly** 选项一起使用。  此标记取消在最终清单中生成依赖项元素。  
  
 **生成类别标记**  
 与 **\-managedassembly** 选项一起使用。  此标记可能导致生成类别标记。  
  
 **启用 DPI 识别**  
 指定应用程序是否支持 DPI。  默认情况下，如果是 MFC 项目，此设置为**“Yes”**，否则为**“No”**，因为仅 MFC 项目具有内置 DPI 识别。  如果添加代码以处理不同的 DPI 设置，您可以将设置重写为**“YES”**。  如果在应用程序不支持 DPI 时将其设置为支持 DPI，则该应用程序可能会出现模糊或变小。  
  
## 请参阅  
 [ClickOnce 应用程序清单](../Topic/ClickOnce%20Application%20Manifest.md)   
 [清单工具属性页](../ide/manifest-tool-property-pages.md)   
 [如何：打开项目属性页](../misc/how-to-open-project-property-pages.md)   
 [如何：编辑项目属性表](../misc/how-to-edit-project-property-sheets.md)