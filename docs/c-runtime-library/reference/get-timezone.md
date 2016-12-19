---
title: "_get_timezone | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_get_timezone"
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
  - "_get_timezone"
  - "get_timezone"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "时区"
  - "get_timezone 函数"
  - "_get_timezone 函数"
ms.assetid: 30ab0838-0ae9-4a2f-bfe6-a49ee443b21e
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _get_timezone
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索协调世界时间 \(UTC\) 和当地时间之间的秒的差异。  
  
## 语法  
  
```  
  
      error_t _get_timezone(   
    long* seconds  
);  
```  
  
#### 参数  
 `seconds`  
 区别在于 UTC 和本地时间之间的秒数。  
  
## 返回值  
 如果成功的话为零，或者如果出错为`errno` 值。  
  
## 备注  
 `_get_timezone` 函数检索UTC 与本地时间之间的秒数，将其格式化为整数。  默认值是 28,800 秒，基于太平洋标准时间 \(晚于 UTC 8小时。\)  
  
 如果 `seconds` 是 `NULL`，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许执行继续，则该函数设置 `errno` 为 `EINVAL` 并返回 `EINVAL`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_get_timezone`|\<time.h\>|  
  
 有关详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)   
 [\_get\_daylight](../../c-runtime-library/reference/get-daylight.md)   
 [\_get\_dstbias](../../c-runtime-library/reference/get-dstbias.md)   
 [\_get\_tzname](../../c-runtime-library/reference/get-tzname.md)