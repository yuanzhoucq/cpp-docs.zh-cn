---
title: 高级，清单工具，配置属性&lt;Projectname&gt;属性页对话框 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManifestTool.KeyFile
- VC.Project.VCManifestTool.UpdateFileHashes
- VC.Project.VCManifestTool.UpdateFileHashesSearchPath
- VC.Project.VCManifestTool.ValidateSignature
- VC.Project.VCManifestTool.KeyContainer
dev_langs:
- C++
ms.assetid: 3d587366-05ea-4956-a978-313069660735
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 47d4dc3ab325a7346d0e787a15d69d646896827d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="advanced-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>高级，清单工具，配置属性&lt;Projectname&gt;属性页对话框
此对话框用于为指定高级的选项[Mt.exe](http://msdn.microsoft.com/library/aa375649)。  
  
 若要访问此属性页对话框中，打开你的项目或属性表的属性页。 展开**清单工具**节点下的**配置属性**，然后选择**高级**。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **更新文件哈希值**  
 使用 /hashupdate 选项来指定该清单工具将计算中指定的文件哈希`<file>`元素，然后更新哈希特性具有计算值。  
  
 **更新文件哈希搜索路径**  
 指定文件中引用的搜索路径`<file>`元素。 此选项还使用 /hashupdate 选项。  
  
## <a name="see-also"></a>请参阅  
 [\<文件 > 元素](/visualstudio/deployment/file-element-clickonce-application)   
 [ClickOnce 应用程序清单](/visualstudio/deployment/clickonce-application-manifest)   
 [清单工具属性页](../ide/manifest-tool-property-pages.md)   
 [使用项目属性](../ide/working-with-project-properties.md)   