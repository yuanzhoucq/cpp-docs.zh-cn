---
title: "_mkgmtime、_mkgmtime32、_mkgmtime64 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mkgmtime32
- _mkgmtime64
- _mkgmtime
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mkgmtime64
- mkgmtime32
- _mkgmtime32
- mkgmtime
- mkgmtime64
- _mkgmtime
dev_langs:
- C++
helpviewer_keywords:
- mkgmtime32 function
- time functions
- mkgmtime function
- _mkgmtime function
- converting times
- mkgmtime64 function
- _mkgmtime64 function
- _mkgmtime32 function
- time, converting
ms.assetid: b4ca2b67-e198-4f43-b3e2-e8ad6bd01867
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 7f73bffc2971b535f393cef7e0e2f957b01eee42
ms.contentlocale: zh-cn
ms.lasthandoff: 04/04/2017

---
# <a name="mkgmtime-mkgmtime32-mkgmtime64"></a>_mkgmtime、_mkgmtime32、_mkgmtime64
将由 `tm``struct` 表示的 UTC 时间转换为由 `time_t` 类型表示的 UTC 时间。  
  
## <a name="syntax"></a>语法  
  
```  
  
      time_t _mkgmtime(  
   struct tm* timeptr  
);  
__time32_t _mkgmtime32(  
   struct tm* timeptr  
);  
__time64_t _mkgmtime64(  
   struct tm* timeptr  
);  
```  
  
#### <a name="parameters"></a>参数  
 `timeptr`  
 指向 UTC 时间的指针作为要转换的 `struct``tm`。  
  
## <a name="return-value"></a>返回值  
 类型 `__time32_t` 或 `__time64_t` 的数量表示自协调世界时 (UTC) 1970 年 1 月 1 日午夜起经过的秒数。 如果日期超出范围 （请参阅备注部分） 或输入不能解释为有效的时间，则返回值为-1。  
  
## <a name="remarks"></a>备注  
 `_mkgmtime32` 和 `_mkgmtime64` 函数将 UTC 时间转换为表示 UTC 时间的 `__time32_t` 或 `__time64_t` 类型。 要将本地时间转换为 UTC 时间，请改用 `mktime`、`_mktime32` 和 `_mktime64`。  
  
 `_mkgmtime` 是计算出 `_mkgmtime64` 的内联函数，且 `time_t` 等同于 `__time64_t`。 如果需要强制编译器将 `time_t` 解释为旧的 32 位 `time_t`，你可以定义 `_USE_32BIT_TIME_T`。 不建议这样做，因为应用程序可能会在 2038 年 1 月 18 日后失效（32 位 `time_t` 的最大范围），并且 64 位平台上不允许此操作。  
  
 传入的时间结构将按照与 `_mktime` 函数相同的方式进行更改：根据 `tm_mday` 和 `tm_year` 的值将 `tm_wday` 和 `tm_yday` 字段设置为新值。 指定 `tm` 结构时间时，将 `tm_isdst` 字段设置为：  
  
-   零 (0)，指示标准时间有效。  
  
-   大于 0 的值，指示夏令时有效。  
  
-   小于零的值，使用 C 运行时库代码计算有效的是标准时间还是夏令时。  
  
 C 运行时库将使用 TZ 环境变量确定正确的夏令时。 如果未设置 TZ，将对操作系统进行查询以获取正确的区域夏令时行为。 `tm_isdst` 是必填字段。 如果未设置，则未定义其值，并且 `mktime` 的返回值不可预知。  
  
 `_mkgmtime32` 函数的范围为从 UTC 时间 1970 年 1 月 1 日午夜到 UTC 时间 2038 年 1 月 18 日 23:59:59。 `_mkgmtime64` 的范围为从 1970 年 1 月 1 日 (UTC) 午夜到 3000 年 12 月 31 日 23:59:59 (UTC)。 超出范围日期将导致返回值-1。 `_mkgmtime` 的范围取决于是否定义了 `_USE_32BIT_TIME_T`。 如果未定义，（默认）范围是 `_mkgmtime64` 的范围；否则，范围限于 `_mkgmtime32` 的 32 位范围。  
  
 注意，`gmtime` 和 `localtime` 将单个静态分配的缓冲区用于转换。 如果你为 `mkgmtime` 提供此缓冲区，则会损坏之前的内容。  
  
## <a name="example"></a>示例  
  
```  
// crt_mkgmtime.c  
#include <stdio.h>  
#include <time.h>  
  
int main()  
{  
    struct tm t1, t2;  
    time_t now, mytime, gmtime;  
    char buff[30];  
  
    time( & now );  
  
    _localtime64_s( &t1, &now );  
    _gmtime64_s( &t2, &now );  
  
    mytime = mktime(&t1);  
    gmtime = _mkgmtime(&t2);  
  
    printf("Seconds since midnight, January 1, 1970\n");  
    printf("My time: %I64d\nGM time (UTC): %I64d\n\n", mytime, gmtime);  
  
    /* Use asctime_s to display these times. */  
  
    _localtime64_s( &t1, &mytime );  
    asctime_s( buff, sizeof(buff), &t1 );  
    printf( "Local Time: %s\n", buff );  
  
    _gmtime64_s( &t2, &gmtime );  
    asctime_s( buff, sizeof(buff), &t2 );  
    printf( "Greenwich Mean Time: %s\n", buff );  
  
}  
```  
  
## <a name="sample-output"></a>示例输出  
  
```  
Seconds since midnight, January 1, 1970  
My time: 1171588492  
GM time (UTC): 1171588492  
  
Local Time: Thu Feb 15 17:14:52 2007  
  
Greenwich Mean Time: Fri Feb 16 01:14:52 2007  
```  
  
 以下示例显示如何使用一周中星期和一年中日期的计算值填充不完整的结构。  
  
```  
// crt_mkgmtime2.c  
#include <stdio.h>  
#include <time.h>  
#include <memory.h>  
  
int main()  
{  
    struct tm t1, t2;  
    time_t gmtime;  
    char buff[30];  
  
    memset(&t1, 0, sizeof(struct tm));  
    memset(&t2, 0, sizeof(struct tm));  
  
    t1.tm_mon = 1;  
    t1.tm_isdst = 0;  
    t1.tm_year = 103;  
    t1.tm_mday = 12;  
  
    // The day of the week and year will be incorrect in the output here.  
    asctime_s( buff, sizeof(buff), &t1);  
    printf("Before calling _mkgmtime, t1 = %s t.tm_yday = %d\n",  
            buff, t1.tm_yday );  
  
    gmtime = _mkgmtime(&t1);  
  
    // The correct day of the week and year were determined.  
    asctime_s( buff, sizeof(buff), &t1);  
    printf("After calling _mkgmtime, t1 = %s t.tm_yday = %d\n",  
            buff, t1.tm_yday );  
  
}  
```  
  
## <a name="output"></a>输出  
  
```  
Before calling _mkgmtime, t1 = Sun Feb 12 00:00:00 2003  
 t.tm_yday = 0  
After calling _mkgmtime, t1 = Wed Feb 12 00:00:00 2003  
 t.tm_yday = 42  
```  
  
## <a name="see-also"></a>另请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [asctime_s、_wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [gmtime_s、_gmtime32_s、_gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime_s、_localtime32_s、_localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [mktime、_mktime32、_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)
