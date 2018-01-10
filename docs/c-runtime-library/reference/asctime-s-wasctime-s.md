---
title: "asctime_s、_wasctime_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wasctime_s
- asctime_s
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
- asctime_s
- _wasctime_s
- _tasctime_s
dev_langs: C++
helpviewer_keywords:
- tasctime_s function
- _tasctime_s function
- time structure conversion
- wasctime_s function
- time, converting
- _wasctime_s function
- asctime_s function
ms.assetid: 17ad9b2b-a459-465d-976a-42822897688a
caps.latest.revision: "29"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 30a48101ea2db80f7c8a37434c1fd73c9c535286
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="asctimes-wasctimes"></a>asctime_s、_wasctime_s
将 `tm` 时间结构转换为字符串。 这些函数是 [asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t asctime_s(   
   char* buffer,  
   size_t numberOfElements,  
   const struct tm *_tm   
);  
errno_t _wasctime_s(   
   wchar_t* buffer,  
   size_t numberOfElements  
   const struct tm *_tm   
);  
template <size_t size>  
errno_t asctime_s(   
   char (&buffer)[size],  
   const struct tm *_tm   
); // C++ only  
template <size_t size>  
errno_t _wasctime_s(   
   wchar_t (&buffer)[size],  
   const struct tm *_tm   
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 `buffer`  
 [out] 指向缓冲区的指针，用于存储字符串结果。 此函数假定为指向有效内存位置的指针，大小由 `numberOfElements` 指定。  
  
 `numberOfElements`  
 [in] 用于存储结果的缓冲区的大小。  
  
 `_tm`  
 [in] 时间/日期结构。 此函数假定为指向有效 `struct tm` 对象的指针。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 0。 如果失败，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则返回值为错误代码。 错误代码是在 ERRNO.H 中定义的。 有关详细信息，请参阅 [errno 常量](../../c-runtime-library/errno-constants.md)。 针对每个错误条件返回的实际错误代码如下表所示。  
  
### <a name="error-conditions"></a>错误条件  
  
|`buffer`|`numberOfElements`|`tm`|返回|`buffer` 中的值|  
|--------------|------------------------|----------|------------|-----------------------|  
|`NULL`|任意|任意|`EINVAL`|未修改|  
|非 `NULL`（指向有效内存）|0|任意|`EINVAL`|未修改|  
|非 `NULL`|0< 大小 < 26|任意|`EINVAL`|空字符串|  
|非 `NULL`|>= 26|`NULL`|`EINVAL`|空字符串|  
|非 `NULL`|>= 26|无效的时间结构或超出时间组件值范围|`EINVAL`|空字符串|  
  
> [!NOTE]
>  `wasctime_s` 的错误条件类似于 `asctime_s`，但大小限制以字数测量。  
  
## <a name="remarks"></a>备注  
 `asctime` 函数将存储为结构的时间转换为字符串。 `_tm` 值通常通过调用 `gmtime` 或 `localtime` 获取。 这两个函数都可以用于填充 `tm` 结构，如 TIME.H 中的定义。  
  
|timeptr 成员|“值”|  
|--------------------|-----------|  
|`tm_hour`|小时，自午夜 (0-23)|  
|`tm_isdst`|如果夏令时生效，则为正；如果夏令时不生效，则为 0；如果夏令时状态未知，则为负。 C 运行时库假设使用美国规则实现夏令时 (DST) 的计算。|  
|`tm_mday`|月 (1-31) 天|  
|`tm_min`|分钟后小时 (0-59)|  
|`tm_mon`|月 (0-11;年 1 月 = 0）|  
|`tm_sec`|分钟 (0-59) 之后的秒|  
|`tm_wday`|周的天 (0-6;星期日 = 0）|  
|`tm_yday`|年份 (0-365; 天1 月 1 日 = 0)|  
|`tm_year`|年（当前年份减去 1900）|  
  
 转换的字符串同时根据本地时区设置进行调整。 有关配置本地时间的信息，请参阅 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md) 和 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md) 以及 [localtime_s、_localtime32_s、_localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md) 函数，有关定义时区环境和全局变量的信息，请参阅 [_tzset](../../c-runtime-library/reference/tzset.md) 函数。  
  
 `asctime_s` 生成的字符串结果正好包含 26 个字符，格式为 `Wed Jan 02 02:03:55 1980\n\0`。 使用 24 小时制。 所有字段都具有固定宽度。 换行符和空字符占据字符串的最后两个位置。 作为第二个参数传入的值应该至少应是此大小。 如果是更小的值，将返回错误代码 `EINVAL`。  
  
 `_wasctime_s` 是 `asctime_s` 的宽字符版本。 除此以外，`_wasctime_s` 和 `asctime_s` 的行为完全相同。  
  
### <a name="generic-text-routine-mapping"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tasctime_s`|`asctime_s`|`asctime_s`|`_wasctime_s`|  
  
 在 C++ 中，通过模板重载简化这些函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`asctime_s`|\<time.h>|  
|`_wasctime_s`|\<time.h> 或 \<wchar.h>|  
  
## <a name="security"></a>安全性  
 如果缓冲区指针不是 `NULL`，并且指针不指向有效的缓冲区，函数将覆盖该位置处的全部内容。 该操作还将导致访问冲突。  
  
 如果传入的大小参数大于缓冲区的实际大小，则可能会发生[缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
## <a name="example"></a>示例  
 此程序以长整型 `aclock` 格式进行系统时间设置，将其转换为 `newtime` 结构，然后使用 `asctime_s` 函数将其转换为字符串形式以进行输出。  
  
```  
// crt_asctime_s.c  
#include <time.h>  
#include <stdio.h>  
  
struct tm newtime;  
__time32_t aclock;  
  
int main( void )  
{  
   char buffer[32];  
   errno_t errNum;  
   _time32( &aclock );   // Get time in seconds.  
   _localtime32_s( &newtime, &aclock );   // Convert time to struct tm form.  
  
   // Print local time as a string.  
  
   errNum = asctime_s(buffer, 32, &newtime);  
   if (errNum)  
   {  
       printf("Error code: %d", (int)errNum);  
       return 1;  
   }  
   printf( "Current date and time: %s", buffer );  
   return 0;  
}  
```  
  
```Output  
Current date and time: Wed May 14 15:30:17 2003  
```  
  
## <a name="see-also"></a>请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime_s、_gmtime32_s、_gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime_s、_localtime32_s、_localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset](../../c-runtime-library/reference/tzset.md)