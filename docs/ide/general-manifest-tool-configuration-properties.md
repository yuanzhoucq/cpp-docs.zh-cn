---
title: 清单工具配置属性 （Visual c + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManifestTool.MergeRulesFile
- VC.Project.VCManifestTool.UseUnicodeResponseFiles
- VC.Project.VCManifestTool.SuppressStartupBanner
- VC.Project.VCManifestTool.UseFAT32Workaround
- VC.Project.VCManifestTool.VerboseOutput
- VC.Project.VCManifestTool.AssemblyIdentity
dev_langs:
- C++
ms.assetid: b99368a5-6819-482c-a06e-f2409290cfd1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1953e7c37c07f66845510efe037015a537aa7baa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="general-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>常规、 清单工具，配置属性&lt;Projectname&gt;属性页对话框
使用此对话框中指定的常规选项[Mt.exe](http://msdn.microsoft.com/library/aa375649)。  
  
 若要访问此属性页对话框中，打开你的项目或属性表的属性页。 展开**清单工具**节点下的**配置属性**，然后选择**常规**。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **取消显示启动版权标志**  
 **是 (/ nologo)** 指定启动清单工具时，将隐藏标准 Microsoft 版权数据。 使用此选项时作为生成过程中或从生成环境的一部分运行 mt.exe 抑制不需要的输出日志文件中。  
  
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