---
title: _searchenv、_wsearchenv
ms.date: 11/04/2016
apiname:
- _searchenv
- _wsearchenv
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wsearchenv
- _tsearchenv
- wsearchenv
- _searchenv
- searchenv
helpviewer_keywords:
- _wsearchenv function
- files [C++], finding
- _searchenv function
- tsearchenv function
- environment paths, searching for files
- _tsearchenv function
- wsearchenv function
- searchenv function
- environment paths
ms.assetid: 9c944a27-d326-409b-aee6-410e8762d9d3
ms.openlocfilehash: c1d2361fceec448c98fd9e5a368653aac38c83e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356766"
---
# <a name="searchenv-wsearchenv"></a>_searchenv、_wsearchenv

使用环境路径搜索文件。 提供这些函数的更多安全版本；请参阅 [_searchenv_s、_wsearchenv_s](searchenv-s-wsearchenv-s.md)。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
void _searchenv(
   const char *filename,
   const char *varname,
   char *pathname
);
void _wsearchenv(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t *pathname
);
template <size_t size>
void _searchenv(
   const char *filename,
   const char *varname,
   char (&pathname)[size]
); // C++ only
template <size_t size>
void _wsearchenv(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t (&pathname)[size]
); // C++ only
```

### <a name="parameters"></a>参数

*filename*<br/>
要搜索的文件名称。

*varname*<br/>
要搜索的环境。

*pathname*<br/>
用于存储完整路径的缓冲区。

## <a name="remarks"></a>备注

**_Searchenv**例程搜索指定的域中的目标文件。 *Varname*变量可以是任何环境或用户定义的变量，例如，**路径**， **LIB**，或**INCLUDE**—，它指定目录路径的列表。 因为 **_searchenv**区分大小写， *varname*应匹配的环境变量的大小写。

例程首先搜索当前工作目录中的文件。 如果找不到文件，它将查找由环境变量指定的目录。 如果目标文件是在其中一个目录中，新创建的路径复制到*pathname*。 如果*文件名*找不到文件，*路径名*包含空的以 null 结尾的字符串。

*Pathname*缓冲区应至少 **_MAX_PATH**字符很长时间才能容纳构建的路径名称的完整长度。 否则为 **_searchenv**可能溢出*路径名*缓冲区并导致意外的行为。

**_wsearchenv**是宽字符版本 **_searchenv**，并为参数 **_wsearchenv**都是宽字符字符串。 **_wsearchenv**并 **_searchenv**行为相同。

如果*文件名*是空字符串，这些函数将返回**ENOENT**。

如果*文件名*或*路径名*是**NULL**调用指针，无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，这些函数将返回-1 并设置**errno**到**EINVAL**。

有关详细信息**errno**和错误代码，请参阅[errno 常量](../../c-runtime-library/errno-constants.md)。

在 C++ 中，这些函数具有可调用这些函数的更新、更安全的版本的模板重载。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv**|**_searchenv**|**_searchenv**|**_wsearchenv**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_searchenv**|\<stdlib.h>|
|**_wsearchenv**|\<stdlib.h> 或 \<wchar.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_searchenv.c
// compile with: /W3
// This program searches for a file in
// a directory that's specified by an environment variable.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char pathbuffer[_MAX_PATH];
   char searchfile[] = "CL.EXE";
   char envvar[] = "PATH";

   // Search for file in PATH environment variable:
   _searchenv( searchfile, envvar, pathbuffer ); // C4996
   // Note: _searchenv is deprecated; consider using _searchenv_s
   if( *pathbuffer != '\0' )
      printf( "Path for %s:\n%s\n", searchfile, pathbuffer );
   else
      printf( "%s not found\n", searchfile );
}
```

```Output
Path for CL.EXE:
C:\Program Files\Microsoft Visual Studio 8\VC\BIN\CL.EXE
```

## <a name="see-also"></a>请参阅

[目录控制](../../c-runtime-library/directory-control.md)<br/>
[getenv、_wgetenv](getenv-wgetenv.md)<br/>
[_putenv、_wputenv](putenv-wputenv.md)<br/>
[_searchenv_s、_wsearchenv_s](searchenv-s-wsearchenv-s.md)<br/>
