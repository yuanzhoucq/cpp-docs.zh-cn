---
title: "“&lt;项目名&gt; 属性页”对话框 -&gt;“配置属性”-&gt;“清单工具”-&gt;“常规” | Microsoft Docs"
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
  - "VC.Project.VCManifestTool.MergeRulesFile"
  - "VC.Project.VCManifestTool.UseUnicodeResponseFiles"
  - "VC.Project.VCManifestTool.SuppressStartupBanner"
  - "VC.Project.VCManifestTool.UseFAT32Workaround"
  - "VC.Project.VCManifestTool.VerboseOutput"
  - "VC.Project.VCManifestTool.AssemblyIdentity"
dev_langs: 
  - "C++"
ms.assetid: b99368a5-6819-482c-a06e-f2409290cfd1
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# “&lt;项目名&gt; 属性页”对话框 -&gt;“配置属性”-&gt;“清单工具”-&gt;“常规”
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用此对话框可指定 [Mt.exe](http://msdn.microsoft.com/library/aa375649) 的常规选项。  
  
 若要访问此属性页对话框，请打开项目或属性表的属性页。  展开**“配置属性”**下的**“清单工具”**节点，然后选择**“常规”**。  
  
## UIElement 列表  
 **取消显示启动版权标志**  
 **“是\(\/nologo\)”**指定启动清单工具时将隐藏标准的 Microsoft 版权数据。  将 mt.exe 作为生成过程的一部分运行或在生成环境中运行时，可以使用此选项取消日志文件中不需要的输出。  
  
 **详细输出**  
 **“是\(\/verbose\)”**指定在清单生成期间将显示附加生成信息。  
  
 **程序集标识**  
 可以使用 \/identity 选项指定标识字符串，该字符串包含 [\<assemblyIdentity\> 元素](../Topic/%3CassemblyIdentity%3E%20Element%20\(ClickOnce%20Application\).md) 的各个特性。  标识字符串以 `name` 特性的值开头，后面是“*特性* \= *值*”对。  标识字符串中的特性采用逗号进行分隔。  
  
 下面是标识字符串的一个示例：  
  
 `Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`  
  
## 请参阅  
 [ClickOnce 应用程序清单](../Topic/ClickOnce%20Application%20Manifest.md)   
 [清单工具属性页](../ide/manifest-tool-property-pages.md)   
 [如何：打开项目属性页](../misc/how-to-open-project-property-pages.md)   
 [如何：编辑项目属性表](../misc/how-to-edit-project-property-sheets.md)