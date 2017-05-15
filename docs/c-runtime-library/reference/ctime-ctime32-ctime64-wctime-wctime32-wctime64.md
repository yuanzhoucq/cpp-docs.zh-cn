---
title: "ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ctime64
- _wctime32
- ctime
- _wctime64
- _ctime32
- _wctime
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
- _wctime64
- _ctime32
- _tctime
- _wctime
- _wctime32
- _tctime64
- _ctime64
- ctime
dev_langs:
- C++
helpviewer_keywords:
- tctime64 function
- _ctime32 function
- ctime32 function
- _wctime function
- wctime64 function
- _tctime64 function
- _tctime32 function
- _ctime64 function
- _wctime64 function
- ctime function
- wctime32 function
- ctime64 function
- _wctime32 function
- _tctime function
- tctime32 function
- tctime function
- wctime function
- time, converting
ms.assetid: 2423de37-a35c-4f0a-a378-3116bc120a9d
caps.latest.revision: 25
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: f3d756cec6d9482cfabcbc2a336cbf5d6381a97a
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="ctime-ctime32-ctime64-wctime-wctime32-wctime64"></a>ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64
将时间值转换为字符串，并调整本地时区设置。 提供这些函数的更安全版本；请参阅 [ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
char *ctime(   
   const time_t *timer   
);  
char *_ctime32(   
   const __time32_t *timer )  
;  
char *_ctime64(   
   const __time64_t *timer )  
;  
wchar_t *_wctime(   
   const time_t *timer   
);  
wchar_t *_wctime32(   
   const __time32_t *timer  
);  
wchar_t *_wctime64(   
   const __time64_t *timer   
);  
```  
  
#### <a name="parameters"></a>参数  
 `timer`  
 指向存储时间的指针。  
  
## <a name="return-value"></a>返回值  
 指向字符串结果的指针。 如果出现以下情况，则返回 `NULL`：  
  
-   `time` 表示 1970 年 1 月 1 日午夜前的日期（UTC 时间）。  
  
-   如果使用 `_ctime32` 或 `_wctime32`，且 `time` 表示 2038 年 1 月 18 日 23:59:59 后的日期（UTC 时间）。  
  
-   如果使用 `_ctime64` 或 `_wctime64`，且 `time` 表示 3000 年 12 月 31 日 23:59:59 后的日期（UTC 时间）。  
  
 `ctime` 是计算出 `_ctime64` 的内联函数，且 `time_t` 等同于 `__time64_t`。 如果需要强制编译器将 `time_t` 解释为旧的 32 位 `time_t`，则可以定义 `_USE_32BIT_TIME_T`。 执行此操作将导致 `ctime` 计算出 `_ctime32`。 不建议这样做，因为应用程序可能会在 2038 年 1 月 18 日后失效；且在 64 位平台上不允许使用它。  
  
## <a name="remarks"></a>备注  
 `ctime` 函数将存储为 [time_t](../../c-runtime-library/standard-types.md) 值的时间值转换为字符串。 通常情况下，通过对 [time](../../c-runtime-library/reference/time-time32-time64.md) 的调用获取 `timer` 值，它返回自协调世界时 (UTC) 1970 年 1 月 1 日午夜 (00:00:00) 以来经过的秒数。 返回值字符串正好包含 26 个字符，且格式为：  
  
```  
Wed Jan 02 02:03:55 1980\n\0  
```  
  
 使用 24 小时制。 所有字段都具有固定宽度。 换行符 ('\n') 和空字符 ('\0') 占据字符串的最后两个位置。  
  
 转换的字符串同时根据本地时区设置进行调整。 有关配置本地时间的信息，请参阅 `time`、[_ftime](../../c-runtime-library/reference/ftime-ftime32-ftime64.md) 和 [localtime](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) 函数，有关定义时区环境和全局变量的详细信息，请参阅 [_tzset](../../c-runtime-library/reference/tzset.md) 函数。  
  
 调用 `ctime` 会修改由 `gmtime` 和 `localtime` 函数使用的单个静态分配的缓冲区。 每次调用其中一个例程都会破坏上一次调用的结果。 `ctime` 与 `asctime` 函数共享静态缓冲区。 因此，调用 `ctime` 会破坏任何上一次调用 `asctime`、`localtime` 或 `gmtime` 的结果。  
  
 `_wctime` 和 `_wctime64` 是 `ctime` 和 `_ctime64` 的宽字符版本；返回指向宽字符串的指针。 否则，`_ctime64`、`_wctime` 和 `_wctime64` 的行为与 `ctime` 完全相同。  
  
 这些函数验证其参数。 如果 `timer` 为空指针，或 timer 值为负值，这些函数将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数返回 `NULL`，并且将 `errno` 设置为 `EINVAL`。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tctime`|`ctime`|`ctime`|`_wctime`|  
|`_tctime32`|`_ctime32`|`_ctime32`|`_wctime32`|  
|`_tctime64`|`_ctime64`|`_ctime64`|`_wctime64`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`ctime`|\<time.h>|  
|`_ctime32`|\<time.h>|  
|`_ctime64`|\<time.h>|  
|`_wctime`|\<time.h> 或 \<wchar.h>|  
|`_wctime32`|\<time.h> 或 \<wchar.h>|  
|`_wctime64`|\<time.h> 或 \<wchar.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_ctime64.c  
// compile with: /W3  
/* This program gets the current  
 * time in _time64_t form, then uses ctime to  
 * display the time in string form.  
 */  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
   __time64_t ltime;  
  
   _time64( &ltime );  
   printf( "The time is %s\n", _ctime64( &ltime ) ); // C4996  
   // Note: _ctime64 is deprecated; consider using _ctime64_s  
}  
```  
  
```Output  
The time is Wed Feb 13 16:04:43 2002  
```  
  
## <a name="see-also"></a>另请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)
