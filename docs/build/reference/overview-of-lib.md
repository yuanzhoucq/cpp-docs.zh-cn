---
title: "LIB 概述 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Lib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LIB [C++], modes"
ms.assetid: e997d423-f574-434f-8b56-25585d137ee0
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# LIB 概述
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

LIB 创建标准库、导入库和导出文件，在生成程序时可将它们与 [LINK](../../build/reference/linker-options.md) 一起使用。  LIB 从命令提示运行。  
  
 可在下列几种模式下使用 LIB：  
  
-   [生成或修改 COFF 库](../../build/reference/managing-a-library.md)  
  
-   [将成员对象提取到文件中](../../build/reference/extracting-a-library-member.md)  
  
-   [创建导出文件和导入库](../../build/reference/working-with-import-libraries-and-export-files.md)  
  
 这些模式是互斥的；每次只能以一种模式使用 LIB。  
  
## Lib 选项  
 下表列出了 lib.exe 的选项，并提供了可获得更多信息的链接。  
  
 **\/DEF**  
 创建导入库和导出文件。  
  
 有关更多信息，请参见[生成导入库和导出文件](../../build/reference/building-an-import-library-and-export-file.md)。  
  
 **\/ERRORREPORT**  
 将有关 lib.exe 内部错误的信息发送给 Microsoft。  
  
 有关更多信息，请参见[运行 LIB](../../build/reference/running-lib.md)。  
  
 **\/EXPORT**  
 从程序中导出函数。  
  
 有关更多信息，请参见[生成导入库和导出文件](../../build/reference/building-an-import-library-and-export-file.md)。  
  
 **\/EXTRACT**  
 创建一个对象 \(.obj\) 文件，其中包含现有库的一个成员的副本。  
  
 有关更多信息，请参见[提取库成员](../../build/reference/extracting-a-library-member.md)。  
  
 **\/INCLUDE**  
 将符号添加到符号表中。  
  
 有关更多信息，请参见[生成导入库和导出文件](../../build/reference/building-an-import-library-and-export-file.md)。  
  
 **\/LIBPATH**  
 重写环境库路径。  
  
 有关更多信息，请参见[管理库](../../build/reference/managing-a-library.md)。  
  
 **\/LIST**  
 将有关输出库的信息显示到标准输出。  
  
 有关更多信息，请参见[管理库](../../build/reference/managing-a-library.md)。  
  
 **\/LTCG**  
 导致使用链接时代码生成机制生成库。  
  
 有关更多信息，请参见[运行 LIB](../../build/reference/running-lib.md)。  
  
 **\/MACHINE**  
 指定程序的目标平台。  
  
 有关更多信息，请参见[运行 LIB](../../build/reference/running-lib.md)。  
  
 **\/NAME**  
 当生成导入库时，指定正在为其生成导入库的 DLL 的名称。  
  
 有关更多信息，请参见[管理库](../../build/reference/managing-a-library.md)。  
  
 **\/NODEFAULTLIB**  
 在解析外部引用时，从其搜索的库列表中移除一个或多个默认库。  
  
 有关更多信息，请参见[管理库](../../build/reference/managing-a-library.md)。  
  
 **\/NOLOGO**  
 取消显示 LIB 版权信息和版本号，并防止回显命令文件。  
  
 有关更多信息，请参见[运行 LIB](../../build/reference/running-lib.md)。  
  
 **\/OUT**  
 重写默认输出文件名。  
  
 有关更多信息，请参见[管理库](../../build/reference/managing-a-library.md)。  
  
 **\/REMOVE**  
 忽略来自输出库的对象。  
  
 有关更多信息，请参见[管理库](../../build/reference/managing-a-library.md)。  
  
 **\/SUBSYSTEM**  
 通知操作系统如何运行通过链接到输出库创建的程序。  
  
 有关更多信息，请参见[管理库](../../build/reference/managing-a-library.md)。  
  
 **\/VERBOSE**  
 显示有关会话进度的详细信息，其中包括所添加的 .obj 文件的名称。  
  
 有关更多信息，请参见[运行 LIB](../../build/reference/running-lib.md)。  
  
 **\/WX**  
 将警告视为错误。  
  
 有关更多信息，请参见[运行 LIB](../../build/reference/running-lib.md)。  
  
## 请参阅  
 [LIB 引用](../../build/reference/lib-reference.md)   
 [LIB 输入文件](../../build/reference/lib-input-files.md)   
 [LIB 输出文件](../../build/reference/lib-output-files.md)   
 [其他 LIB 输出](../../build/reference/other-lib-output.md)   
 [库结构](../../build/reference/structure-of-a-library.md)