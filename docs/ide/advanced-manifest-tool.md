---
title: "“&lt;项目名&gt; 属性页”对话框 -&gt;“配置属性”-&gt;“清单工具”-&gt;“高级” | Microsoft Docs"
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
  - "VC.Project.VCManifestTool.KeyFile"
  - "VC.Project.VCManifestTool.UpdateFileHashes"
  - "VC.Project.VCManifestTool.UpdateFileHashesSearchPath"
  - "VC.Project.VCManifestTool.ValidateSignature"
  - "VC.Project.VCManifestTool.KeyContainer"
dev_langs: 
  - "C++"
ms.assetid: 3d587366-05ea-4956-a978-313069660735
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# “&lt;项目名&gt; 属性页”对话框 -&gt;“配置属性”-&gt;“清单工具”-&gt;“高级”
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用此对话框可指定 [Mt.exe](http://msdn.microsoft.com/library/aa375649) 的高级选项。  
  
 若要访问此属性页对话框，请打开项目或属性表的属性页。  展开**“配置属性”**下的**“清单工具”**节点，然后选择**“高级”**。  
  
## UIElement 列表  
 **更新文件哈希**  
 使用 \/hashupdate 选项指定清单工具将计算在 `<file>` 元素中指定的文件哈希，然后使用计算的值更新哈希特性。  
  
 **更新文件哈希搜索路径**  
 指定在 `<file>` 元素中引用的文件的搜索路径。  此选项也使用 \/hashupdate 选项  
  
## 请参阅  
 [\<file\> 元素](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md)   
 [ClickOnce 应用程序清单](../Topic/ClickOnce%20Application%20Manifest.md)   
 [清单工具属性页](../ide/manifest-tool-property-pages.md)   
 [如何：打开项目属性页](../misc/how-to-open-project-property-pages.md)   
 [如何：编辑项目属性表](../misc/how-to-edit-project-property-sheets.md)