---
title: "编译器选项 | Microsoft Docs"
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
  - "cl.exe 编译器"
  - "编译器选项, C++"
  - "IPF Visual C++ 编译器"
  - "Itanium Visual C++ 编译器"
  - "x64 Visual C++ 编译器"
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# 编译器选项
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

cl.exe 是控制 Microsoft C 和 C\+\+ 编译器以及链接器的工具。cl.exe 只能在支持 Microsoft Visual Studio 的操作系统中运行。  
  
> [!NOTE]
>  您只能从 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 命令提示符处启动此工具。  而不能从系统命令提示符或文件资源管理器中启动此工具。  
  
 编译器产生通用对象文件格式 \(COFF\) 对象 \(.obj\) 文件。  链接器产生可执行文件 \(.exe\) 或动态链接库文件 \(DLL\)。  
  
 注意，所有编译器选项都区分大小写。  
  
 若要编译但不链接，请使用 [\/c](../../build/reference/c-compile-without-linking.md)。  
  
## 查找选项  
 若要查找特定编译器选项，请参见以下列表之一：  
  
-   [按字母顺序列出的编译器选项](../../build/reference/compiler-options-listed-alphabetically.md)  
  
-   [按类别列出的编译器选项](../../build/reference/compiler-options-listed-by-category.md)  
  
## 指定选项  
 每个编译器选项的主题讨论如何在开发环境中设置该选项。  有关指定开发环境外的选项的信息，请参见：  
  
-   [编译器命令行语法](../../build/reference/compiler-command-line-syntax.md)  
  
-   [CL 命令文件](../../build/reference/cl-command-files.md)  
  
-   [CL 环境变量](../../build/reference/cl-environment-variables.md)  
  
## 相关生成工具  
 使用 [NMAKE](../../build/nmake-reference.md) 生成输出文件。  
  
 使用 [BSCMAKE](../../build/reference/bscmake-reference.md) 支持类浏览。  
  
 [链接器选项](../../build/reference/linker-options.md)还影响如何生成程序。  
  
## 请参阅  
 [C\/C\+\+ 生成参考](../../build/reference/c-cpp-building-reference.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [快速编译](../../build/reference/fast-compilation.md)   
 [CL 调用链接器](../../build/reference/cl-invokes-the-linker.md)