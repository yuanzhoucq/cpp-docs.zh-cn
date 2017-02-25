---
title: "“托管资源”属性页 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCManagedResourceCompilerTool.ResourceFileName"
  - "VC.Project.VCManagedResourceCompilerTool.OutputFileName"
  - "VC.Project.VCManagedResourceCompilerTool.DefaultLocalizedResources"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "“托管资源”属性页"
ms.assetid: 80b80384-ee55-494d-9f0e-907bb98cfc19
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# “托管资源”属性页
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

启用资源编译器的设置。  
  
 **托管资源** 属性页包含以下属性：  
  
 **资源逻辑名**  
 指定生成的中间 .resources 文件的逻辑名称。  逻辑名称是用于加载资源的名称。  如果未指定逻辑名称；则将资源 \(.resx\) 文件名用作逻辑名称。  
  
 **输出文件名**  
 指定资源 \(.resx\) 文件有用的最终输出文件的名称。  
  
 **默认本地化资源**  
 指定给定的 .resx 文件是分配到默认资源还是分配到附属 .dll。  
  
 有关访问 **托管资源** 属性页的信息，请参见 [如何：用属性页指定项目属性](../misc/how-to-specify-project-properties-with-property-pages.md)"。  
  
## 请参阅  
 [Using RC \(The RC Command Line\)](http://msdn.microsoft.com/library/windows/desktop/aa381055)   
 [属性页](../ide/property-pages-visual-cpp.md)   
 [\/ASSEMBLYRESOURCE（嵌入托管资源）](../build/reference/assemblyresource-embed-a-managed-resource.md)