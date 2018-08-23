---
title: “受管理资源”属性页 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManagedResourceCompilerTool.ResourceFileName
- VC.Project.VCManagedResourceCompilerTool.OutputFileName
- VC.Project.VCManagedResourceCompilerTool.DefaultLocalizedResources
dev_langs:
- C++
helpviewer_keywords:
- Managed Resources property page
ms.assetid: 80b80384-ee55-494d-9f0e-907bb98cfc19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2922a0a92a121d6838478daaf2c32f1c7a630d21
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340354"
---
# <a name="managed-resources-property-page"></a>“托管资源”属性页
启用资源编译器的设置。  
  
 “受管理资源”属性页包含下列属性：  
  
 **资源逻辑名称**  
 指定生成的中间 .resources 文件的逻辑名称。 逻辑名称是用于加载资源的名称。 如果未指定逻辑名称，则使用资源 (.resx) 文件名作为逻辑名称。  
  
 **输出文件名**  
 指定此资源 (.resx) 文件构成的最终输出文件的名称。  
  
 **默认本地化资源**  
 指定给定的 .resx 文件是构成默认资源还是附属 .dll。  
  
 有关如何访问“受管理资源”属性页的信息，请参阅[使用项目属性](../ide/working-with-project-properties.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用 RC（RC 命令行）](http://msdn.microsoft.com/library/windows/desktop/aa381055)   
 [属性页](../ide/property-pages-visual-cpp.md)   
 [/ASSEMBLYRESOURCE（嵌入托管资源）](../build/reference/assemblyresource-embed-a-managed-resource.md)