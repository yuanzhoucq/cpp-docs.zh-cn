---
title: "“XML 文档生成器工具”属性页 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCXDCMakeTool.ValidateIntelliSense"
  - "VC.Project.VCXDCMakeTool.SuppressStartupBanner"
  - "VC.Project.VCXDCMakeTool.DocumentLibraryDependencies"
  - "VC.Project.VCXDCMakeTool.OutputDocumentFile"
  - "VC.Project.VCXDCMakeTool.AdditionalDocumentFiles"
dev_langs: 
  - "C++"
ms.assetid: 645912b5-197a-4c36-ba58-64df09444ca0
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# “XML 文档生成器工具”属性页
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

“XML 文档生成器工具”属性页公开了 xdcmake.exe 的功能。  当源代码包含文档注释并且指定了 [\/doc（处理文档注释）](../build/reference/doc-process-documentation-comments-c-cpp.md) 时，xdcmake.exe 将 .xdc 文件合并到 .xml 文件中。  有关将文档注释添加到源代码中的信息，请参见 [建议的文档注释标记](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)。  
  
> [!NOTE]
>  开发环境（属性页）中的 xdcmake.exe 选项与 xdcmake.exe 在命令行中使用时的选项不同。  有关在命令行使用 xdcmake.exe 的信息，请参见 [XDCMake 参考](../ide/xdcmake-reference.md)。  
  
## UIElement 列表  
 **取消显示启动版权标志**  
 取消显示版权消息。  
  
 **附加文档文件**  
 您希望项目系统在其中查找 .xdc 文件的附加目录。  xdcmake 将始终查找项目生成的 .xdc 文件。  可指定多个目录。  
  
 **输出文档文件**  
 .xml 输出文件的名称和目录位置。  有关使用宏指定目录位置的信息，请参见 [用于生成命令和属性的宏](../ide/common-macros-for-build-commands-and-properties.md)。  
  
 **文档库依赖项**  
 如果您的项目在解决方案中的 .lib 项目上有依赖项，您可以将 .lib 项目中的 .xdc 文件处理到当前项目的 .xml 文件中。  
  
## 请参阅  
 [属性页](../ide/property-pages-visual-cpp.md)   
 [属性页](../ide/property-pages-visual-cpp.md)