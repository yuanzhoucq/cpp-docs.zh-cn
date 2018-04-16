---
title: "管理资源属性页 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCManagedResourceCompilerTool.ResourceFileName
- VC.Project.VCManagedResourceCompilerTool.OutputFileName
- VC.Project.VCManagedResourceCompilerTool.DefaultLocalizedResources
dev_langs:
- C++
helpviewer_keywords:
- Managed Resources property page
ms.assetid: 80b80384-ee55-494d-9f0e-907bb98cfc19
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b8683c9212a25a5b278405c2d2c31d7fc607d0f5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="managed-resources-property-page"></a>“托管资源”属性页
启用资源编译器的设置。  
  
 **被管理的资源**属性页包含以下属性：  
  
 **资源的逻辑名称**  
 指定*逻辑名称*的生成的中间.resources 文件。 逻辑名称是用来加载资源的名称。 如果未不指定任何逻辑名称，则资源 (.resx) 文件名称用作的逻辑名称。  
  
 **输出文件名**  
 指定的资源 (.resx) 文件分配给最终输出文件的名称。  
  
 **默认的本地化的资源**  
 指定给定的.resx 文件分配到默认资源或附属程序集.dll。  
  
 有关如何访问信息**被管理的资源**属性页中，请参阅[使用项目属性](../ide/working-with-project-properties.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用 RC （RC 命令行）](http://msdn.microsoft.com/library/windows/desktop/aa381055)   
 [属性页](../ide/property-pages-visual-cpp.md)   
 [/ASSEMBLYRESOURCE （嵌入托管的资源）](../build/reference/assemblyresource-embed-a-managed-resource.md)