---
title: "gmtime_s、_gmtime32_s、_gmtime64_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _gmtime32_s
- gmtime_s
- _gmtime64_s
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
- _gmtime_s
- gmtime64_s
- gmtime32_s
- _gmtime64_s
- gmtime_s
- _gmtime32_s
dev_langs: C++
helpviewer_keywords:
- gmtime_s function
- gmtime32_s function
- time functions
- gmtime64_s function
- _gmtime64_s function
- time structure conversion
- _gmtime_s function
- _gmtime32_s function
ms.assetid: 261c7df0-2b0c-44ba-ba61-cb83efaec60f
caps.latest.revision: "29"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f0d0fc911c052e58b1f2aeb9b656f737746bd2de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="gmtimes-gmtime32s-gmtime64s"></a>gmtime_s、_gmtime32_s、_gmtime64_s
将时间值转换为结构。 这些是具有安全增强功能的 [_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) 的版本，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 `_tm`  
 指向 `tm` 结构的指针。 返回的结构字段以 UTC 格式保留 `timer` 参数的计算值，而不是以本地时间格式进行保留。  
  
 `time`  
 指向存储时间的指针。 时间表示为自 1970 年 1 月 1 日午夜 (00:00:00)，协调世界时 (UTC) 以来所经过的秒数。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 0。 如果失败，则返回值为错误代码。 在 Errno.h 中定义了错误代码；有关这些错误的列表，请参阅 [errno](../../c-runtime-library/errno-constants.md)。  
  
### <a name="error-conditions"></a>错误条件  
  
|`_tm`|`time`|返回|`_tm` 中的值|  
|-----------|------------|------------|--------------------|  
|`NULL`|任何|`EINVAL`|未修改。|  
|非 `NULL`（指向有效内存）|`NULL`|`EINVAL`|所有字段都设置为 -1。|  
|非 `NULL`|< 0|`EINVAL`|所有字段都设置为 -1。|  
  
 对于前两种错误条件，都会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些功能将 `errno` 设置为 `EINVAL` 并返回 `EINVAL`。  
  
## <a name="remarks"></a>备注  
 `_gmtime32_s` 函数将分解 `time` 值并将其存储于在 Time.h 中定义的类型 `tm` 结构中。 结构地址将传入 `_tm` 中。 `time` 的值通常通过对 `time` 函数的调用来获取。  
  
> [!NOTE]
>  目标环境应尝试确定夏令时是否生效。 C 运行时库假设使用美国规则实现夏令时的计算。  
  
 每个结构字段的类型均为 `int`，如下表中所示。  
  
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
  
 使用 `__time64_t` 结构的 `_gmtime64_s` 允许日期最大表示为 3000 年 12 月 31 日 23:59:59，UTC；而 `gmtime32_s` 只能表示截至 2038 年 1 月 18 日 23:59:59，UTC 之前的日期。 1970 年 1 月 1 日午夜是这两个函数的日期范围下限。  
  
 `gmtime_s` 是计算出 `_gmtime64_s` 的内联函数，且 `time_t` 等同于 `__time64_t`。 如果需要强制编译器将 `time_t` 解释为旧的 32 位 `time_t`，你可以定义 `_USE_32BIT_TIME_T`。 执行此操作将导致 `gmtime_s` 内联到 `_gmtime32_s`。 不建议这样做，因为应用程序可能会在 2038 年 1 月 18 日后失效；且在 64 位平台上不允许使用它。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`gmtime_s`|\<time.h>|  
|`_gmtime32_s`|\<time.h>|  
|`_gmtime64_s`|\<time.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
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
Coordinated universal time is Fri Apr 25 20:12:33 2003  
```  
  
## <a name="see-also"></a>请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime_s、_wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime_s、_localtime32_s、_localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [_mkgmtime、_mkgmtime32、_mkgmtime64](../../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)   
 [mktime、_mktime32、_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)