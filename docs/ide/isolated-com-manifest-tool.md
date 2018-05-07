---
title: 清单工具隔离 COM 属性 （Visual c + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.ReplacementsFile
dev_langs:
- C++
ms.assetid: 457582b8-cfde-49c0-92e3-3a6b9e8c08eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c425a71f8bb8a7972ade29fb0d18cf3eab7debb5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="isolated-com-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>隔离配置属性 COM 清单工具， &lt;Projectname&gt;属性页对话框
使用此对话框中指定**独立 COM**选项[Mt.exe](http://msdn.microsoft.com/library/aa375649)。  
  
 若要访问此属性页对话框中，打开你的项目或属性表的属性页。 展开**清单工具**节点下的**通用属性**，然后选择**独立 COM**。  
  
## <a name="task-list"></a>任务列表  
  
-   [如何：生成独立应用程序以使用 COM 组件](../build/how-to-build-isolated-applications-to-consume-com-components.md)  
  
## <a name="uielement-list"></a>UIElement 列表  
 **类型库文件**  
 使用 /tlb 选项来指定该清单工具将用于生成清单文件的类型库文件 （.tlb 文件） 的名称。  
  
 **注册器脚本文件**  
 使用 /rgs 选项来指定该清单工具将用于生成清单文件注册器脚本文件 (.rgs file) 的名称。  
  
 **组件文件名称**  
 使用了 /dll 选项来指定该清单工具将生成资源的名称。 必须为此属性输入一个值时为值**类型库文件**或**注册器脚本文件**指定。  
  
 **替换文件**  
 使用 /replacements 选项来指定包含.rgs 文件中的可替换字符串的值的文件的完整路径。  
  
## <a name="see-also"></a>请参阅  
 [独立应用程序](http://msdn.microsoft.com/library/aa375190)   
 [ClickOnce 应用程序清单](/visualstudio/deployment/clickonce-application-manifest)   
 [清单工具属性页](../ide/manifest-tool-property-pages.md)   
 [使用项目属性](../ide/working-with-project-properties.md)   