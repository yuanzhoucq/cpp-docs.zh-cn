---
title: "文件常量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_O_EXCL"
  - "_O_RDWR"
  - "_O_APPEND"
  - "_O_RDONLY"
  - "_O_TRUNC"
  - "_O_CREAT"
  - "_O_WRONLY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_O_APPEND 常量"
  - "_O_CREAT 常量"
  - "_O_EXCL 常量"
  - "_O_RDONLY 常量"
  - "_O_RDWR 常量"
  - "_O_TRUNC 常量"
  - "_O_WRONLY 常量"
  - "O_APPEND 常量"
  - "O_CREAT 常量"
  - "O_EXCL 常量"
  - "O_RDONLY 常量"
  - "O_RDWR 常量"
  - "O_TRUNC 常量"
  - "O_WRONLY 常量"
ms.assetid: c8fa5548-9ac2-4217-801d-eb45e86f2fa4
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 文件常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
#include <fcntl.h>  
  
```  
  
## 备注  
 从一个或多个窗体的整数表达式这些常量确定读取或编写操作类型允许的。  它是通过组合一个或更多常数窗体具有特定模式的常数。  
  
 常数文件如下：  
  
 `_O_APPEND`  
 重新定位文件指针到文件尾在每次写入操作之前。  
  
 `_O_CREAT`  
 创建并打开要编写的文件；如果 *文件名* 指定的文件存在，这不起作用。  
  
 `_O_EXCL`  
 如果 *文件名* 指定的文件存在，则返回 false。  只当使用 `_O_CREAT` 时使用。  
  
 `_O_RDONLY`  
 只读打开的文件如果指定此标志，则可以为 `_O_RDWR` 或 `_O_WRONLY` 。  
  
 `_O_RDWR`  
 读取和写入的文件；打开如果指定此标志，则可以为 `_O_RDONLY` 或 `_O_WRONLY` 。  
  
 `_O_TRUNC`  
 打开和截断现有文件；长为零文件必须具有写入权限。  销毁文件的内容。  如果指定此标志，则不能指定 `_O_RDONLY`。  
  
 `_O_WRONLY`  
 只读打开的文件如果指定此标志，则可以为  `_O_RDONLY` 或 `_O_RDWR` 。  
  
## 请参阅  
 [\_open、\_wopen](../c-runtime-library/reference/open-wopen.md)   
 [\_sopen、\_wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [全局常量](../c-runtime-library/global-constants.md)