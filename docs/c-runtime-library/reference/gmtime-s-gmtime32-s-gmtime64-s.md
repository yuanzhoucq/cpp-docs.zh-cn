---
title: "gmtime_s、_gmtime32_s、_gmtime64_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_gmtime32_s"
  - "gmtime_s"
  - "_gmtime64_s"
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
  - "_gmtime_s"
  - "gmtime64_s"
  - "gmtime32_s"
  - "_gmtime64_s"
  - "gmtime_s"
  - "_gmtime32_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "gmtime_s 函数"
  - "gmtime32_s 函数"
  - "时间函数"
  - "gmtime64_s 函数"
  - "_gmtime64_s 函数"
  - "时间结构转换"
  - "_gmtime_s 函数"
  - "_gmtime32_s 函数"
ms.assetid: 261c7df0-2b0c-44ba-ba61-cb83efaec60f
caps.latest.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 29
---
# gmtime_s、_gmtime32_s、_gmtime64_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将时间值转换为一种结构。 一些版本 [\_gmtime32、 \_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) 因安全性增强中所述 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)。  
  
## 语法  
  
```  
errno_t gmtime_s(  
   struct tm* _tm,  
   const __time_t* time  
);  
errno_t _gmtime32_s(  
   struct tm* _tm,  
   const __time32_t* time  
);  
errno_t _gmtime64_s(  
   struct tm* _tm,  
   const __time64_t* time   
);  
```  
  
#### 参数  
 `_tm`  
 指向 `tm` 结构。 返回的结构字段存储的计算结果的值 `timer` 参数以 utc 为单位，而不是以本地时间。  
  
 `time`  
 指针，指向存储的时间。 因为自午夜以来经过的秒为单位表示的时间 \(00: 00:00\)、 1970 年 1 月 1 日，格式为协调世界时 \(UTC\)。  
  
## 返回值  
 如果成功，则为零。 如果失败，返回值将是错误代码。 错误代码被在 Errno.h;有关这些错误的列表，请参阅 [errno](../../c-runtime-library/errno-constants.md)。  
  
### 错误条件  
  
|`_tm`|`time`|返回|中的值 `_tm`|  
|-----------|------------|--------|---------------|  
|`NULL`|any|`EINVAL`|不会修改。|  
|不 `NULL` （指向有效内存）|`NULL`|`EINVAL`|所有字段都设置为\-1。|  
|不 `NULL`|\< 0|`EINVAL`|所有字段都设置为\-1。|  
  
 对于第一个的两个错误条件，无效参数处理程序将调用，如中所述 [参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些功能将 `errno` 设置为 `EINVAL` 并返回 `EINVAL`。  
  
## 备注  
 `_gmtime32_s` 函数将分解 `time` 值并将其存储在类型的结构 `tm`, 在 Time.h 中定义。 将传入该结构的地址 `_tm`。 值 `time` 通常通过调用中获取 `time` 函数。  
  
> [!NOTE]
>  目标环境应尝试确定夏时制时间是否有效。 C 运行库假定用于实现夏令时计算的美国规则。  
  
 每个结构字段的类型是 `int`, 下, 表中所示。  
  
 `tm_sec`  
 分钟后的几秒 \(0\-59\)。  
  
 `tm_min`  
 小时后的分钟 \(0\-59\)。  
  
 `tm_hour`  
 午夜算起的小时 \(0\-23\)。  
  
 `tm_mday`  
 月 \(1\-31\) 天。  
  
 `tm_mon`  
 月 \(0 – 11;年 1 月 \= 0）。  
  
 `tm_year`  
 年份 （当前年份减去 1900年）。  
  
 `tm_wday`  
 星期几 \(0 – 6;星期日 \= 0）。  
  
 `tm_yday`  
 每年的一天 \(0\-365;1 月 1 日 \= 0\)。  
  
 `tm_isdst`  
 始终为 0 的 `gmtime`。  
  
 `_gmtime64_s`, 它使用 `__time64_t` 结构，请允许通过 23:59:59，3000 年 12 月 31 日，UTC; 向上表示的日期值，而 `gmtime32_s` 仅表示 23:59:59 2038 年 1 月 18 日，UTC 日期。 午夜 1970 年 1 月 1 日是这两个这些函数的日期范围的下限。  
  
 `gmtime_s` 是一个内联函数，其计算结果为 `_gmtime64_s` 和 `time_t` 等同于 `__time64_t`。 如果需要强制编译器将 `time_t` 解释为旧的 32 位 `time_t`，你可以定义 `_USE_32BIT_TIME_T`。 这样做，这将导致 `gmtime_s` 要内联到 `_gmtime32_s`。 这不是建议的因为您的应用程序可能会失败后 2038 年 1 月 18 日，并且不允许在 64 位平台上。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`gmtime_s`|\<time.h\>|  
|`_gmtime32_s`|\<time.h\>|  
|`_gmtime64_s`|\<time.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_gmtime64_s.c  
// This program uses _gmtime64_s to convert a 64-bit  
// integer representation of coordinated universal time  
// to a structure named newtime, then uses asctime_s to  
// convert this structure to an output string.  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
   struct tm newtime;  
   __int64 ltime;  
   char buf[26];  
   errno_t err;  
  
   _time64( &ltime );  
  
   // Obtain coordinated universal time:   
   err = _gmtime64_s( &newtime, &ltime );  
   if (err)  
   {  
      printf("Invalid Argument to _gmtime64_s.");  
   }  
  
   // Convert to an ASCII representation   
   err = asctime_s(buf, 26, &newtime);  
   if (err)  
   {  
      printf("Invalid Argument to asctime_s.");  
   }  
  
   printf( "Coordinated universal time is %s\n",   
           buf );  
}  
```  
  
```Output  
格式为协调通用时间是星期五 Apr 25 20:12:33 2003年  
```  
  
## .NET Framework 等效项  
  
-   [System::DateTime::UtcNow](https://msdn.microsoft.com/en-us/library/system.datetime.utcnow.aspx)  
  
-   [System::DateTime::ToUniversalTime](https://msdn.microsoft.com/en-us/library/system.datetime.touniversaltime.aspx)  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime\_s、\_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime\_s, \_localtime32\_s, \_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [\_mkgmtime、\_mkgmtime32、\_mkgmtime64](../../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)   
 [mktime、\_mktime32、\_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)