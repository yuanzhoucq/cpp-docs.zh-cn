---
title: "XML 文档生成器工具属性页 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCXDCMakeTool.ValidateIntelliSense
- VC.Project.VCXDCMakeTool.SuppressStartupBanner
- VC.Project.VCXDCMakeTool.DocumentLibraryDependencies
- VC.Project.VCXDCMakeTool.OutputDocumentFile
- VC.Project.VCXDCMakeTool.AdditionalDocumentFiles
dev_langs:
- C++
ms.assetid: 645912b5-197a-4c36-ba58-64df09444ca0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bc09dafc0f07bc16a11dd255419440b6464456c5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="xml-document-generator-tool-property-pages"></a>“XML 文档生成器工具”属性页
XML 文档生成器工具属性页公开 xdcmake.exe 的功能。 xdcmake.exe.xdc 会文件合并到一个.xml 文件时你的源代码包含文档注释和[/doc （处理文档注释） （C/c + +）](../build/reference/doc-process-documentation-comments-c-cpp.md)指定，则。 请参阅[建议的文档注释标记](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)有关将文档注释添加到源代码的信息。  
  
> [!NOTE]
>  在命令行使用 xdcmake.exe 时，在开发环境 （属性页） 中的 xdcmake.exe 选项将有所不同选项。 在命令行使用 xdcmake.exe 的信息，请参阅[XDCMake 参考](../ide/xdcmake-reference.md)。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **取消显示启动版权标志**  
 禁止显示版权消息。  
  
 **其他文档文件**  
 你希望项目系统以查找.xdc 文件的其他目录。 xdcmake 始终将查找由项目生成的.xdc 文件。 可以指定多个目录。  
  
 **输出文档文件**  
 .Xml 输出文件的名称和目录位置。 请参阅[用于生成命令和属性的公共宏](../ide/common-macros-for-build-commands-and-properties.md)有关使用宏来指定目录位置信息。  
  
 **文档库依赖项**  
 如果你的项目在解决方案中的.lib 项目上具有依赖关系，你可以为当前项目的.xml 文件处理.lib 项目中的.xdc 文件。  
  
## <a name="see-also"></a>请参阅  
 [属性页](../ide/property-pages-visual-cpp.md)   
 [属性页](../ide/property-pages-visual-cpp.md)