---
title: "gmtime、_gmtime32、_gmtime64 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _gmtime32
- gmtime
- _gmtime64
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
- gmtime
- _gmtime32
- _gmtime64
dev_langs: C++
helpviewer_keywords:
- gmtime32 function
- _gmtime64 function
- gmtime function
- time functions
- _gmtime32 function
- gmtime64 function
- time structure conversion
ms.assetid: 315501f3-477e-475d-a414-ef100ee0db27
caps.latest.revision: "30"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 78213f97021ad1e7c89d5dfde6c1cea8b6e12a7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="gmtime-gmtime32-gmtime64"></a>gmtime、_gmtime32、_gmtime64
将时间值转换为结构。 提供这些函数的更安全版本；请参阅 [gmtime_s、_gmtime32_s、_gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
struct tm *gmtime(   
   const time_t *timer   
);  
struct tm *_gmtime32(   
   const __time32_t *timer   
);  
struct tm *_gmtime64(   
   const __time64_t *timer   
);  
```  
  
#### <a name="parameters"></a>参数  
 `timer`  
 指向存储时间的指针。 时间表示为自 1970 年 1 月 1 日午夜 (00:00:00)，协调世界时 (UTC) 以来所经过的秒数。  
  
## <a name="return-value"></a>返回值  
 指向类型 [tm](../../c-runtime-library/standard-types.md) 的结构的指针。 返回的结构字段以 UTC 格式保留 `timer` 参数的计算值，而不是以本地时间格式进行保留。 每个结构字段的类型均为 `int`，如下所示：  
  
 `tm_sec`  
 分钟之后的秒 (0-59)。  
  
 `tm_min`  
 分钟后小时 (0-59)。  
  
 `tm_hour`  
 小时，自午夜 (0-23)。  
  
 `tm_mday`  
 某一天的月份 (1-31)。  
  
 `tm_mon`  
 月 (0-11;年 1 月 = 0）。  
  
 `tm_year`  
 年（当前年份减去 1900）。  
  
 `tm_wday`  
 星期几 (0-6;星期日 = 0）。  
  
 `tm_yday`  
 年的某一天 (0-365;1 月 1 日 = 0)。  
  
 `tm_isdst`  
 `gmtime` 始终为 0。  
  
 `gmtime`、`mktime`、`mkgmtime` 和 `localtime` 的 32 位和 64 位版本均为每个线程使用一个常用的 `tm` 结构以进行转换。 对这些函数的每次调用都会破坏以前调用的结果。 如果 `timer` 表示 1970 年 1 月 1 日午夜前的日期，则 `gmtime` 返回 `NULL`。 无错误返回。  
  
 使用 `__time64_t` 结构的 `_gmtime64` 允许日期最大表示为 3000 年 12 月 31 日 23:59:59，UTC；而 `_gmtime32` 只能表示截至 2038 年 1 月 18 日 23:59:59，UTC 之前的日期。 1970 年 1 月 1 日午夜是这两个函数的日期范围下限。  
  
 `gmtime` 是计算出 `_gmtime64` 的内联函数，且 `time_t` 等同于 `__time64_t`，除非定义了 `_USE_32BIT_TIME_T`。 如果必须强制编译器将 `time_t` 解释为旧的 32 位 `time_t`，则可以定义 `_USE_32BIT_TIME_T`，但执行此操作会导致将 `gmtime` 内联到 `_gmtime32` 并将 `time_t` 定义为 `__time32_t`。 我们建议，不执行上述操作，因为 64 位平台上不允许使用它，并且应用程序会在 2038 年 1 月 18 日之后失效。  
  
 这些函数验证其参数。 如果 `timer` 为空指针，或计时器值为负值，这些函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数返回 `NULL`，并且将 `errno` 设置为 `EINVAL`。  
  
## <a name="remarks"></a>备注  
 `_gmtime32` 函数将分解 `timer` 值并将其存储于在 TIME.H 中定义的类型 `tm` 的静态分配结构中。 `timer` 的值往往通过对 `time` 函数的调用来获取。  
  
> [!NOTE]
>  在大多数情况下，目标环境尝试确定夏令时是否生效。 C 运行时库假设使用美国规则实现夏令时 (DST) 的计算。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`gmtime`|\<time.h>|  
|`_gmtime32`|\<time.h>|  
|`_gmtime64`|\<time.h>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```C  
// crt_gmtime.c  
// compile with: /W3  
// This program uses _gmtime64 to convert a long-  
// integer representation of coordinated universal time  
// to a structure named newtime, then uses asctime to  
// convert this structure to an output string.  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
   struct tm *newtime;  
   __int64 ltime;  
   char buff[80];  
  
   _time64( &ltime );  
  
   // Obtain coordinated universal time:  
   newtime = _gmtime64( &ltime ); // C4996  
   // Note: _gmtime64 is deprecated; consider using _gmtime64_s  
   asctime_s( buff, sizeof(buff), newtime );  
   printf( "Coordinated universal time is %s\n", buff );  
}  
```  
  
```Output  
Coordinated universal time is Tue Feb 12 23:11:31 2002  
```  
  
## <a name="see-also"></a>请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime_s、_gmtime32_s、_gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [_mkgmtime、_mkgmtime32、_mkgmtime64](../../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)   
 [mktime、_mktime32、_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)