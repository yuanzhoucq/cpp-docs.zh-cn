---
title: _searchenv_s、_wsearchenv_s
ms.date: 4/2/2020
api_name:
- _wsearchenv_s
- _searchenv_s
- _o__searchenv_s
- _o__wsearchenv_s
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
- _searchenv_s
- _wsearchenv_s
- wsearchenv_s
- searchenv_s
helpviewer_keywords:
- tsearchenv_s function
- files [C++], finding
- buffers [C++], buffer overruns
- environment paths, searching for files
- wsearchenv_s function
- searchenv_s function
- _tsearchenv_s function
- buffer overruns
- buffers [C++], avoiding overruns
- _wsearchenv_s function
- _searchenv_s function
- environment paths
ms.assetid: 47f9fc29-250e-4c09-b52e-9e9f0ef395ca
ms.openlocfilehash: 5dd21013c8910ba07e2d23606af49bc80458dbc6
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918993"
---
# <a name="_searchenv_s-_wsearchenv_s"></a>_searchenv_s、_wsearchenv_s

通过使用环境路径搜索文件。 这些版本的 [_searchenv、_wsearchenv](searchenv-wsearchenv.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
errno_t _searchenv_s(
   const char *filename,
   const char *varname,
   char *pathname,
   size_t numberOfElements
);
errno_t _wsearchenv_s(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t *pathname,
   size_t numberOfElements
);
template <size_t size>
errno_t _searchenv_s(
   const char *filename,
   const char *varname,
   char (&pathname)[size]
); // C++ only
template <size_t size>
errno_t _wsearchenv_s(
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

*numberOfElements*<br/>
*路径名*缓冲区的大小。

## <a name="return-value"></a>返回值

如果成功，则为零；如果失败，则为错误代码。

如果*filename*为空字符串，则返回值为**ENOENT**。

### <a name="error-conditions"></a>错误条件

|*名字*|*varname*|*路径名*|*numberOfElements*|返回值|*路径名*的内容|
|----------------|---------------|----------------|------------------------|------------------|----------------------------|
|any|any|**Null**|any|**EINVAL**|不适用|
|**Null**|any|any|any|**EINVAL**|未更改|
|any|any|any|<= 0|**EINVAL**|未更改|

如果发生这些错误情况中的任何一个，都会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数会将**errno**设置为**EINVAL**并返回**EINVAL**。

## <a name="remarks"></a>备注

**_Searchenv_s**例程搜索指定域中的目标文件。 *Varname*变量可以是指定目录路径的列表的任何环境或用户定义的变量，如**路径**、 **LIB**和**INCLUDE**。 由于 **_searchenv_s**区分大小写，因此*varname*应与环境变量的情况匹配。 如果*varname*与在进程的环境中定义的环境变量名称不匹配，则该函数将返回零，且*pathname*变量保持不变。

例程首先搜索当前工作目录中的文件。 如果找不到文件，它接下来将查找由环境变量指定的目录。 如果目标文件在其中一个目录中，则新创建的路径将被复制到*pathname*。 如果找不到*文件名*文件， *pathname*包含空的以 null 结尾的字符串。

*路径名*缓冲区的长度应至少为 **_MAX_PATH**个字符，以容纳构造的路径名称的完整长度。 否则， **_searchenv_s**可能会导致*路径名*缓冲区溢出，导致意外行为。

**_wsearchenv_s**是 **_searchenv_s**的宽字符版本;**_wsearchenv_s**的参数是宽字符字符串。 否则 **_wsearchenv_s**和 **_searchenv_s**的行为相同。

在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv_s**|**_searchenv_s**|**_searchenv_s**|**_wsearchenv_s**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_searchenv_s**|\<stdlib.h>|
|**_wsearchenv_s**|\<stdlib.h> 或 \<wchar.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_searchenv_s.c
/* This program searches for a file in
* a directory specified by an environment variable.
*/

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char pathbuffer[_MAX_PATH];
   char searchfile[] = "CL.EXE";
   char envvar[] = "PATH";
   errno_t err;

   /* Search for file in PATH environment variable: */
   err = _searchenv_s( searchfile, envvar, pathbuffer, _MAX_PATH );
   if (err != 0)
   {
      printf("Error searching the path. Error code: %d\n", err);
   }
   if( *pathbuffer != '\0' )
      printf( "Path for %s:\n%s\n", searchfile, pathbuffer );
   else
      printf( "%s not found\n", searchfile );
}
```

```Output
Path for CL.EXE:
C:\Program Files\Microsoft Visual Studio 2010\VC\BIN\CL.EXE
```

## <a name="see-also"></a>另请参阅

[目录控制](../../c-runtime-library/directory-control.md)<br/>
[_searchenv、_wsearchenv](searchenv-wsearchenv.md)<br/>
[getenv、_wgetenv](getenv-wgetenv.md)<br/>
[_putenv、_wputenv](putenv-wputenv.md)<br/>
