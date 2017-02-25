---
title: "_get_daylight | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__daylight"
  - "_get_daylight"
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
  - "api-ms-win-crt-time-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "get_daylight"
  - "_get_daylight"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_get_daylight 函数"
  - "夏时制偏移量"
  - "get_daylight 函数"
ms.assetid: f85a6ba3-e187-4ca7-aed7-ffc694c8ac4c
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _get_daylight
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索夏令时偏移量（以小时为单位）。  
  
## 语法  
  
```  
  
error_t _get_daylight(      int* hours );  
```  
  
#### 参数  
 `hours`  
 夏令时偏移量（以小时为单位）。  
  
## 返回值  
 如果成功，则为零；如果发生错误，则为 `errno` 值。  
  
## 备注  
 `_get_daylight` 函数将夏令时中的小时数作为整数进行检索。  如果夏令时有效，则默认偏移量为一小时（但是少数地区遵守两小时的偏移量）。  
  
 如果 `hours` 为 `NULL`，则调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许执行继续，则该函数将 `errno` 设置为 `EINVAL` 并返回 `EINVAL`。  
  
 我们建议你使用此函数，而非 `_daylight` 宏或已弃用的 `__daylight` 函数。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_get_daylight`|\<time.h\>|  
  
 有关详细信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)   
 [\_get\_dstbias](../../c-runtime-library/reference/get-dstbias.md)   
 [\_get\_timezone](../../c-runtime-library/reference/get-timezone.md)   
 [\_get\_tzname](../../c-runtime-library/reference/get-tzname.md)