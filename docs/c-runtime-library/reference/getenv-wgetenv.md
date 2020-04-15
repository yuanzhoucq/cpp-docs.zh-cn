---
title: getenv, _wgetenv
description: 描述 Microsoft C 运行时getenv库_wgetenv和函数。
ms.date: 4/2/2020
api_name:
- getenv
- _wgetenv
- _o__wgetenv
- _o_getenv
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wgetenv
- getenv
- _tgetenv
helpviewer_keywords:
- getenv function
- tgetenv function
- wgetenv function
- environment values
- environment variables
- _tgetenv function
- _wgetenv function
ms.assetid: 3b9cb9ab-a126-4e0e-a44f-6c5a7134daf4
no-loc:
- getenv
- _wgetenv
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
ms.openlocfilehash: c9d7f7e1a2c5d6b15aee2f7f972a30cc0c90115c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344257"
---
# <a name="getenv-_wgetenv"></a>getenv、_wgetenv

从当前环境中获取值。 提供这些函数的更安全版本；请参阅 [getenv_s、_wgetenv_s](getenv-s-wgetenv-s.md)。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
char *getenv(
   const char *varname
);
wchar_t *_wgetenv(
   const wchar_t *varname
);
```

### <a name="parameters"></a>参数

*瓦尔名称*<br/>
环境变量名称。

## <a name="return-value"></a>返回值

返回指向包含*varname*的环境表条目的指针。 使用返回的指针修改环境变量并不安全。 使用[_putenv](putenv-wputenv.md)函数修改环境变量的值。 如果在环境表中找不到*varname，* 则返回值为**NULL。**

## <a name="remarks"></a>备注

**getenv**函数搜索变量环境变量的列表，以搜索*varname*。 **getenv**在 Windows 操作系统中不区分大小写。 **getenv**和 **_putenv**使用全局变量 **_environ**指向的环境的副本来访问环境。 **getenv**仅在运行时库可访问的数据结构上运行，而不是操作系统为进程创建的环境"段"上运行。 因此，使用*envp*参数到[主](../../cpp/main-function-command-line-args.md)或[wmain](../../cpp/main-function-command-line-args.md)的程序可能会检索无效信息。

如果*varname*为**NULL，** 则此函数将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，此函数将**errno**设置到**EINVAL**并返回**NULL**。

**_wgetenv**是**getenv**的宽字符版本;**_wgetenv**的参数和返回值是宽字符字符串。 **_wenviron**全局变量是 **_environ**的宽字符版本。

在 MBCS 程序中（例如，在 SBCS ASCII 程序中 **），_wenviron**最初为**NULL，** 因为环境由多字节字符串组成。 然后，在第一次调用[_wputenv](putenv-wputenv.md)时，或者在第一次调用 **_wgetenv**如果 （MBCS） 环境已经存在时，将创建相应的宽字符字符串环境，然后由 **_wenviron**指向 。

同样，在 Unicode （**_wmain**） 程序中 **，_environ**最初为**NULL，** 因为环境由宽字符字符串组成。 然后，在第一次调用 **_putenv**时，或者在第一次调用**getenv**时（如果（Unicode） 环境已经存在，则创建相应的 MBCS 环境，然后由 **_environ**指向 。

当程序中同时存在环境的两个副本（MBCS 和 Unicode）时，运行时系统必须保留这两个副本，而这将减慢执行时间。 例如，每当调用 **_putenv**时，也会自动执行对 **_wputenv**的调用，以便两个环境字符串对应。

> [!CAUTION]
> 在极少数情况下，当运行时系统同时保留环境的 Unicode 版本和多字节版本时，两个环境版本可能不完全对应。 这是因为，虽然任何唯一的多字节字符字符串将映射到唯一的 Unicode 字符串，但从唯一的 Unicode 字符串到多字节字符字符串的映射却不一定是唯一的。 有关详细信息，请参阅 [_environ、_wenviron](../../c-runtime-library/environ-wenviron.md)。

> [!NOTE]
> **函数的_putenv**和 **_getenv**系列不具有线程安全。 **_getenv**可以在 **_putenv**修改字符串时返回字符串指针，从而导致随机失败。 确保对这些函数的调用同步。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv**|**getenv**|**getenv**|**_wgetenv**|

要检查或更改**TZ**环境变量的值，请根据需要使用**getenv、_putenv**和 **_putenv****_tzset。** 有关**TZ**的详细信息，请参阅[_tzset](tzset.md)和[_daylight、时区和_tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**getenv**|\<stdlib.h>|
|**_wgetenv**|\<stdlib.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_getenv.c
// compile with: /W3
// This program uses getenv to retrieve
// the LIB environment variable and then uses
// _putenv to change it to a new value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *libvar;

   // Get the value of the LIB environment variable.
   libvar = getenv( "LIB" ); // C4996
   // Note: getenv is deprecated; consider using getenv_s instead

   if( libvar != NULL )
      printf( "Original LIB variable is: %s\n", libvar );

   // Attempt to change path. Note that this only affects the environment
   // variable of the current process. The command processor's
   // environment is not changed.
   _putenv( "LIB=c:\\mylib;c:\\yourlib" ); // C4996
   // Note: _putenv is deprecated; consider using putenv_s instead

   // Get new value.
   libvar = getenv( "LIB" ); // C4996

   if( libvar != NULL )
      printf( "New LIB variable is: %s\n", libvar );
}
```

```Output
Original LIB variable is: C:\progra~1\devstu~1\vc\lib
New LIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>另请参阅

[过程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[环境常数](../../c-runtime-library/environmental-constants.md)<br/>
