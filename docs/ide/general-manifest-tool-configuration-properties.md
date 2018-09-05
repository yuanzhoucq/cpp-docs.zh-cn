---
title: 清单工具配置属性 (Visual C++) | Microsoft Docs
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
ms.openlocfilehash: ef1eb1c0c1ee8c9fb2814bc7cd808ea2e524b8a4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200328"
---
# <a name="general-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>“&lt;项目名&gt; 属性页”对话框 ->“配置属性”->“清单工具”->“常规”
使用此对话框指定 [Mt.exe](https://msdn.microsoft.com/library/aa375649) 的常规选项。  
  
 若要访问此属性页对话框，请打开项目或属性表的属性页。 展开“配置属性”下的“清单工具节点”，然后选择“常规”。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **取消显示启动版权标志**  
 如果为“是(/nologo)”，则指定在启动清单工具时隐藏标准 Microsoft 版权所有数据。 将 mt.exe 作为生成过程的一部分运行或从生成环境运行 mt.exe 时，使用此选项取消显示日志文件中不需要的输出。  
  
 **详细输出**  
 如果为“是(/verbose)”，则指定在清单生成期间显示其他生成信息。  
  
 **程序集标识**  
 使用 /identity 选项指定标识字符串，该字符串包含 [\<assemblyIdentity> 元素](/visualstudio/deployment/assemblyidentity-element-clickonce-application)的特性。 标识字符串以 `name` 特性的值开头，后面跟特性 = 值对。 标识字符串中的特性以逗号隔开。  
  
 以下是一个示例标识字符串：  
  
 `Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`  
  
## <a name="see-also"></a>请参阅  
 [ClickOnce 应用程序清单](/visualstudio/deployment/clickonce-application-manifest)   
 [清单工具属性页](../ide/manifest-tool-property-pages.md)   
 [使用项目属性](../ide/working-with-project-properties.md)   