---
title: 清单工具输入和输出属性 （Visual c + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManifestTool.OutputManifestFile
- VC.Project.VCManifestTool.InputResourceManifests
- VC.Project.VCManifestTool.EmbedManifest
- VC.Project.VCManifestTool.AdditionalManifestFiles
- VC.Project.VCManifestTool.DependencyInformationFile
- VC.Project.VCManifestTool.OutputResourceManifest
- VC.Project.VCManifestTool.GenerateCatalogFiles
dev_langs:
- C++
ms.assetid: a8bb20f6-7ace-45ca-bab0-b4f4a5caf170
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 15be7636188bb670febd7875974d683c1d78360f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="input-and-output-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>输入和输出，清单工具，配置属性&lt;Projectname&gt;属性页对话框
使用此对话框中指定的输入和输出选项[Mt.exe](http://msdn.microsoft.com/library/aa375649)。  
  
 若要访问此属性页对话框中，打开你的项目或属性表的属性页。 展开**清单工具**节点下的**配置属性**，然后选择**输入和输出**。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **其他清单文件**  
 使用 **/清单**选项以指定的清单工具将处理的其他清单文件或合并的完整路径。 完整路径由分号分隔。  
  
 **输入的资源清单**  
 使用 **/inputresource**选项以指定类型 RT_MANIFEST，其输入到该清单工具的资源的完整路径。 可以通过指定的资源 ID 遵循的路径 例如：  
  
 `dll_with_manifest.dll;#1`  
  
 资源 ID 是可选的默认为 CREATEPROCESS_MANIFEST_RESOURCE_ID 中参见 winuser.h。  
  
 **嵌入清单**  
 **是**指定项目系统将嵌入到程序集的应用程序清单文件。  
  
 **不**指定项目系统将创建应用程序清单文件作为独立的文件。  
  
 **输出清单文件**  
 指定输出清单文件的名称。 只有一个清单文件所操作的清单工具时，此属性是可选的。  
  
 **清单资源文件**  
 指定资源文件用于将清单嵌入到项目输出的输出。  
  
 **生成目录文件**  
 使用 **/makecdfs**选项以指定该清单工具将生成目录定义文件 （.cdf 文件），用于使目录。  
  
 **从 ManagedAssembly 生成清单**  
 从托管程序集生成清单。 (**-managedassemblyname: * * * 文件*)。  
  
 **禁止显示依赖关系元素**  
 与使用 **-managedassembly**选项。 此标记取消生成最终的清单中的依赖关系元素。  
  
 **生成类别标记**  
 与使用 **-managedassembly**选项。 此标记会导致类别标记来生成。  
  
 **启用 DPI 感知**  
 指定是否 DPI 感知应用程序。 默认情况下，设置是**是**对于 MFC 项目和**否**否则为因为 DPI 感知内置了只有 MFC 项目。 你可以重写将设置改为**是**如果添加代码来处理采用不同 DPI 设置。 模糊或如果你将其设置为 dpi 时它不是小型，可能会出现你的应用程序。  
  
## <a name="see-also"></a>请参阅  
 [ClickOnce 应用程序清单](/visualstudio/deployment/clickonce-application-manifest)   
 [清单工具属性页](../ide/manifest-tool-property-pages.md)   
 [使用项目属性](../ide/working-with-project-properties.md)   