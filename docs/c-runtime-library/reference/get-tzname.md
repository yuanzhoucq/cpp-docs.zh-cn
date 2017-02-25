---
title: "_get_tzname | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_get_tzname"
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
  - "_get_tzname"
  - "get_tzname"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_get_tzname 函数"
  - "get_tzname 函数"
  - "时区"
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# _get_tzname
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索该时区标准时区的夏时制名称或名称 \(DST\) 的字符串表示形式。  
  
## 语法  
  
```  
errno_t _get_tzname(  
    size_t* pReturnValue,  
    char* timeZoneName,  
    size_t sizeInBytes,  
    int index      
);  
```  
  
#### 参数  
 \[out\] `pReturnValue`  
 字符串长度 `timeZoneName` 包括一个 NULL 终结器。  
  
 \[out\] `timeZoneName`  
 字符串的地址时区标准时区的夏时制名称或名称 \(DST\) 的表示的，具体取决于 `index`。  
  
 \[in\] `sizeInBytes`  
 `timeZoneName` 字符串的大小（单位为字节）。  
  
 \[in\] `index`  
 索引检索的两个时区名称之一。  
  
## 返回值  
 如果成功则为0，否则为 `errno` 类型值。  
  
 如果或 `timeZoneName` 为 `NULL`，或其 `sizeInBytes` 为零或小于零 \(0\)，但不能两者\)，的参数无效处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则该函数设置 `errno` 为 `EINVAL` 并返回 `EINVAL`。  
  
### 错误情况  
  
|`pReturnValue`|`timeZoneName`|`sizeInBytes`|`index`|返回值|`timeZoneName` 的内容|  
|--------------------|--------------------|-------------------|-------------|---------|------------------------|  
|TZ 的名称范围|`NULL`|0|0 或 1|0|未修改|  
|TZ 的名称范围|any|\> 0|0 或 1|0|TZ 命名|  
|未修改|`NULL`|\> 0|any|`EINVAL`|未修改|  
|未修改|any|零|any|`EINVAL`|未修改|  
|未修改|any|\> 0|\> 1|`EINVAL`|未修改|  
  
## 备注  
 `_get_tzname` 函数检索该时区标准时区的夏时制名称或名称 \(DST\) 的字符串表示为根据索引，以及字符串的 `timeZoneName` 地址的范围在 `pReturnValue`中。  如果 `timeZoneName` 为 `NULL`，且 `sizeInBytes` 为零，任意时区字符串的大小 \(以字节为单位\) 返回到 `pReturnValue`中。  索引必须是 0 或 1 标准时区的夏时制标准时区的；其他所有值索引具有不确定的结果。  
  
### 索引  
  
|`index`|`timeZoneName` 的内容|默认值 \= `timeZoneName`。|  
|-------------|------------------------|----------------------------|  
|0|时区名称|"PST"|  
|1|获取标准时区名称。|"PDT"|  
|\> 1 or \< 0|将 `errno` 设置为 `EINVAL`。|未修改|  
  
 在运行时显式更改，除非该值，则默认值分别为“PST”和“PDT”。这些字符数组的大小由 `TZNAME_MAX` 管理值。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_get_tzname`|\<time.h\>|  
  
 有关详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)   
 [\_get\_daylight](../../c-runtime-library/reference/get-daylight.md)   
 [\_get\_dstbias](../../c-runtime-library/reference/get-dstbias.md)   
 [\_get\_timezone](../../c-runtime-library/reference/get-timezone.md)   
 [TZNAME\_MAX](../../c-runtime-library/tzname-max.md)