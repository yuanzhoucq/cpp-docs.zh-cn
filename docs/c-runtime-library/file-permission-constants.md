---
title: "文件权限常量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_S_IWRITE"
  - "_S_IREAD"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_S_IREAD 常量"
  - "_S_IWRITE 常量"
  - "常量 [C++], 文件特性"
  - "文件权限 [C++]"
  - "S_IREAD 常量"
  - "S_IWRITE 常量"
ms.assetid: 593cad33-31d1-44d2-8941-8af7d210c88c
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 文件权限常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
#include <sys/stat.h>  
  
```  
  
## 备注  
 当`_O_CREAT` \(`_open`，`_sopen`\) 具体化时，需要一个这样的常量。  
  
 `pmode` 参数实现文件的权限设置。  
  
|常量|含义|  
|--------|--------|  
|`_S_IREAD`|允许读取。|  
|`_S_IWRITE`|允许写。|  
|`_S_IREAD`  &#124; `_S_IWRITE`|允许读取和写入。|  
  
 如果将 `pmode`用作 `_umask`的参数，清单常数可以设置权限集，如下所示。  
  
|常量|含义|  
|--------|--------|  
|`_S_IREAD`|不允许写入文件 \(文件只读\)|  
|`_S_IWRITE`|不允许读取 \(文件只写\)|  
|`_S_IREAD`  &#124; `_S_IWRITE`|允许读取和写入|  
  
## 请参阅  
 [\_open、\_wopen](../c-runtime-library/reference/open-wopen.md)   
 [\_sopen、\_wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [\_umask](../c-runtime-library/reference/umask.md)   
 [标准类型](../c-runtime-library/standard-types.md)   
 [全局常量](../c-runtime-library/global-constants.md)