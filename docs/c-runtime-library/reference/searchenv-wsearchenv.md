---
title: _searchenv、_wsearchenv
ms.date: 4/2/2020
api_name:
- _searchenv
- _wsearchenv
- _o__searchenv
- _o__wsearchenv
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 83ba5663d569d449a0024db5abe2eb3ee903123b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913223"
---
# <a name="_searchenv-_wsearchenv"></a>_searchenv、_wsearchenv

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

*名字*<br/>
要搜索的文件名称。

*varname*<br/>
要搜索的环境。

*路径名*<br/>
用于存储完整路径的缓冲区。

## <a name="remarks"></a>备注

**_Searchenv**例程搜索指定域中的目标文件。 *Varname*变量可以是任何环境或用户定义的变量（例如， **PATH**、 **LIB**或**INCLUDE**），后者指定目录路径的列表。 由于 **_searchenv**区分大小写，因此*varname*应与环境变量的情况匹配。

例程首先搜索当前工作目录中的文件。 如果找不到文件，它将查找由环境变量指定的目录。 如果目标文件在其中一个目录中，则新创建的路径将被复制到*pathname*。 如果找不到*文件名*文件， *pathname*包含空的以 null 结尾的字符串。

*路径名*缓冲区的长度应至少为 **_MAX_PATH**个字符，以容纳构造的路径名称的完整长度。 否则， **_searchenv**可能会导致*路径名*缓冲区溢出并导致意外的行为。

**_wsearchenv**是 **_searchenv**的宽字符版本，并且 **_wsearchenv**的参数是宽字符字符串。 否则 **_wsearchenv**和 **_searchenv**的行为相同。

如果*filename*为空字符串，则这些函数将返回**ENOENT**。

如果*filename*或*pathname*为**空**指针，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回-1，并将**errno**设置为**EINVAL**。

有关**errno**和错误代码的详细信息，请参阅[errno 常量](../../c-runtime-library/errno-constants.md)。

在 C++ 中，这些函数具有可调用这些函数的更新、更安全的版本的模板重载。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv**|**_searchenv**|**_searchenv**|**_wsearchenv**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_searchenv**|\<stdlib.h>|
|**_wsearchenv**|\<stdlib.h> 或 \<wchar.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

[目录控制](../../c-runtime-library/directory-control.md)<br/>
[getenv、_wgetenv](getenv-wgetenv.md)<br/>
[_putenv、_wputenv](putenv-wputenv.md)<br/>
[_searchenv_s、_wsearchenv_s](searchenv-s-wsearchenv-s.md)<br/>
