---
title: "共享常量 | Microsoft Docs"
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
  - "_SH_DENYNO"
  - "_SH_DENYRD"
  - "_SH_DENYRW"
  - "_SH_DENYWR"
  - "_SH_COMPAT"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_SH_COMPAT 常量"
  - "_SH_DENYNO 常量"
  - "_SH_DENYRD 常量"
  - "_SH_DENYRW 常量"
  - "_SH_DENYWR 常量"
  - "SH_COMPAT 常量"
  - "SH_DENYNO 常量"
  - "SH_DENYRD 常量"
  - "SH_DENYRW 常量"
  - "SH_DENYWR 常量"
  - "共享常量"
ms.assetid: 95fadc3a-55dc-473d-98b5-e8211900465d
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 共享常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文件共享的常数模式。  
  
## 语法  
  
```  
  
#include <share.h>  
  
```  
  
## 备注  
 *shflag* 参数决定共享模式，包括一个或多个清单常数。  这些结合使用 *oflag* 参数 \(参见 [文件常数](../c-runtime-library/file-constants.md)\)。  
  
 下表列出常数及其含义：  
  
|常量|含义|  
|--------|--------|  
|`_SH_DENYRW`|拒绝对文件的读访问和写访问|  
|`_SH_DENYWR`|拒绝对文件的写访问|  
|`_SH_DENYRD`|拒绝对文件的读访问|  
|`_SH_DENYNO`|允许读写访问权限|  
|`_SH_SECURE`|设置安全模式 \(共享读取，独占写访问权限\)。|  
  
## 请参阅  
 [\_sopen、\_wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [\_fsopen、\_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [全局常量](../c-runtime-library/global-constants.md)