---
title: "_set_doserrno | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_doserrno"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_set_doserrno"
  - "set_doserrno"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_doserrno 全局变量"
  - "_set_doserrno 函数"
  - "doserrno 全局变量"
  - "set_doserrno 函数"
ms.assetid: 8686c159-3797-4705-a53e-7457869ca6f3
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _set_doserrno
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置 [\_doserrno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 的全局变量的值。  
  
## 语法  
  
```  
errno_t _set_doserrno(   
   int value   
);  
```  
  
#### 参数  
 \[in\] `value`  
 `_doserrno` 的新值。  
  
## 返回值  
 如果成功则返回 0。  
  
## 备注  
 可能的值在Errno.h 中定义。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_set_doserrno`|\<stdlib.h\>|\<errno.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [\_get\_doserrno](../../c-runtime-library/reference/get-doserrno.md)   
 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)