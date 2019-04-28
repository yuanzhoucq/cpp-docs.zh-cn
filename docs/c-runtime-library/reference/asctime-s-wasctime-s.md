---
title: asctime_s、_wasctime_s
ms.date: 11/04/2016
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
helpviewer_keywords:
- tasctime_s function
- _tasctime_s function
- time structure conversion
- wasctime_s function
- time, converting
- _wasctime_s function
- asctime_s function
ms.assetid: 17ad9b2b-a459-465d-976a-42822897688a
ms.openlocfilehash: 350d8c7b1dcf61272a3cfee884dff8a63b455f1c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349470"
---
# <a name="asctimes-wasctimes"></a>asctime_s、_wasctime_s

将转换**tm**时间结构转换为字符串。 这些函数是 [asctime、_wasctime](asctime-wasctime.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。

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
指向用于存储字符串结果的缓冲区的指针。 此函数假定指向有效内存位置的指针与由指定的大小*numberOfElements*。

*numberOfElements*<br/>
若要将结果存储所使用的缓冲区的大小。

*tmSource*<br/>
时间/日期结构。 此函数假定为指向有效**struct** **tm**对象。

## <a name="return-value"></a>返回值

如果成功，则返回 0。 如果失败，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则返回值为错误代码。 错误代码是在 ERRNO.H 中定义的。 有关详细信息，请参阅 [errno 常量](../../c-runtime-library/errno-constants.md)。 针对每个错误条件返回的实际错误代码如下表所示。

### <a name="error-conditions"></a>错误条件

|*buffer*|*numberOfElements*|*tmSource*|返回|中的值*缓冲区*|
|--------------|------------------------|----------|------------|-----------------------|
|**NULL**|任意|任意|**EINVAL**|未修改|
|不**NULL** （指向有效内存）|0|任意|**EINVAL**|未修改|
|不**NULL**|0< 大小 < 26|任意|**EINVAL**|空字符串|
|不**NULL**|>= 26|**NULL**|**EINVAL**|空字符串|
|不**NULL**|>= 26|无效的时间结构或超出时间组件值范围|**EINVAL**|空字符串|

> [!NOTE]
> 错误条件**wasctime_s**类似于**asctime_s**使用以字为单位的大小限制的异常。

## <a name="remarks"></a>备注

**Asctime**函数将存储为结构转换为字符串的时间转换。 *TmSource*值通常从调用获取**gmtime**或**localtime**。 这两个函数可用于填写**tm**结构，如定义的时间。H.

|timeptr 成员|“值”|
|--------------------|-----------|
|**tm_hour**|午夜 (0-23) 以后的小时数|
|**tm_isdst**|如果夏令时生效，则为正；如果夏令时不生效，则为 0；如果夏令时状态未知，则为负。 C 运行时库假设使用美国规则实现夏令时 (DST) 的计算。|
|**tm_mday**|一天的月份 (1-31)|
|**tm_min**|小时 (0-59) 后的分钟数|
|**tm_mon**|月 (0-11;年 1 月 = 0）|
|**tm_sec**|分钟 (0-59) 后的秒数|
|**tm_wday**|一天的周 (0-6;星期天 = 0）|
|**tm_yday**|某一日 (0-365;1 月 1 日 = 0)|
|**tm_year**|年（当前年份减去 1900）|

转换的字符串同时根据本地时区设置进行调整。 有关配置本地时间的信息，请参阅 [time、_time32、_time64](time-time32-time64.md) 和 [_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md) 以及 [localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md) 函数，有关定义时区环境和全局变量的信息，请参阅 [_tzset](tzset.md) 函数。

生成的字符串结果**asctime_s**包含完全 26 个字符，其形式`Wed Jan 02 02:03:55 1980\n\0`。 使用 24 小时制。 所有字段都具有固定宽度。 换行符和空字符占据字符串的最后两个位置。 作为第二个参数传入的值应该至少应是此大小。 如果是更小，错误代码**EINVAL**，将返回。

**_wasctime_s**是宽字符版本**asctime_s**。 **_wasctime_s**并**asctime_s**行为相同。

### <a name="generic-text-routine-mapping"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime_s**|**asctime_s**|**asctime_s**|**_wasctime_s**|

在 C++ 中，通过模板重载简化这些函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**asctime_s**|\<time.h>|
|**_wasctime_s**|\<time.h> 或 \<wchar.h>|

## <a name="security"></a>安全性

如果缓冲区指针不是**NULL**和指针不指向有效的缓冲区，则函数将覆盖任何位于的位置。 该操作还将导致访问冲突。

如果传入的大小参数大于缓冲区的实际大小，则可能会发生[缓冲区溢出](/windows/desktop/SecBP/avoiding-buffer-overruns)。

## <a name="example"></a>示例

此程序将系统时间置于长整型**时钟的人脸**，将其转换为结构**newtime** ，然后将它转换为字符串形式的输出，请使用**asctime_s**函数。

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
