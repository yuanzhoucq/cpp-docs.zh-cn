---
title: "用作链接器输入的 .Obj 文件 | Microsoft Docs"
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
  - "用作链接器输入的 .obj 文件"
  - "COFF 文件"
  - "LINK 工具 [C++], .obj 文件"
  - "链接器 [C++], OBJ 文件作为输入"
  - "OBJ 文件作为链接器输入"
  - "对象文件, 链接器输出"
  - "OMF 对象文件"
ms.assetid: 3028e423-8b10-4972-8eb4-6e9ae58f0a26
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 用作链接器输入的 .Obj 文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

链接器工具 \(LINK.EXE\) 接受通用对象文件格式 \(COFF\) 的 .obj 文件。  
  
## 备注  
 Microsoft 提供了一个可下载文档，其中定义了通用对象文件格式。  有关更多信息，请下载修订版 8.1 或更高版本的 [Microsoft 可移植可执行文件和通用对象文件格式规范](http://go.microsoft.com/fwlink/?LinkId=93292)。  
  
## Unicode 支持  
 从 Visual Studio 2005 开始，Microsoft Visual C\+\+ 编译器按照 ISO\/IEC C 和 C\+\+ 标准的定义，支持在标识符中使用 Unicode 字符。  之前版本的编译器仅支持在标识符中使用 ASCII 字符。  为了在函数名、类名和静态变量名中支持 Unicode，编译器和链接器对 .obj 文件中的 COFF 符号使用 Unicode UTF\-8 编码。  UTF\-8 编码向上兼容 Visual Studio 早期版本使用的 ASCII 编码。  
  
 有关编译器和链接器的更多信息，请参见[编译器和链接器中的 Unicode 支持](../../build/reference/unicode-support-in-the-compiler-and-linker.md)。  有关 Unicode 标准的更多信息，请 参见[Unicode](http://go.microsoft.com/fwlink/?LinkId=37123) 结构。  
  
## 请参阅  
 [LINK 输入文件](../../build/reference/link-input-files.md)   
 [链接器选项](../../build/reference/linker-options.md)   
 [支持 Unicode](../../text/support-for-unicode.md)   
 [编译器和链接器中的 Unicode 支持](../../build/reference/unicode-support-in-the-compiler-and-linker.md)   
 [Unicode 标准](http://go.microsoft.com/fwlink/?LinkId=37123)   
 [通用对象文件格式规范](http://go.microsoft.com/fwlink/?LinkId=93292)