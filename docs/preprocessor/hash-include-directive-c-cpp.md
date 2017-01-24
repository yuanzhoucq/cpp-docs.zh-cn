---
title: "#include 指令 (C/C++) | Microsoft Docs"
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
  - "#include"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#include 指令"
  - "include 指令 (#include)"
  - "预处理器, 指令"
ms.assetid: 17067dc0-8db1-4f2d-b43e-ec12ecf83238
caps.latest.revision: 15
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #include 指令 (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

告知预处理器将已指定文件的内容视为它们在源程序中指令出现处出现的方式处理。  
  
## 语法  
  
```  
  
      #include  "path-spec"  
#include  <path-spec>  
```  
  
## 备注  
 可以将常数和宏定义编入包含文件中，然后使用 `#include` 指令将它们添加到任何源文件中。  包含文件还可用于合并外部变量和复杂数据类型的声明。  在为此目的而创建的包含文件中，类型只能定义和命名一次。  
  
 `path-spec` 是一个文件名，可以选择性地在其前放置一个目录说明。  文件名必须命名现有文件。  `path-spec` 的语法取决于编译程序时基于的操作系统。  
  
 有关如何在使用 [\/clr](../build/reference/clr-common-language-runtime-compilation.md) 编译的 C\+\+ 应用程序中引用程序集的信息，请参阅 [\#using](../preprocessor/hash-using-directive-cpp.md)。  
  
 两种语法形式都会导致指令被替换为指定包含文件的整个内容。  两种形式之间的区别在于，在未完全指定路径时预处理器搜索标头文件的顺序。  下表显示了这两种语法形式之间的差异。  
  
|语法形式|操作|  
|----------|--------|  
|带引号的形式|预处理器按以下顺序搜索包含文件：<br /><br /> 1.  在包含 `#include` 语句的文件所在的同一目录中。<br />2.  在当前打开的包含文件的目录中，采用与打开它们的顺序相反的顺序。  搜索从父包含文件的目录中开始进行，然后继续向上到任何祖父包含文件的目录。<br />3.  跟随每个 \/I 编译器选项指定的路径。<br />4.  跟随 INCLUDE 环境变量指定的路径。|  
|尖括号形式|预处理器按以下顺序搜索包含文件：<br /><br /> 1.  跟随每个 \/I 编译器选项指定的路径。<br />2.  通过命令行进行编译时，跟随 INCLUDE 环境变量指定的路径。|  
  
 只要找到具有给定名称的文件，预处理器就会停止搜索。  如果在两个双引号 \(" "\) 之间括住包含文件的完整明确的路径说明，则预处理器只搜索该路径说明，并忽略标准目录。  
  
 如果用双引号括起来的文件名是不完整的路径规格，则预处理器将首先搜索“父”文件的目录。  父文件是包含 `#include` 指令的文件。  例如，如果将名为 `file2` 的文件包括在名为 `file1` 的文件中，则 `file1` 为父文件。  
  
 包含文件可以“嵌套”；即 `#include` 指令可以出现在由另一个 `#include` 指令命名的文件中。  例如，`file2` 可以包含 `file3`。  在这种情况下，`file1` 依然为 `file2` 的父级，但它可能为 `file3` 的“祖父级”。  
  
 当嵌套了包含文件并从命令行开始编译时，目录搜索会从父文件的目录开始，然后在所有祖父文件的目录中继续进行。  即，搜索将相对于包含当前正在处理的源的目录开始。  如果找不到该文件，则搜索会移动到由 \/I 编译器选项指定的目录。  最后，将搜索 INCLUDE 环境变量指定的目录。  
  
 在开发环境中，将忽略 INCLUDE 环境变量。  有关如何设置要为包含文件搜索的目录的信息（同样应用于 LIB 环境变量），请参阅 [VC\+\+ Directories, Projects, Options Dialog Box](http://msdn.microsoft.com/zh-cn/e027448b-c811-4c3d-8531-4325ad3f6e02)。  
  
 此示例使用尖括号显示文件包含：  
  
```  
#include <stdio.h>  
```  
  
 此示例将名为 STDIO.H 文件的内容添加到源程序。  尖括号会促使预处理器在搜索 \/I 编译器选项指定的目录之后，搜索 STDIO.H 的 INCLUDE 环境变量指定的目录。  
  
 下一个示例用引号形式显示文件包含：  
  
```  
#include "defs.h"  
```  
  
 此示例将 DEFS.H 指定的文件的内容添加到源程序。  双引号意味着，预处理器将首先搜索包含父源文件的目录。  
  
 包含文件的嵌套可扩展至 10 个级别。  处理嵌套的 `#include` 时，预处理器将继续在源文件中插入封闭的包含文件。  
  
 **Microsoft 专用**  
  
 为了查找可包含的源文件，预处理器会先搜索 \/I 编译器选项指定的目录。  如果 \/I 选项不存在或失败，预处理器会使用 INCLUDE 环境变量在尖括号中查找包含文件。  INCLUDE 环境变量和 \/I 编译器选项可以包含使用分号 \(;\) 分隔的多个路径。  如果多个目录显示为 \/I 选项的一部分或在 INCLUDE 环境变量中，预处理器会按它们的出现顺序搜索它们。  
  
 例如，命令  
  
```  
CL /ID:\MSVC\INCLUDE MYPROG.C  
```  
  
 会促使预处理器搜索包含文件（如 STDIO.H）的目录 D:\\MSVC\\INCLUDE\\。  命令  
  
```  
SET INCLUDE=D:\MSVC\INCLUDE  
CL MYPROG.C  
```  
  
 具有同样的作用。  如果两组搜索都失败，则会生成严重的编译器错误。  
  
 如果为路径包含冒号的包含文件指定完整的文件名（例如，F:\\MSVC\\SPECIAL\\INCL\\TEST.H），则预处理器会遵循该路径。  
  
 对于指定为 `#include` "`path-spec`" 的包含文件，目录搜索从父文件的目录开始，然后在任何祖父文件的目录中继续进行。  也就是说，搜索将相对于包含当前正在处理的 `#include` 指令的源文件内容的目录开始。  如果没有祖父文件且没有找到该文件，则搜索会像文件名括在尖括号中一样继续进行。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [预处理器指令](../preprocessor/preprocessor-directives.md)