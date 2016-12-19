---
title: "在项目中使用预编译头 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "预编译的头"
ms.assetid: 95010260-a035-4327-9d61-222016ac146c
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 在项目中使用预编译头
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

前面几节概述以下预编译头：\/Yc 和 \/Yu、\/Fp 选项以及 [hdrstop](../../preprocessor/hdrstop.md) 杂注。  本节描述一种在项目中使用手动预编译头选项的方法；在文章的最后提供了一个示例生成文件及该文件管理的代码。  
  
 有关在项目中使用手动预编译头选项的其他方法，请参考位于 MFC\\SRC 目录中的生成文件之一，该目录是在 Visual C\+\+ 默认安装期间创建的。  这些生成文件所采用的方法与本节介绍的方法类似，但更多地使用了 Microsoft 程序维护实用工具 \(NMAKE\) 宏，并对生成过程提供更多的控制。  
  
 本节包含下列主题：  
  
-   [生成过程中的 PCH 文件](../../build/reference/pch-files-in-the-build-process.md)  
  
-   [PCH 的示例生成文件](../../build/reference/sample-makefile-for-pch.md)  
  
-   [PCH 的代码示例](../../build/reference/example-code-for-pch.md)  
  
## 请参阅  
 [创建预编译的头文件](../../build/reference/creating-precompiled-header-files.md)