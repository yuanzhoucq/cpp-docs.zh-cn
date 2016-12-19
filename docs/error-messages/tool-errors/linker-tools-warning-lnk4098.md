---
title: "链接器工具警告 LNK4098 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4098"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4098"
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具警告 LNK4098
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

默认库“library”与其他库的使用冲突；请使用 \/NODEFAULTLIB:library  
  
 您尝试与不兼容的库链接。  
  
> [!NOTE]
>  运行库现在包含可防止混合不同类型的指令。  如果尝试在同一个程序中使用不同类型的运行库或使用调试和非调试版本的运行库，则将收到此警告。  例如，如果编译一个文件以使用一种运行库，而编译另一个文件以使用另一种运行库（例如单线程运行库对多线程运行库），并尝试链接它们，则将得到此警告。  应将所有源文件编译为使用同一个运行库。  有关更多信息，请参见[使用运行库](../../build/reference/md-mt-ld-use-run-time-library.md)（**\/MD**、**\/MT** 和 **\/LD**）编译器选项。  
  
 可以使用链接器的 [\/VERBOSE:LIB](../../build/reference/verbose-print-progress-messages.md) 开关来确定链接器搜索的库。  如果收到 LNK4098，并想创建使用如单线程、非调试运行库的可执行文件，请使用 **\/VERBOSE:LIB** 选项确定链接器搜索的库。  链接器作为搜索的库输出的应是 LIBC.lib，而非 LIBCMT.lib、MSVCRT.lib、LIBCD.lib、LIBCMTD.lib 和 MSVCRTD.lib。  对每个要忽略的库可以使用 [\/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)，以通知链接器忽略错误的运行库。  
  
 下表显示根据要使用的运行库应忽略的库。  
  
|若要使用此运行库|请忽略这些库|  
|--------------|------------|  
|单线程 \(libc.lib\)|libcmt.lib、msvcrt.lib、libcd.lib、libcmtd.lib、msvcrtd.lib|  
|多线程 \(libcmt.lib\)|libc.lib、msvcrt.lib、libcd.lib、libcmtd.lib、msvcrtd.lib|  
|使用 DLL 的多线程 \(msvcrt.lib\)|libc.lib、libcmt.lib、libcd.lib、libcmtd.lib、msvcrtd.lib|  
|调试单线程 \(libcd.lib\)|libc.lib、libcmt.lib、msvcrt.lib、libcmtd.lib、msvcrtd.lib|  
|调试多线程 \(libcmtd.lib\)|libc.lib、libcmt.lib、msvcrt.lib、libcd.lib、msvcrtd.lib|  
|使用 DLL 的调试多线程 \(msvcrtd.lib\)|libc.lib、libcmt.lib、msvcrt.lib、libcd.lib、libcmtd.lib|  
  
 例如，如果收到此警告，并希望创建使用非调试、单线程版本的运行库的可执行文件，可以将下列选项与链接器一起使用：  
  
```  
/NODEFAULTLIB:libcmt.lib /NODEFAULTLIB:msvcrt.lib /NODEFAULTLIB:libcd.lib /NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib  
```