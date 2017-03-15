---
title: "fseek、_lseek 常量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SEEK_END"
  - "SEEK_SET"
  - "SEEK_CUR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SEEK_CUR 常量"
  - "SEEK_END 常量"
  - "SEEK_SET 常量"
ms.assetid: 9deeb13e-5aa3-4c33-80d8-721c80a4de9d
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# fseek、_lseek 常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
#include <stdio.h>  
  
```  
  
## 备注  
 *原点* 参数指定初始位置，并且可以是下面显示的常数之一：  
  
|常量|含义|  
|--------|--------|  
|`SEEK_END`|文件结尾|  
|`SEEK_CUR`|文件指针的当前位置。|  
|`SEEK_SET`|文件开头|  
  
## 请参阅  
 [fseek、\_fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)   
 [\_lseek、\_lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)   
 [全局常量](../c-runtime-library/global-constants.md)