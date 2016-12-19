---
title: "Commit-To-Disk 常量 | Microsoft Docs"
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
  - "vc.constants"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "commit-to-disk 常量"
ms.assetid: 0b903b23-b4fa-431e-a937-51d95f695ecf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Commit-To-Disk 常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
## 语法  
  
```  
  
#include <stdio.h>  
```  
  
## 备注  
 这些特定于 Microsoft 的常数指定缓冲区与打开文件是否刷新到缓冲区操作系统的或到磁盘。  字符串中的模式指定读写类型类型访问权限 \(**"r"**、**"w"**、**"a"**、**"r\+"**、**"w\+"**，**"a\+"**\)。  
  
 提交对磁盘模式如下：  
  
 **c**  
 编写指定缓冲区中没有的内容记录到磁盘。  此功能只发生在提交对磁盘显式调用 [fflush](../c-runtime-library/reference/fflush.md) [\_flushall](../c-runtime-library/reference/flushall.md) 或函数。  在处理敏感数据时，此模式很有用。  例如，在中，如果程序终止，在对 `fflush` 或 `_flushall`的调用中，您可以确定数据到达后操作系统的缓冲区。  但是，文件，除非打开使用 **c** 选项，数据不可能使到磁盘，则操作系统也终止。  
  
 **n**  
 编写指定缓冲区中未记录的内容。操作系统的缓冲区。  操作系统可以缓存数据然后确定一的最佳时间写入磁盘。  在大多数情况下，此行为为有效的程序行为进行。  但是，数据，则保留重要 \(如或\) 飞机票银行事务信息请考虑使用 **c** 选项。  溢出模式；默认值为 **n**。  
  
> [!NOTE]
>  **c** 和 **n** 选项不是 ANSI 标准的一部分，但是 Microsoft 的 `fopen`，扩展，因此不应使用 ANSI 可移植性需的位置。  
  
## 使用与现有代码的提交对磁盘功能  
 默认情况下，设置为 [fflush](../c-runtime-library/reference/fflush.md) 的调用或 [\_flushall](../c-runtime-library/reference/flushall.md) 库函数将数据写入操作系统维护的缓冲区。  操作系统决定的最佳时间实际数据写入磁盘。  运行时库的提交到磁盘的功能，可以确保关键数据直接写入磁盘，而不是操作系统的缓冲区。  可以将此功能的现有程序，而无需重写它通过其 COMMODE.OBJ 链接的对象文件。  
  
 在生成的可执行文件中，对 `fflush` 的调用写入缓冲区的内容直接到磁盘，因此，对 `_flushall` 的调用将所有缓冲区内容到磁盘。  这两个函数会很 COMMODE.OBJ 影响的唯一一部分。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [流 I\/O](../c-runtime-library/stream-i-o.md)   
 [\_fdopen、\_wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen、\_wfopen](../c-runtime-library/reference/fopen-wfopen.md)   
 [全局常量](../c-runtime-library/global-constants.md)