---
title: "UNIX | Microsoft Docs"
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
  - "unix"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "POSIX 兼容性"
  - "POSIX 文件名"
  - "UNIX"
  - "UNIX, 兼容性"
ms.assetid: 40792414-7a5b-415d-bfa8-2bfb1ebb3731
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# UNIX
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果计划将程序迁移到 UNIX，请遵循以下准则：  
  
-   不要从 SYS 子目录移除头文件。  只要你不打算把程序移植到UNIX，你可以把SYS头文件放到任何位置。  
  
-   使用 UNIX 兼容路径分隔符在采用表示路径和文件名的字符串用作参数的例程。 在路径中使用 UNIX 兼容路径分隔符，采用字符串表示路径，把文件名用作参数。  UNIX 仅支持正斜杠 \(\/\)，而Win32操作系统支持反斜杠 \(\\\)和正斜杠 \(\/\)。   因此本文档使用 UNIX 兼容正斜杠作为路径分隔符，例如在 `#include` 语句中。\(然而，Windows 操作系统命令 shell，CMD.EXE，不支持在命令提示符处输入正斜杠。\)  
  
-   使用在 UNIX 正确工作，大小写敏感性的路径和文件名。 在UNIX中使用对大小写敏感的路径和文件名能够正常工作。  Win32 操作系统中的文件分配表 \(FAT\) 文件系统不区分大小；NTFS 文件系统保留对目录列表区分大小写，但文件搜索和其他系统操作的情况将忽略大小写。  
  
    > [!NOTE]
    >  在这个 Visual C\+\+ 版本中，UNIX兼容性说明已经从函数中移除了。  
  
## 请参阅  
 [兼容性](../c-runtime-library/compatibility.md)