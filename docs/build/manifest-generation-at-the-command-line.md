---
title: "命令行上的清单生成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "清单工具 (mt.exe)"
  - "清单 [C++]"
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 命令行上的清单生成
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在命令行中使用 nmake 或类似工具生成 C\/C\+\+ 应用程序时，将在链接器处理完所有对象文件并生成最终二进制文件后生成清单。  链接器收集存储在对象文件中的程序集信息，并将此信息合并到最终清单文件中。  默认情况下，链接器将生成一个名为\<binary\_name\>.\<extension\>.manifest 的文件，用于描述最终二进制文件。  链接器不会将清单文件嵌入此二进制文件中，只能将清单生成为外部文件。  有几种方法可将清单嵌入最终二进制文件中，如使用[清单工具 \(mt.exe\)](http://msdn.microsoft.com/library/aa375649) 或将清单编译为资源文件。  切记：将清单嵌入最终二进制文件中时，必须遵守特定的规则，这样才能启用诸如增量链接、签名、编辑并继续等功能。  [如何：将清单嵌入到 C\/C\+\+ 应用程序](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md) 中讨论了在命令行生成清单时使用的这些功能及其他选项。  
  
## 请参阅  
 [清单](http://msdn.microsoft.com/library/aa375365)   
 [\/INCREMENTAL（增量链接）](../build/reference/incremental-link-incrementally.md)   
 [强名称程序集（程序集签名）](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)   
 [编辑并继续](../Topic/Edit%20and%20Continue.md)   
 [了解 C\/C\+\+ 程序的清单生成](../build/understanding-manifest-generation-for-c-cpp-programs.md)