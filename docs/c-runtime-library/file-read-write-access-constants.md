---
title: "文件读取/写入访问常量 | Microsoft Docs"
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
  - "c.constants.file"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "用于文件读取/写入的访问常量"
  - "常量 [C++], 文件特性"
  - "文件读取/写入访问常量"
  - "读取/写入访问常量"
  - "写入访问常量"
ms.assetid: 56cd1d22-39a5-4fcf-bea2-7046d249e8ee
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 文件读取/写入访问常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
#include <stdio.h>  
```  
  
## 备注  
 这些常数指定文件请求的访问类型 \(“a”，“r“,或"w”\) 。  [转换模式](../c-runtime-library/file-translation-constants.md) \(“b”或“t”\) 和 [提交磁盘模式](../c-runtime-library/commit-to-disk-constants.md) \(“c”或“n”\) 都可以指定访问类型。  
  
 访问类型在下面描述。  
  
 **"a"**  
 打开写在文件（追加）的结束；如果它不存在，那么先创建文件。  所有写入操作发生在文件末尾。  尽管使用 `fseek` 或 **rewind** 可重新定位文件指针，但在执行任何写入操作前，文件指针将始终被移回文件末尾。  
  
 **"a\+"**  
 与上述相同，但也允许读取。  
  
 **"r"**  
 打开以便读取。  如果文件不存在或无法找到，打开文件的调用将失败。  
  
 **"r\+"**  
 打开以便读取和写入。  如果文件不存在或无法找到，打开文件的调用将失败。  
  
 **“w”**  
 打开用于写入的空文件。  如果给定文件存在，则其内容会被销毁。  
  
 **“w\+”**  
 打开用于读取和写入的空文件。  如果给定文件存在，则其内容会被销毁。  
  
 当指定"r\+", "w\+" 或 "a\+" 类型时，读取和写入都是被允许的（文件将处于打开状态以进行“更新”）。  但是，当您在读取和写入之间切换时，必须介入`fflush`，`fsetpos`，`fseek`, 或**rewind**操作。  如果需要，可以为`fsetpos` 或 `fseek` 操作指定当前位置。  
  
## 请参阅  
 [\_fdopen、\_wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen、\_wfopen](../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen、\_wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)   
 [\_fsopen、\_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [\_popen、\_wpopen](../c-runtime-library/reference/popen-wpopen.md)   
 [全局常量](../c-runtime-library/global-constants.md)