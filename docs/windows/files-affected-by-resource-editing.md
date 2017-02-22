---
title: "Files Affected by Resource Editing | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resource editing"
  - "resources [Visual Studio], editing"
ms.assetid: d0820df1-ba84-40ac-bce9-29ea5ee7e3f8
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Files Affected by Resource Editing
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在资源编辑会话期间，Visual Studio 环境使用下表中显示的文件。  
  
|文件名|说明|  
|---------|--------|  
|Resource.h|由开发环境生成的头文件；包含符号定义。|  
|Filename.aps|当前资源脚本文件的二进制版本；用于快速加载。<br /><br /> 资源编辑器不直接读取 .rc 或 resource.h 文件。  资源编译器将它们编译成由资源编辑器使用的 .aps 文件。  该文件是一个编译步骤，只存储符号数据。  与普通编译过程一样，非符号信息（如注释）在编译过程中将被放弃。  每当 .aps 文件与 .rc 文件不同步时，就会重新生成 .rc 文件（例如，当你进行“保存”时，资源编辑器将覆盖 .rc 文件和 resource.h 文件）。  对资源本身所做的任何更改依然包含在 .rc 文件中，但一旦覆盖 .rc 文件就总会丢失注释。  有关如何保留注释的信息，请参阅[编译时包含资源](../windows/how-to-include-resources-at-compile-time.md)。|  
|.rc|包含当前项目中的资源脚本的资源脚本文件。  每当进行保存时，.aps 文件就会覆盖此文件。|  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。 有关手动将资源文件添加到托管项目、访问资源、显示静态资源以及将资源字符串分配给属性的信息，请参阅[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 Win32  
  
## 请参阅  
 [Resource Files](../mfc/resource-files-visual-studio.md)