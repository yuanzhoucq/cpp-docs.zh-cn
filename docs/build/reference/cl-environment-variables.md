---
title: "CL 环境变量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 编译器, 环境变量"
  - "环境变量, CL 编译器"
  - "INCLUDE 环境变量"
  - "LIBPATH 环境变量"
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# CL 环境变量
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

CL 工具使用以下环境变量:  
  
-   CL 和 \_CL\_（如果已定义）。  CL 工具会将 CL 环境变量中定义的选项和参数预置到命令行参数前面，并在处理之前附加 \_CL\_ 中定义的选项和参数。  
  
-   INCLUDE，必须指向 Visual C\+\+ 安装的 \\include 子目录。  
  
-   LIBPATH，指定用于搜索使用 [\#using](../../preprocessor/hash-using-directive-cpp.md) 引用的元数据文件的目录。  有关 LIBPATH 的详细信息，请参阅 `#using`。  
  
 可以使用以下语法设置 CL 或 \_CL\_ 环境变量：  
  
```  
SET CL=[ [option] ... [file] ...] [/link link-opt ...]  
SET _CL_=[ [option] ... [file] ...] [/link link-opt ...]  
```  
  
 有关 CL 和 \_CL\_ 环境变量的参数的详细信息，请参阅[编译器命令行语法](../../build/reference/compiler-command-line-syntax.md)。  
  
 可以使用这些环境变量定义最常使用的文件和选项，并使用命令行为特定用途定义特定文件和选项。  CL 和 \_CL\_ 环境变量限制为 1024 个字符（命令行输入限制）。  
  
 不能使用 \/D 选项定义使用等号 \(\=\) 的符号。  可以将等号替换为数字符号 \(\#\)。  通过这种方式，可以使用 CL 或 \_CL\_ 环境变量定义定义具有显式值的预处理器常量（例如，`/DDEBUG#1` 可定义 `DEBUG=1`）。  
  
 有关相关信息，请参阅[设置环境变量](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。  
  
## 示例  
 下面是设置 CL 环境变量的示例：  
  
```  
SET CL=/Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ  
```  
  
 设置此环境变量时，如果在命令行处输入 `CL INPUT.C`，则这是有效的命令：  
  
```  
CL /Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ INPUT.C  
```  
  
 下面的示例使普通 CL 命令编译源文件 FILE1.c 和 FILE2.c，然后链接对象文件 FILE1.obj、FILE2.obj 和 FILE3.obj：  
  
```  
SET CL=FILE1.C FILE2.C  
SET _CL_=FILE3.OBJ  
CL  
  
```  
  
 这与下面的命令行的效果相同：  
  
```  
CL FILE1.C FILE2.C FILE3.OBJ  
```  
  
## 请参阅  
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)