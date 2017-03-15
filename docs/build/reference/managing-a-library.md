---
title: "管理库 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLibrarianTool.IgnoreAllDefaultLibraries"
  - "VC.Project.VCLibrarianTool.AdditionalDependencies"
  - "VC.Project.VCLibrarianTool.RemoveObjects"
  - "VC.Project.VCLibrarianTool.LibraryPaths"
  - "VC.Project.VCLibrarianTool.OutputFile"
  - "VC.Project.VCLibrarianTool.IgnoreDefaultLibraryNames"
  - "VC.Project.VCLibrarianTool.AdditionalLibraryDirectories"
  - "VC.Project.VCLibrarianTool.ListContentsFile"
  - "VC.Project.VCLibrarianTool.ListContents"
  - "VC.Project.VCLibrarianTool.SubSystemVersion"
  - "VC.Project.VCLibrarianTool.IgnoreDefaultLibraryName"
  - "VC.Project.VCLibrarianTool.SubSystem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/CONVERT 库管理器选项"
  - "/LIBPATH 库管理器选项"
  - "/LINK50COMPAT 库管理器选项"
  - "/LIST 库管理器选项"
  - "/OUT 库管理器选项"
  - "/REMOVE 库管理器选项"
  - "/SUBSYSTEM 库管理器选项"
  - "CONVERT 库管理器选项"
  - "-CONVERT 库管理器选项"
  - "LIB [C++], 管理 COFF 库"
  - "LIBPATH 库管理器选项"
  - "-LIBPATH 库管理器选项"
  - "LINK50COMPAT 库管理器选项"
  - "-LINK50COMPAT 库管理器选项"
  - "LIST 库管理器选项"
  - "-LIST 库管理器选项"
  - "对象文件"
  - "对象文件, 生成和修改"
  - "OUT 库管理器选项"
  - "-OUT 库管理器选项"
  - "REMOVE 库管理器选项"
  - "-REMOVE 库管理器选项"
  - "SUBSYSTEM 库管理器选项"
  - "-SUBSYSTEM 库管理器选项"
ms.assetid: f56a8b85-fbdc-4c09-8d8e-00f0ffe1da53
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 管理库
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

LIB 默认模式用于生成或修改 COFF 对象库。  当没有指定 \/EXTRACT（将对象复制到文件中）和 \/DEF（生成导入库）选项时，LIB 在此模式下运行。  
  
 若要从对象和\/或库生成库，请使用下列语法：  
  
```  
LIB [options...] files...  
```  
  
 此命令从一个或多个输入 *files* 创建库。  此 *files* 可以是 COFF 对象文件、32 位 OMF 对象文件或现有的 COFF 库。  LIB 创建一个包含指定文件中所有对象的库。  如果输入文件是 32 位 OMF 对象文件，则 LIB 在生成库之前将其转换到 COFF。  LIB 无法接受 LIB 16 位版本创建的库中的 32 位 OMF 对象。  必须首先使用 16 位 LIB 提取该对象，然后才能将提取的对象文件作为 32 位 LIB 的输入。  
  
 默认情况下，LIB 使用第一个对象或库文件的基文件名和扩展名 .lib 来命名输出文件。  输出文件放置在当前目录下。  如果已存在同名文件，输出文件将替换现有文件。  若要保留现有库，请使用 \/OUT 选项为输出文件指定名称。  
  
 下列选项适用于生成和修改库：  
  
 \/LIBPATH:`dir`  
 重写环境库路径。  有关详细信息，请参见 LINK [\/LIBPATH](../../build/reference/libpath-additional-libpath.md) 选项说明。  
  
 \/LIST  
 将有关输出库的信息显示到标准输出。  可以将输出重定向到文件。  可以使用 \/LIST 来确定现有库的内容，而不用修改库。  
  
 \/NAME:*filename*  
 当生成导入库时，指定正在为其生成导入库的 DLL 的名称。  
  
 \/NODEFAULTLIB  
 在解析外部引用时，从其搜索的库列表中移除一个或多个默认库。  有关更多信息，请参见 [\/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)。  
  
 \/OUT:*filename*  
 重写默认输出文件名。  默认情况下，输出库创建在当前目录中，并使用命令行中的第一个库或对象文件的基文件名和扩展名 .lib。  
  
 \/REMOVE:*object*  
 省略输出库中的指定 *object*。  LIB 会通过组合所有对象\(无论是在对象文件中还是在库中\)，然后使用 \/REMOVE 删除指定的任何对象，创建一个输出库。  
  
 \/SUBSYSTEM:{CONSOLE &#124; EFI\_APPLICATION &#124; EFI\_BOOT\_SERVICE\_DRIVER &#124; EFI\_ROM &#124; EFI\_RUNTIME\_DRIVER &#124; NATIVE &#124; POSIX &#124; WINDOWS &#124; WINDOWSCE}\[,\#\[.\#\#\]\]  
 通知操作系统如何运行通过链接到输出库创建的程序。  有关更多信息，请参见 LINK [\/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) 选项说明。  
  
 在命令行中指定的 LIB 选项不区分大小写。  
  
 可使用 LIB 执行下列库管理任务：  
  
-   若要将对象添加到库中，请指定现有库的文件名和新对象的文件名。  
  
-   若要组合库，请指定库文件名。  可使用单个 LIB 命令添加对象和组合库。  
  
-   若要用新对象替换库成员，请指定包含要替换的成员对象的库和新对象（或包含该对象的库）的文件名。  如果同名对象已存在于一个以上的输入文件中，则 LIB 将 LIB 命令行中指定的最后一个对象放入输出库中。  在替换库成员时，务必在包含旧对象的库之后指定新的对象或库。  
  
-   若要将成员从库中删除，请使用 \/REMOVE 选项。  LIB 在组合所有输入对象之后处理任何 \/REMOVE 规范，与命令行顺序无关。  
  
> [!NOTE]
>  不能在同一个步骤中既删除成员又将其提取到文件中。  必须首先使用 \/EXTRACT 提取成员对象，然后使用 \/REMOVE 再次运行 LIB。  此行为不同于在其他 Microsoft 产品中提供的 16 位 LIB（用于 OMF 库）的行为。  
  
## 请参阅  
 [LIB 引用](../../build/reference/lib-reference.md)