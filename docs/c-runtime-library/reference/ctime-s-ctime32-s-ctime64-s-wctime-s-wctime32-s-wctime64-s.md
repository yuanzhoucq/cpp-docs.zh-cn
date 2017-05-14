---
title: "ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ctime64_s
- _wctime32_s
- ctime_s
- _wctime64_s
- _ctime32_s
- _wctime_s
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
- ctime64_s
- _ctime32_s
- _tctime32_s
- _ctime64_s
- _wctime_s
- _tctime_s
- _tctime64_s
- ctime_s
- ctime32_s
dev_langs:
- C++
helpviewer_keywords:
- _wctime32_s function
- ctime64_s function
- _tctime64_s function
- _wctime_s function
- tctime_s function
- _wctime64_s function
- ctime_s function
- ctime32_s function
- _ctime64_s function
- tctime64_s function
- wctime64_s function
- wctime_s function
- _tctime_s function
- tctime32_s function
- wctime32_s function
- time, converting
- _ctime32_s function
- _tctime32_s function
ms.assetid: 36ac419a-8000-4389-9fd8-d78b747a009b
caps.latest.revision: 27
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
ms.openlocfilehash: 371ca59a6002cd5936771f1ac9cea7c39b192cee
ms.contentlocale: zh-cn
ms.lasthandoff: 04/04/2017

---
# <a name="ctimes-ctime32s-ctime64s-wctimes-wctime32s-wctime64s"></a>ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s
将时间值转换为字符串，并调整本地时区设置。 这些版本的 [ctime、_ctime64、_wctime、_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t ctime_s(   
   char* buffer,  
   size_t numberOfElements,  
   const time_t *time   
);  
errno_t _ctime32_s(   
   char* buffer,  
   size_t numberOfElements,  
   const __time32_t *time   
);  
errno_t _ctime64_s(   
   char* buffer,  
   size_t numberOfElements,  
   const __time64_t *time )  
;  
errno_t _wctime_s(   
   wchar_t* buffer,  
   size_t numberOfElements,  
   const time_t *time   
);  
errno_t _wctime32_s(   
   wchar_t* buffer,  
   size_t numberOfElements,  
   const __time32_t *time   
);  
errno_t _wctime64_s(   
   wchar_t* buffer,  
   size_t numberOfElements,  
   const __time64_t *time   
);  
template <size_t size>  
errno_t _ctime32_s(   
   char (&buffer)[size],  
   const __time32_t *time   
); // C++ only  
template <size_t size>  
errno_t _ctime64_s(   
   char (&buffer)[size],  
   const __time64_t *time  
); // C++ only  
template <size_t size>  
errno_t _wctime32_s(   
   wchar_t (&buffer)[size],  
   const __time32_t *time   
); // C++ only  
template <size_t size>  
errno_t _wctime64_s(   
   wchar_t (&buffer)[size],  
   const __time64_t *time   
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 [out] `buffer`  
 必须足以容纳 26 个字符。 指向字符字符串结果时，或`NULL`如果︰  
  
-   `time` 表示 1970 年 1 月 1 日午夜前的日期（UTC 时间）。  
  
-   如果使用 `_ctime32_s` 或 `_wctime32_s`，且 `time` 表示 2038 年 1 月 18 日 23:59:59 后的日期（UTC 时间）。  
  
-   如果使用 `_ctime64_s` 或 `_wctime64_s`，且 `time` 表示 3000 年 12 月 31 日 23:59:59 后的日期（UTC 时间）。  
  
-   如果使用 `_ctime_s` 或 `_wctime_s`，这些函数就成为之前的函数的包装器。 请参见“备注”部分。  
  
 [in] `numberOfElements`  
 缓冲区的大小。  
  
 [in] `time`  
 指向存储时间的指针。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 0。 如果由于无效参数导致失败，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则返回错误代码。 在 ERRNO.H 中定义了错误代码；有关这些错误的列表，请参阅 [errno](../../c-runtime-library/errno-constants.md)。 针对每个错误条件而引发的实际错误代码如下表所示。  
  
## <a name="error-conditions"></a>错误条件  
  
|`buffer`|`numberOfElements`|`time`|返回|`buffer` 中的值|  
|--------------|------------------------|------------|------------|-----------------------|  
|`NULL`|任何|任何|`EINVAL`|未修改|  
|非 `NULL`（指向有效内存）|0|任何|`EINVAL`|未修改|  
|非 `NULL`|0< 大小 < 26|任何|`EINVAL`|空字符串|  
|非 `NULL`|>= 26|NULL|`EINVAL`|空字符串|  
|非 `NULL`|>= 26|< 0|`EINVAL`|空字符串|  
  
## <a name="remarks"></a>备注  
 `ctime_s` 函数将存储为 [time_t](../../c-runtime-library/standard-types.md) 结构的时间值转换为字符串。 通常情况下，通过对 [time](../../c-runtime-library/reference/time-time32-time64.md) 的调用获取 `time` 值，它返回自协调世界时 (UTC) 1970 年 1 月 1 日午夜 (00:00:00) 以来经过的秒数。 返回值字符串正好包含 26 个字符，且格式为：  
  
```  
Wed Jan 02 02:03:55 1980\n\0  
```  
  
 使用 24 小时制。 所有字段都具有固定宽度。 新换行符 ('\n') 和空字符 ('\0') 占据字符串的最后两个位置。  
  
 转换的字符串同时根据本地时区设置进行调整。 有关配置本地时间的信息，请参阅 `time`、[_ftime](../../c-runtime-library/reference/ftime-ftime32-ftime64.md) 和 [localtime32_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md) 函数，有关定义时区环境和全局变量的信息，请参阅 [_tzset](../../c-runtime-library/reference/tzset.md) 函数。  
  
 `_wctime32_s` 和 `_wctime64_s` 是 `_ctime32_s` 和 `_ctime64_s` 的宽字符版本；返回指向宽字符串的指针。 否则，`_ctime64_s`、`_wctime32_s` 和 `_wctime64_s` 的行为与 `_ctime32_s` 完全相同。  
  
 `ctime_s` 是计算出 `_ctime64_s` 的内联函数，且 `time_t` 等同于 `__time64_t`。 如果需要强制编译器将 `time_t` 解释为旧的 32 位 `time_t`，则可以定义 `_USE_32BIT_TIME_T`。 执行此操作将导致 `ctime_s` 计算出 `_ctime32_s`。 不建议这样做，因为应用程序可能会在 2038 年 1 月 18 日后失效；且在 64 位平台上不允许使用它。  
  
 在 C++ 中，通过模板重载简化这些函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tctime_s`|`ctime_s`|`ctime_s`|`_wctime_s`|  
|`_tctime32_s`|`_ctime32_s`|`_ctime32_s`|`_wctime32_s`|  
|`_tctime64_s`|`_ctime64_s`|`_ctime64_s`|`_wctime64_s`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`ctime_s`, `_ctime32_s`, `_ctime64_s`|\<time.h>|  
|`_wctime_s`, `_wctime32_s`, `_wctime64_s`|\<time.h> 或 \<wchar.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="example"></a>示例  
  
```  
// crt_wctime_s.c  
/* This program gets the current  
 * time in time_t form and then uses _wctime_s to  
 * display the time in string form.  
 */  
  
#include <time.h>  
#include <stdio.h>  
  
#define SIZE 26  
  
int main( void )  
{  
   time_t ltime;  
   wchar_t buf[SIZE];  
   errno_t err;  
  
   time( &ltime );  
  
   err = _wctime_s( buf, SIZE, &ltime );  
   if (err != 0)  
   {  
      printf("Invalid Arguments for _wctime_s. Error Code: %d\n", err);  
   }  
   wprintf_s( L"The time is %s\n", buf );  
}  
```  
  
## <a name="sample-output"></a>示例输出  
  
```  
The time is Fri Apr 25 13:03:39 2003  
```  
  
## <a name="see-also"></a>另请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime_s、_wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime_s、_gmtime32_s、_gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime_s、_localtime32_s、_localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)
