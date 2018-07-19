---
title: _searchenv_s、_wsearchenv_s | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wsearchenv_s
- _searchenv_s
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
- _searchenv_s
- _wsearchenv_s
- wsearchenv_s
- searchenv_s
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b14dee908cdf1cc0d564047035a72f501df130b4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32410910"
---
# <a name="searchenvs-wsearchenvs"></a>_searchenv_s、_wsearchenv_s

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

*filename*<br/>
要搜索的文件名称。

*varname*<br/>
要搜索的环境。

*路径名*<br/>
用于存储完整路径的缓冲区。

*numberOfElements*<br/>
大小*路径名*缓冲区。

## <a name="return-value"></a>返回值

如果成功，则为零；如果失败，则为错误代码。

如果*filename*为空字符串，则返回值是**ENOENT**。

### <a name="error-conditions"></a>错误条件

|*filename*|*varname*|*路径名*|*numberOfElements*|返回值|内容*路径名*|
|----------------|---------------|----------------|------------------------|------------------|----------------------------|
|任何|任何|**NULL**|任何|**EINVAL**|n/a|
|**NULL**|任何|任何|任何|**EINVAL**|未更改|
|任何|任何|任何|<= 0|**EINVAL**|未更改|

如果发生这些错误情况中的任何一个，都会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将设置**errno**到**EINVAL**并返回**EINVAL**。

## <a name="remarks"></a>备注

**_Searchenv_s**例程搜索指定的域中的目标文件。 *Varname*变量可以是任何环境或用户定义的变量，如指定的目录路径的列表**路径**， **LIB**，和**包括**. 因为 **_searchenv_s**区分大小写， *varname*应匹配的环境变量的大小写。 如果*varname*不在进程的环境中定义的环境变量的名称匹配，则函数返回零和*路径名*变量保持不变。

例程首先搜索当前工作目录中的文件。 如果找不到文件，它接下来将查找由环境变量指定的目录。 如果目标文件在其中一个目录，则新创建的路径复制到*路径名*。 如果*filename*找不到文件，*路径名*包含一个空的以 null 结尾的字符串。

*路径名*缓冲区至少应为 **_MAX_PATH**长度个字符，以便容纳构建的路径名称的完整长度。 否则为 **_searchenv_s**可能溢出*路径名*缓冲区导致意外行为。

**_wsearchenv_s**是宽字符版本的 **_searchenv_s**; 的自变量 **_wsearchenv_s**是宽字符字符串。 **_wsearchenv_s**和 **_searchenv_s**否则具有相同行为。

在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv_s**|**_searchenv_s**|**_searchenv_s**|**_wsearchenv_s**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_searchenv_s**|\<stdlib.h>|
|**_wsearchenv_s**|\<stdlib.h> 或 \<wchar.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[目录控制](../../c-runtime-library/directory-control.md)<br/>
[_searchenv、_wsearchenv](searchenv-wsearchenv.md)<br/>
[getenv、_wgetenv](getenv-wgetenv.md)<br/>
[_putenv、_wputenv](putenv-wputenv.md)<br/>
