---
title: "C/C++ 生成参考 | Microsoft Docs"
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
  - "builds [C++], 附加信息"
  - "cl.exe 编译器 [C++], 生成程序"
  - "编译源代码 [C++], 附加信息"
  - "链接器 [C++], 生成参考"
ms.assetid: 100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C/C++ 生成参考
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 提供两种生成 C\/C\+\+ 程序的方法。  最容易（并且最常用）的方法是[在 Visual C\+\+ 开发环境中生成](../../ide/building-cpp-projects-in-visual-studio.md)。  另外一种方法是[使用命令行工具从命令提示符生成](../../build/building-on-the-command-line.md)。  无论使用哪种方法，您都可以使用 Visual C\+\+ 源编辑器或您选择的第三方编辑器创建源文件。  
  
 如果程序使用生成文件而不是 .vcxproj 文件，则仍可以在开发环境中把它生成为[外部项目](../../ide/building-external-projects.md)。  
  
## 本节内容  
 [编译 C\/C\+\+ 程序](../../build/reference/compiling-a-c-cpp-program.md)  
 描述编译器，编译器用于创建一个包含机器码、链接器指令、节、外部引用和函数\/数据名的对象文件。  
  
 [链接](../../build/reference/linking.md)  
 描述链接器，链接器用于组合来自编译器创建的对象文件中的代码和来自静态链接库的代码，解析名称引用并创建可执行文件。  
  
 [发布版本](../../build/reference/release-builds.md)  
 提供有关从调试版本更改为发布版本的原因和场合的信息，并探讨从调试版本更改为发布版本时可能遇到的某些问题。  
  
 [优化代码](../../build/reference/optimizing-your-code.md)  
 提供指向探讨优化代码机制的主题的链接：  
  
 [C\/C\+\+ 生成工具](../../build/reference/c-cpp-build-tools.md)  
 提供下列用于查看或操作生成输出的命令行工具：  
  
 [C\/C\+\+ 生成错误](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)  
 介绍内容表中的生成错误部分。  
  
## 相关章节  
 [C\/C\+\+ 预处理器参考](../../preprocessor/c-cpp-preprocessor-reference.md)  
 探讨用于通过翻译宏、运算符以及指令来为编译器准备源文件的预处理器。  
  
 [了解自定义生成步骤和生成事件](../../ide/understanding-custom-build-steps-and-build-events.md)  
 探讨如何自定义生成过程。  
  
 [生成 C\/C\+\+ 程序](../../build/building-c-cpp-programs.md)  
 提供描述如下内容的主题链接：从命令行或从 Visual Studio 集成开发环境生成程序。  
  
 [设置编译器选项](../../build/reference/setting-compiler-options.md)  
 描述如何在开发环境中或命令行上设置编译器选项。  
  
 [编译器选项](../../build/reference/compiler-options.md)  
 提供指向探讨如何使用编译器选项的主题的链接。  
  
 [设置链接器选项](../../build/reference/setting-linker-options.md)  
 描述如何在集成开发环境中或集成开发环境外设置链接器选项。  
  
 [链接器选项](../../build/reference/linker-options.md)  
 提供指向探讨如何使用链接器选项的主题的链接。  
  
 [BSCMAKE 参考](../../build/reference/bscmake-reference.md)  
 描述用于从在编译期间创建的 .sbr 文件生成浏览信息文件 \(.bsc\) 的 Microsoft 浏览信息维护实用工具 \(BSCMAKE.EXE\)。  
  
 [LIB 引用](../../build/reference/lib-reference.md)  
 描述用于创建和管理通用对象文件格式 \(COFF\) 对象文件库的 Microsoft 库管理器 \(LIB.exe\)。  
  
 [EDITBIN 参考](../../build/reference/editbin-reference.md)  
 描述用于修改通用对象文件格式 \(COFF\) 二进制文件的 Microsoft COFF 二进制文件编辑器 \(EDITBIN.EXE\)。  
  
 [DUMPBIN 参考](../../build/reference/dumpbin-reference.md)  
 描述用于显示有关通用对象文件格式 \(COFF\) 二进制文件的信息的 Microsoft COFF 二进制文件转储器 \(DUMPBIN.EXE\)。  
  
 [NMAKE 参考](../../build/nmake-reference.md)  
 描述 Microsoft 程序维护实用工具 \(NMAKE.EXE\)，它是一个基于说明文件中包含的命令生成项目的工具。