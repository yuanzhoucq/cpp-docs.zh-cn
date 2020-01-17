---
title: getenv_s, _wgetenv_s
description: 介绍 getenv_s 和 _wgetenv_s 函数的 Microsoft C 运行时库。
ms.date: 01/15/2020
api_name:
- getenv_s
- _wgetenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- getenv_s
- _tgetenv_s
- _wgetenv_s
helpviewer_keywords:
- _tgetenv_s function
- wgetenv_s function
- _wgetenv_s function
- getenv_s function
- environment variables
- tgetenv_s function
ms.assetid: c3ae1ffe-d4cd-4bae-bcb1-3afa754c613a
no-loc:
- getenv_s
- _wgetenv_s
- _putenv_s
- main
- wmain
- errno
- EINVAL
- ERANGE
- _environ
- _wenviron
- _putenv
- _wputenv
- _tgetenv_s
- _tzset
- _dupenv_s
- _wdupenv_s
ms.openlocfilehash: 1eb0adc8c92f1133fd929b9d877b2526c042855f
ms.sourcegitcommit: e93f3e6a110fe38bc642055bdf4785e620d4220f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2020
ms.locfileid: "76124002"
---
# <a name="opno-locgetenv_s-opno-loc_wgetenv_s"></a>getenv_s, _wgetenv_s

从当前环境中获取值。 这些版本的 [getenv、_wgetenv](getenv-wgetenv.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
errno_t getenv_s(
   size_t *pReturnValue,
   char* buffer,
   size_t numberOfElements,
   const char *varname
);
errno_t _wgetenv_s(
   size_t *pReturnValue,
   wchar_t *buffer,
   size_t numberOfElements,
   const wchar_t *varname
);
template <size_t size>
errno_t getenv_s(
   size_t *pReturnValue,
   char (&buffer)[size],
   const char *varname
); // C++ only
template <size_t size>
errno_t _wgetenv_s(
   size_t *pReturnValue,
   wchar_t (&buffer)[size],
   const wchar_t *varname
); // C++ only
```

### <a name="parameters"></a>参数

*pReturnValue*<br/>
所需的缓冲区大小，如果找不到该变量，则为 0。

*buffer*<br/>
用于存储环境变量值的缓冲区。

*numberOfElements*<br/>
*缓冲区*的大小。

*varname*<br/>
环境变量名称。

## <a name="return-value"></a>返回值

如果成功，则为零；如果失败，则返回错误代码。

### <a name="error-conditions"></a>错误条件

|*pReturnValue*|*buffer*|*numberOfElements*|*varname*|返回值|
|--------------------|--------------|------------------------|---------------|------------------|
|**NULL**|任何|任何|任何|**EINVAL**|
|任何|**NULL**|>0|任何|**EINVAL**|
|任何|任何|任何|**NULL**|**EINVAL**|

如[参数验证](../../c-runtime-library/parameter-validation.md)中所述，这些错误条件调用无效参数处理程序。 如果允许执行继续，则函数将 **errno** 设置为 **EINVAL** 并返回 **EINVAL** 。

此外，如果缓冲区太小，这些函数将返回 **ERANGE** 。 它们不会调用无效的参数处理程序。 它们在*pReturnValue*中写出所需的缓冲区大小，从而使程序能够使用较大的缓冲区再次调用函数。

## <a name="remarks"></a>备注

**getenv_s** 函数将在环境变量列表中搜索*varname*。 在 Windows 操作系统中， **getenv_s** 不区分大小写。 **getenv_s** 和[_putenv_s](putenv-s-wputenv-s.md)使用由全局变量指向的环境副本 **_environ** 来访问环境。 **getenv_s** 仅对运行库可访问的数据结构执行，而不是由操作系统为进程创建的环境 "段" 运行。 因此，使用*envp*参数[main](../../cpp/main-function-command-line-args.md)或[wmain](../../cpp/main-function-command-line-args.md)的程序可能会检索无效信息。

**_wgetenv_s** 是 **getenv_s** 的宽字符版本; **_wgetenv_s** 的参数和返回值是宽字符字符串。 **_wenviron** 全局变量是 **_environ** 的宽字符版本。

在 MBCS 程序中（例如，在 SBCS ASCII 程序中）， **_wenviron** 初始为**NULL** ，因为环境是由多字节字符字符串组成的。 然后，在第一次调用[_wputenv](putenv-wputenv.md)或第一次调用 **_wgetenv_s** 时，如果（MBCS）环境已存在，则将创建一个对应的宽字符字符串环境，并通过 **_wenviron** 指向该环境。

同样，在 Unicode （ **_wmain**）程序中， **_environ** 最初为**NULL** ，因为环境是由宽字符字符串组成的。 然后，在首次调用[_putenv](putenv-wputenv.md)或首次调用时 **getenv_s** 如果（Unicode）环境已存在，则会创建相应的 MBCS 环境，并通过 **_environ** 指向该环境。

当程序中同时存在环境的两个副本（MBCS 和 Unicode）时，运行时系统必须保留这两个副本，而这将减慢执行时间。 例如，在调用 **_putenv** 时，还会自动执行对 **_wputenv** 的调用，以便两个环境字符串相对应。

> [!CAUTION]
> 在极少数情况下，当运行时系统同时保留环境的 Unicode 版本和多字节版本时，两个环境版本可能不完全对应。 这是因为，虽然任何唯一的多字节字符字符串将映射到唯一的 Unicode 字符串，但从唯一的 Unicode 字符串到多字节字符字符串的映射却不一定是唯一的。 有关详细信息，请参阅[_environ_wenviron](../../c-runtime-library/environ-wenviron.md)。

> [!NOTE]
> **_putenv_s** 和 **_getenv_s**系列函数不是线程安全的。 **_getenv_s** **_putenv_s** 在修改字符串时可能返回字符串指针，从而导致随机失败。 确保对这些函数的调用同步。

在 C++ 中，这些函数的使用由模板重载简化；重载可以自动推导出缓冲区长度，从而不再需要指定大小自变量。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv_s**|**getenv_s**|**getenv_s**|**_wgetenv_s**|

若要检查或更改**TZ**环境变量的值，请根据需要使用 **getenv_s** 、 **_putenv** 和 **_tzset** 。 有关**TZ**的详细信息，请参阅[_tzset](tzset.md)和[_daylight、_dstbias、_timezone 和 _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)。

## <a name="requirements"></a>需求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**getenv_s**|\<stdlib.h>|
|**_wgetenv_s**|\<stdlib.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_getenv_s.c
// This program uses getenv_s to retrieve
// the LIB environment variable and then uses
// _putenv to change it to a new value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char* libvar;
   size_t requiredSize;

   getenv_s( &requiredSize, NULL, 0, "LIB");
   if (requiredSize == 0)
   {
      printf("LIB doesn't exist!\n");
      exit(1);
   }

   libvar = (char*) malloc(requiredSize * sizeof(char));
   if (!libvar)
   {
      printf("Failed to allocate memory!\n");
      exit(1);
   }

   // Get the value of the LIB environment variable.
   getenv_s( &requiredSize, libvar, requiredSize, "LIB" );

   printf( "Original LIB variable is: %s\n", libvar );

   // Attempt to change path. Note that this only affects
   // the environment variable of the current process. The command
   // processor's environment is not changed.
   _putenv_s( "LIB", "c:\\mylib;c:\\yourlib" );

   getenv_s( &requiredSize, NULL, 0, "LIB");

   libvar = (char*) realloc(libvar, requiredSize * sizeof(char));
   if (!libvar)
   {
      printf("Failed to allocate memory!\n");
      exit(1);
   }

   // Get the new value of the LIB environment variable.
   getenv_s( &requiredSize, libvar, requiredSize, "LIB" );

   printf( "New LIB variable is: %s\n", libvar );

   free(libvar);
}
```

```Output
Original LIB variable is: c:\vctools\lib;c:\vctools\atlmfc\lib;c:\vctools\PlatformSDK\lib;c:\vctools\Visual Studio SDKs\DIA Sdk\lib;c:\vctools\Visual Studio SDKs\BSC Sdk\lib
New LIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>另请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[环境常量](../../c-runtime-library/environmental-constants.md)<br/>
[_putenv，_wputenv](putenv-wputenv.md)<br/>
[_dupenv_s，_wdupenv_s](dupenv-s-wdupenv-s.md)<br/>
