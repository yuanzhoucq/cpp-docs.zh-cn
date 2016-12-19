---
title: "了解 C/C++ 程序的清单生成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "清单 [C++]"
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
caps.latest.revision: 12
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 了解 C/C++ 程序的清单生成
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[清单](http://msdn.microsoft.com/library/aa375365)是一个 XML 文档，既可以是外部的 XML 文件，也可以是嵌入到应用程序或程序集内部的资源。  [独立应用程序](http://msdn.microsoft.com/library/aa375190)的清单用于管理共享的并行程序集的名称和版本，应用程序应当在运行时绑定到这些程序集。  [并行程序集](_win32_side_by_side_assemblies)的清单用于指定该程序集在名称、版本、资源和其他程序集上的依赖项。  
  
 创建独立应用程序或并行程序集的清单有两种方式。  第一，程序集的作者可遵循规则和命名要求手动创建清单文件。  或者，如果程序仅依赖于 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 程序集（如，CRT、MFC、ATL 或其他），则可由链接器自动生成清单。  
  
 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 库的头文件包含程序集信息，当这些库包含在应用程序代码中时，则链接器使用此程序集信息来生成最终二进制文件的清单。  链接器不会将清单文件嵌入到二进制文件中，而只能将其作为外部文件生成。  并非在所有的情况下，都可以将清单作为外部文件。  例如，建议在私有程序集中嵌入清单。  在命令行中生成时（如使用 nmake 生成代码时），可使用清单工具嵌入清单；有关更多信息，请参见 [命令行上的清单生成](../build/manifest-generation-at-the-command-line.md)。  当在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中生成时，可通过在**“项目属性”**对话框中设置清单工具的属性来嵌入清单；请参见 [Visual Studio 中的清单生成](../build/manifest-generation-in-visual-studio.md)。  
  
## 请参阅  
 [独立应用程序和并行程序集的概念](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [生成 C\/C\+\+ 独立应用程序和并行程序集](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)