---
title: "编译器和链接器中的 Unicode 支持 | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.UseUnicodeResponseFiles"
  - "VC.Project.VCLibrarianTool.UseUnicodeResponseFiles"
  - "VC.Project.VCCLCompilerTool.UseUnicodeResponseFiles"
  - "VC.Project.VCXDCMakeTool.UseUnicodeResponseFiles"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Unicode, Visual C++"
ms.assetid: acc1d322-56b9-4696-a30e-2af891a4e288
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器和链接器中的 Unicode 支持
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题介绍 Visual C\+\+ 生成工具中的 Unicode 支持。  
  
 文件名  
 命令行或编译器指令（如 \#include）中指定的文件名中现在可能包含 Unicode 字符。  
  
 源代码文件  
 现在，标识符、宏、字符串和字符文本以及注释中均支持 Unicode 字符。现在也支持通用字符名称。  
  
 可按以下编码格式将 Unicode 字符输入到源代码文件中：  
  
-   具有或不具有字节顺序标记 \(BOM\) 的 UTF\-16 Little Endian  
  
-   具有或不具有 BOM 的 UTF\-16 Big Endian  
  
-   具有 BOM 的 UTF\-8  
  
 Output  
 在编译期间，编译器以 UTF\-16 格式将诊断输出到控制台。可在控制台显示的字符由控制台窗口属性决定。重定向到文件的编译器输出位于当前 ANSI 控制台代码页中。  
  
 链接器响应文件和 .DEF 文件  
 响应文件和 DEF 文件可以是具有字节顺序标记的 UTF\-16，也可以是 ANSI。以前仅支持 ANSI。  
  
 .asm 和 .cod 转储  
 默认情况下，.asm 和 .cod 转储为 ANSI 格式，以便兼容 MASM。使用 \/FAu 则输出 UTF\-8。请注意，如果指定 \/FAs，则将只是直接输出混合源文件，而且可能会显示为乱码，例如，当源代码为 UTF\-8 并且未指定 \/FAsu 时。  
  
 可以通过选择合适的工具以及选择**“启用 Unicode 响应文件”**属性（默认为启用）在开发环境中启用 Unicode 文件名（请参见 [如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)）。  有些情况下需要更改此默认值，例如要修改开发环境以便使用不具有 Unicode 支持的编译器时。  
  
## 请参阅  
 [在命令行上生成](../../build/building-on-the-command-line.md)