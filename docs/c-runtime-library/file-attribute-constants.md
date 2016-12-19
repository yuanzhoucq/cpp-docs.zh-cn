---
title: "文件特性常量 | Microsoft Docs"
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
  - "A_HIDDEN"
  - "_A_NORMAL"
  - "_A_SUBDIR"
  - "_A_RDONLY"
  - "A_NORMAL"
  - "A_SUBDIR"
  - "_A_SYSTEM"
  - "c.constants.file"
  - "_A_HIDDEN"
  - "A_RDONLY"
  - "_A_ARCH"
  - "A_ARCH"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_A_ARCH 常量"
  - "_A_HIDDEN 常量"
  - "_A_NORMAL 常量"
  - "_A_RDONLY 常量"
  - "_A_SUBDIR 常量"
  - "_A_SYSTEM 常量"
  - "常量 [C++], 文件特性"
  - "文件特性常量 [C++]"
  - "文件 [C++], 文件特性常量"
ms.assetid: 8dc8ccb9-99f5-446b-876c-7ebecc2f764f
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 文件特性常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
#include <io.h>  
```  
  
## 备注  
 这些常数指定函数当前文件的状态或指定目录。  
  
 下列清单常数代表这些状态：  
  
 `_A_ARCH`  
 Archive.  设置什么时候文件被改变，并通过 BACKUP命令清理文件。  值：0x20  
  
 `_A_HIDDEN`  
 隐藏文件  通常不会看到 DIR 命令，因此，除非使用 \/AH 选项。  返回有关常规文件和文件状态的信息。  值：0x02  
  
 `_A_NORMAL`  
 Normal。  文件能无任何限制的读取或写入。  值：0x00  
  
 `_A_RDONLY`  
 只读。  文件不能打开写入。并且，具有相同名称的文件不可能创建。  值：0x01  
  
 `_A_SUBDIR`  
 子目录。  值：0x10  
  
 `_A_SYSTEM`  
 系统文件。  通常不会看到 DIR 命令，因此，除非使用 \/AS 选项。  值：0x04  
  
 多个常数可以组合使用或运算符 \(&#124;\)。  
  
## 请参阅  
 [文件名搜索函数](../c-runtime-library/filename-search-functions.md)   
 [全局常量](../c-runtime-library/global-constants.md)