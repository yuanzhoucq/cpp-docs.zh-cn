---
title: asctime_s、_wasctime_s
ms.date: 11/04/2016
api_name:
- _wasctime_s
- asctime_s
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- asctime_s
- _wasctime_s
- _tasctime_s
helpviewer_keywords:
- tasctime_s function
- _tasctime_s function
- time structure conversion
- wasctime_s function
- time, converting
- _wasctime_s function
- asctime_s function
ms.assetid: 17ad9b2b-a459-465d-976a-42822897688a
ms.openlocfilehash: 1cd2a15db0a27dedd88b9abf24b98d338515c949
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624786"
---
# <a name="asctime_s-_wasctime_s"></a>asctime_s、_wasctime_s

将**tm**时间结构转换为字符串。 这些函数是 [asctime、_wasctime](asctime-wasctime.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。

## <a name="syntax"></a>语法

```C
errno_t asctime_s(
   char* buffer,
   size_t numberOfElements,
   const struct tm *tmSource
);
errno_t _wasctime_s(
   wchar_t* buffer,
   size_t numberOfElements
   const struct tm *tmSource
);
template <size_t size>
errno_t asctime_s(
   char (&buffer)[size],
   const struct tm *tmSource
); // C++ only
template <size_t size>
errno_t _wasctime_s(
   wchar_t (&buffer)[size],
   const struct tm *tmSource
); // C++ only
```

### <a name="parameters"></a>参数

*buffer*<br/>
指向用于存储字符串结果的缓冲区的指针。 此函数假定指针指向使用*numberOfElements*指定的大小的有效内存位置。

*numberOfElements*<br/>
用于存储结果的缓冲区的大小。

*tmSource*<br/>
时间/日期结构。 此函数假定为指向有效**结构** **tm**对象的指针。

## <a name="return-value"></a>返回值

如果成功，则返回 0。 如果失败，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则返回值为错误代码。 错误代码是在 ERRNO.H 中定义的。 有关详细信息，请参阅 [errno 常量](../../c-runtime-library/errno-constants.md)。 针对每个错误条件返回的实际错误代码如下表所示。

### <a name="error-conditions"></a>错误条件

|*buffer*|*numberOfElements*|*tmSource*|返回|*缓冲区*中的值|
|--------------|------------------------|----------|------------|-----------------------|
|**NULL**|任意|任意|**EINVAL**|未修改|
|Not **NULL** （指向有效内存）|0|任意|**EINVAL**|未修改|
|Not **NULL**|0< 大小 < 26|任意|**EINVAL**|空字符串|
|Not **NULL**|>= 26|**NULL**|**EINVAL**|空字符串|
|Not **NULL**|>= 26|无效的时间结构或超出时间组件值范围|**EINVAL**|空字符串|

> [!NOTE]
> **Wasctime_s**的错误条件类似于**asctime_s** ，但大小限制以单词度量的情况除外。

## <a name="remarks"></a>备注

**Asctime**函数将存储为结构的时间转换为字符串。 *TmSource*值通常是通过调用**gmtime**或**localtime**获取的。 这两个函数可用于填写**tm**结构，如时间中所定义。高.

|timeptr 成员|“值”|
|--------------------|-----------|
|**tm_hour**|午夜后的小时数（0-23）|
|**tm_isdst**|如果夏令时生效，则为正；如果夏令时不生效，则为 0；如果夏令时状态未知，则为负。 C 运行时库假设使用美国规则实现夏令时 (DST) 的计算。|
|**tm_mday**|每月的某一日（1-31）|
|**tm_min**|每小时后的分钟数（0-59）|
|**tm_mon**|Month （0-11;1月 = 0）|
|**tm_sec**|分钟后的秒数（0-59）|
|**tm_wday**|一周中的某一日（0-6;星期日 = 0）|
|**tm_yday**|一年的某一日（0-365;1月1日 = 0）|
|**tm_year**|年（当前年份减去 1900）|

转换的字符串同时根据本地时区设置进行调整。 有关配置本地时间的信息，请参阅 [time、_time32、_time64](time-time32-time64.md) 和 [_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md) 以及 [localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md) 函数，有关定义时区环境和全局变量的信息，请参阅 [_tzset](tzset.md) 函数。

**Asctime_s**生成的字符串结果正好包含26个字符，格式 `Wed Jan 02 02:03:55 1980\n\0`。 使用 24 小时制。 所有字段都具有固定宽度。 换行符和空字符占据字符串的最后两个位置。 作为第二个参数传入的值应该至少应是此大小。 如果小于，则返回错误代码**EINVAL**。

**_wasctime_s**是**asctime_s**的宽字符版本。 否则， **_wasctime_s**和**asctime_s**的行为相同。

这些函数的调试库版本首先用0xFE 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

### <a name="generic-text-routine-mapping"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime_s**|**asctime_s**|**asctime_s**|**_wasctime_s**|

在 C++ 中，通过模板重载简化这些函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**asctime_s**|\<time.h>|
|**_wasctime_s**|\<time.h> 或 \<wchar.h>|

## <a name="security"></a>安全

如果缓冲区指针不为**NULL** ，并且指针不指向有效的缓冲区，则该函数将覆盖位置上的任何内容。 该操作还将导致访问冲突。

如果传入的大小参数大于缓冲区的实际大小，则可能会发生[缓冲区溢出](/windows/win32/SecBP/avoiding-buffer-overruns)。

## <a name="example"></a>示例

此程序将系统时间置于长整型**aclock**中，将其转换为结构**newtime** ，然后使用**asctime_s**函数将其转换为字符串形式的输出。

```C
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

[时间管理](../../c-runtime-library/time-management.md)<br/>
[ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
