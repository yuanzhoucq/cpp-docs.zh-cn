---
title: "清单工具配置属性 （Visual c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCManifestTool.MergeRulesFile
- VC.Project.VCManifestTool.UseUnicodeResponseFiles
- VC.Project.VCManifestTool.SuppressStartupBanner
- VC.Project.VCManifestTool.UseFAT32Workaround
- VC.Project.VCManifestTool.VerboseOutput
- VC.Project.VCManifestTool.AssemblyIdentity
dev_langs: C++
ms.assetid: b99368a5-6819-482c-a06e-f2409290cfd1
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0e5e56c823a7a30850e24e393a545f0df6a6637a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="general-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>常规、 清单工具，配置属性&lt;Projectname&gt;属性页对话框
使用此对话框中指定的常规选项[Mt.exe](http://msdn.microsoft.com/library/aa375649)。  
  
 若要访问此属性页对话框中，打开你的项目或属性表的属性页。 展开**清单工具**节点下的**配置属性**，然后选择**常规**。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **取消显示启动版权标志**  
 **是 (/ nologo)**指定启动清单工具时，将隐藏标准 Microsoft 版权数据。 使用此选项时作为生成过程中或从生成环境的一部分运行 mt.exe 抑制不需要的输出日志文件中。  
  
 **详细输出**  
 **是 （/ 详细）**指定清单生成过程中，将显示其他生成信息。  
  
 **程序集标识**  
 使用 /identity 选项来指定一个标识字符串，其包含的属性[ \<assemblyIdentity > 元素](/visualstudio/deployment/assemblyidentity-element-clickonce-application)。 标识字符串开头的值`name`特性，并后跟*属性* = *值*对。 用逗号分隔的标识字符串中的属性。  
  
 下面是一个示例标识字符串：  
  
 `Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`  
  
## <a name="see-also"></a>请参阅  
 [ClickOnce 应用程序清单](/visualstudio/deployment/clickonce-application-manifest)   
 [清单工具属性页](../ide/manifest-tool-property-pages.md)   
 [使用项目属性](../ide/working-with-project-properties.md)   