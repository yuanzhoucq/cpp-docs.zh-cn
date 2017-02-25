---
title: "_stat 结构 st_mode 字段常量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "S_IFCHR"
  - "S_IFDIR"
  - "_S_IWRITE"
  - "S_IFMT"
  - "_S_IFDIR"
  - "_S_IREAD"
  - "S_IEXEC"
  - "_S_IEXEC"
  - "_S_IFMT"
  - "S_IWRITE"
  - "S_IFREG"
  - "S_IREAD"
  - "_S_IFCHR"
  - "_S_IFREG"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_S_IEXEC 常量"
  - "_S_IFCHR 常量"
  - "_S_IFDIR 常量"
  - "_S_IFMT 常量"
  - "_S_IFREG 常量"
  - "_S_IREAD 常量"
  - "_S_IWRITE 常量"
  - "S_IEXEC 常量"
  - "S_IFCHR 常量"
  - "S_IFDIR 常量"
  - "S_IFMT 常量"
  - "S_IFREG 常量"
  - "S_IREAD 常量"
  - "S_IWRITE 常量"
  - "st_mode 字段常量"
  - "stat 结构"
  - "stat 结构, 常量"
ms.assetid: fd462004-7563-4766-8443-30b0a86174b6
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# _stat 结构 st_mode 字段常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
#include <sys/stat.h>  
  
```  
  
## 备注  
 这些常量可以在 [\_stat structure](../c-runtime-library/standard-types.md)的 **st\_mode** 字段用于表示文件类型。  
  
 位屏蔽常数介绍如下：  
  
|常量|含义|  
|--------|--------|  
|`_S_IFMT`|文件类型掩码|  
|`_S_IFDIR`|目录|  
|`_S_IFCHR`|特殊字符 \(如果集，指示设备\)|  
|`_S_IFREG`|规则|  
|`_S_IREAD`|读取权限，所有者|  
|`_S_IWRITE`|写入权限，所有者|  
|`_S_IEXEC`|执行\/搜索权限，所有者|  
  
## 请参阅  
 [\_stat、\_wstat 函数](../c-runtime-library/reference/stat-functions.md)   
 [\_fstat、\_fstat32、\_fstat64、\_fstati64、\_fstat32i64、\_fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [标准类型](../c-runtime-library/standard-types.md)   
 [全局常量](../c-runtime-library/global-constants.md)