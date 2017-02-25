---
title: "How to: Include Resources at Compile Time | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.resvw.resource.including"
  - "vc.resvw.resource.including"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "compiling source code, including resources"
  - "comments [C++], compiled files"
  - "resources [Visual Studio], including at compile time"
  - "projects [C++], including resources"
  - "#include directive"
  - "include directive (#include)"
ms.assetid: 357e93c2-0a29-42f9-806f-882f688b8924
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# How to: Include Resources at Compile Time
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通常可简单且方便地在一个资源脚本 \(.rc\) 文件中使用所有资源的默认安排。  不过，可以通过在[“资源包括”对话框](../windows/resource-includes-dialog-box.md)的**“编译时指令”**框中列出相关资源，在编译时将其他文件中的资源添加到当前项目。  
  
 将资源置于主 .rc 文件之外的文件中有以下几个原因：  
  
-   向保存 .rc 文件时不会删除的资源语句添加注释。  
  
     资源编辑器不直接读取 .rc 或 resource.h 文件。  资源编译器将它们编译成由资源编辑器使用的 .aps 文件。  该文件是一个编译步骤，只存储符号数据。  与普通编译过程一样，非符号信息（如注释）在编译过程中将被放弃。  每当 .aps 文件与 .rc 文件不同步时，就会重新生成 .rc 文件（例如，当你进行“保存”时，资源编辑器将覆盖 .rc 文件和 resource.h 文件）。  对资源本身所做的任何更改依然包含在 .rc 文件中，但一旦覆盖 .rc 文件就总会丢失注释。  
  
-   包含已开发和测试并且无需进一步修改的资源。  （包含在内但没有 .rc 扩展名的任何文件都不可通过资源编辑器进行编辑。）  
  
-   包含正由几个不同项目使用，或属于源代码版本控制系统，因而必须存在于一个修改会影响所有项目的中心位置的资源。  
  
-   包括采用自定义格式的资源（如 RCDATA 资源）。  RCDATA 资源可能具有特殊要求。  例如，不能使用表达式作为 nameID 字段的值。  有关详细信息，请参阅 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 文档。  
  
 如果现有 .rc 文件中有一些部分满足以上任何条件，则应将这些部分置于一个或多个单独的 .rc 文件中，并使用[“资源包括”对话框](../windows/resource-includes-dialog-box.md)将它们包含在项目中。  在新项目的 \\res 子目录中创建的 *Projectname*.rc2 文件用于此用途。  
  
### 编译时在项目中包含资源  
  
1.  将资源置于具有唯一文件名的资源脚本文件中。  不要使用 *projectname*.rc，因为这是用于主资源脚本文件的文件名。  
  
2.  右键单击 .rc 文件（在[“资源视图”](../windows/resource-view-window.md)中），然后从快捷菜单中选择**“资源包括”**。  
  
3.  在**“编译时指令”**框中，添加 [\#include](../preprocessor/hash-include-directive-c-cpp.md) 编译器指令以在开发环境中将新资源文件包含在主资源文件中。  
  
     采用这种方式包含的文件中的资源会在编译时成为可执行文件的一部分。  它们在你处理项目的主 .rc 文件时不可直接进行编辑或修改。  需要单独打开包含的 .rc 文件。  包含在内但没有 .rc 扩展名的任何文件都不可通过资源编辑器进行编辑。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。 有关手动将资源文件添加到托管项目、访问资源、显示静态资源以及将资源字符串分配给属性的信息，请参阅[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 Win32  
  
## 请参阅  
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)