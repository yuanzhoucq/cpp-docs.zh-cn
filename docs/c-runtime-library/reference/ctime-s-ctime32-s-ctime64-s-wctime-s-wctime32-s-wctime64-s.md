---
title: ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s
ms.date: 4/2/2020
api_name:
- _ctime64_s
- _wctime32_s
- ctime_s
- _wctime64_s
- _ctime32_s
- _wctime_s
- _o__ctime32_s
- _o__ctime64_s
- _o__wctime32_s
- _o__wctime64_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: ca7636f7054b6c7e228b57e0e776250f1b4ccb32
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914824"
---
# <a name="ctime_s-_ctime32_s-_ctime64_s-_wctime_s-_wctime32_s-_wctime64_s"></a>ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s

将时间值转换为字符串，并调整本地时区设置。 这些版本的 [ctime、_ctime64、_wctime、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。

## <a name="syntax"></a>语法

```C
errno_t ctime_s(
   char* buffer,
   size_t numberOfElements,
   const time_t *sourceTime
);
errno_t _ctime32_s(
   char* buffer,
   size_t numberOfElements,
   const __time32_t *sourceTime
);
errno_t _ctime64_s(
   char* buffer,
   size_t numberOfElements,
   const __time64_t *sourceTime )
;
errno_t _wctime_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const time_t *sourceTime
);
errno_t _wctime32_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const __time32_t *sourceTime
);
errno_t _wctime64_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const __time64_t *sourceTime
);
```

```cpp
template <size_t size>
errno_t _ctime32_s(
   char (&buffer)[size],
   const __time32_t *sourceTime
); // C++ only
template <size_t size>
errno_t _ctime64_s(
   char (&buffer)[size],
   const __time64_t *sourceTime
); // C++ only
template <size_t size>
errno_t _wctime32_s(
   wchar_t (&buffer)[size],
   const __time32_t *sourceTime
); // C++ only
template <size_t size>
errno_t _wctime64_s(
   wchar_t (&buffer)[size],
   const __time64_t *sourceTime
); // C++ only
```

### <a name="parameters"></a>参数

*宽限*<br/>
必须足以容纳 26 个字符。 指向字符串结果的指针; 如果为，则为**NULL** 。

- *sourceTime*表示1970年1月1日午夜之前的日期。

- 如果使用 **_ctime32_s**或 **_wctime32_s**并且*SourceTime*表示23:59:59 年1月 2038 18 日之后的日期，则为。

- 如果使用 **_ctime64_s**或 **_wctime64_s**并且*SourceTime*表示23:59:59 年12月 3000 31 日之后的日期（UTC）。

- 如果使用 **_ctime_s**或 **_wctime_s**，则这些函数是以前函数的包装器。 请参阅“备注”部分。

*numberOfElements*<br/>
缓冲区的大小。

*sourceTime*<br/>
指向存储时间的指针。

## <a name="return-value"></a>返回值

如果成功，则返回 0。 如果由于无效参数导致失败，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则返回错误代码。 错误代码是在 ERRNO 中定义的。高有关这些错误的列表，请参阅[errno](../../c-runtime-library/errno-constants.md)。 针对每个错误条件而引发的实际错误代码如下表所示。

## <a name="error-conditions"></a>错误条件

|*宽限*|*numberOfElements*|*sourceTime*|返回|*缓冲区*中的值|
|--------------|------------------------|------------|------------|-----------------------|
|**Null**|any|any|**EINVAL**|未修改|
|Not **NULL** （指向有效内存）|0|any|**EINVAL**|未修改|
|Not **NULL**|0< 大小 < 26|any|**EINVAL**|空字符串|
|Not **NULL**|>= 26|Null|**EINVAL**|空字符串|
|Not **NULL**|>= 26|< 0|**EINVAL**|空字符串|

## <a name="remarks"></a>备注

**Ctime_s**函数将作为[time_t](../../c-runtime-library/standard-types.md)结构存储的时间值转换为字符串。 *SourceTime*值通常是从对[time](time-time32-time64.md)的调用中获取的，它返回自午夜（00:00:00）起，年1月 1970 1 日（协调世界时（UTC））开始经过的秒数。 返回值字符串正好包含 26 个字符，且格式为：

`Wed Jan 02 02:03:55 1980\n\0`

使用 24 小时制。 所有字段都具有固定宽度。 新换行符 ('\n') 和空字符 ('\0') 占据字符串的最后两个位置。

转换的字符串同时根据本地时区设置进行调整。 有关定义时区环境和全局变量的信息，请参阅[time](time-time32-time64.md)、 [_ftime](ftime-ftime32-ftime64.md)和[localtime32_s](localtime-s-localtime32-s-localtime64-s.md)函数，了解有关配置本地时间和[_tzset](tzset.md)函数的信息。

**_wctime32_s**和 **_wctime64_s**是 **_ctime32_s**和 **_ctime64_s**的宽字符版本;返回指向宽字符字符串的指针。 否则， **_ctime64_s**、 **_wctime32_s**和 **_wctime64_s**与 **_ctime32_s**的行为相同。

**ctime_s**是计算结果为 **_ctime64_s**并且**time_t**等效于 **__time64_t**的内联函数。 如果需要强制编译器将**time_t**解释为旧32位**time_t**，可以定义 **_USE_32BIT_TIME_T**。 这样做将导致**ctime_s**计算为 **_ctime32_s**。 不建议这样做，因为应用程序可能会在 2038 年 1 月 18 日后失效；且在 64 位平台上不允许使用它。

在 C++ 中，通过模板重载简化这些函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

这些函数的调试库版本首先用0xFE 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime_s**|**ctime_s**|**ctime_s**|**_wctime_s**|
|**_tctime32_s**|**_ctime32_s**|**_ctime32_s**|**_wctime32_s**|
|**_tctime64_s**|**_ctime64_s**|**_ctime64_s**|**_wctime64_s**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**ctime_s**、 **_ctime32_s** **_ctime64_s**|\<time.h>|
|**_wctime_s**、 **_wctime32_s** **_wctime64_s**|\<time.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
// crt_wctime_s.c
// This program gets the current
// time in time_t form and then uses _wctime_s to
// display the time in string form.

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

```Output
The time is Fri Apr 25 13:03:39 2003
```

## <a name="see-also"></a>另请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
