---
title: _getcwd、_wgetcwd
ms.date: 11/04/2016
apiname:
- _wgetcwd
- _getcwd
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getcwd
- wgetcwd
- _wgetcwd
- tgetcwd
- _tgetcwd
helpviewer_keywords:
- getcwd function
- working directory
- _wgetcwd function
- _getcwd function
- current working directory
- wgetcwd function
- directories [C++], current working
ms.assetid: 888dc8c6-5595-4071-be55-816b38e3e739
ms.openlocfilehash: 4c533f0e716cb9a13c152b9be3c46f60291118d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331787"
---
# <a name="getcwd-wgetcwd"></a>_getcwd、_wgetcwd

获取当前工作目录。

## <a name="syntax"></a>语法

```C
char *_getcwd(
   char *buffer,
   int maxlen
);
wchar_t *_wgetcwd(
   wchar_t *buffer,
   int maxlen
);
```

### <a name="parameters"></a>参数

*buffer*<br/>
路径的存储位置。

*maxlen*<br/>
以字符为单位的路径的最大长度： **char**有关 **_getcwd**并**wchar_t**有关 **_wgetcwd**。

## <a name="return-value"></a>返回值

返回一个指向*缓冲区*。 一个**NULL**返回值指示错误，并**errno**设置为**ENOMEM**，，该值指示是否有足够的内存来分配*maxlen*字节 (时**NULL**参数指定为*缓冲区*)，或设置为**ERANGE**，指示路径的长度超过*maxlen*字符。 如果*maxlen*小于或等于零，此函数调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。

有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Getcwd**函数获取默认驱动器的当前工作目录的完整路径，并将其存储在*缓冲区*。 整数自变量*maxlen*指定路径的最大长度。 如果路径 （包括终止 null 字符） 的长度超过了出错*maxlen*。 *缓冲区*参数可以是**NULL**; 的大小至少缓冲区*maxlen* （仅在必需时超过） 自动分配，使用**malloc**，以存储路径。 更高版本可以通过调用释放此缓冲区**免费**并将其传递 **_getcwd**返回值 （指向已分配的缓冲区的指针）。

**_getcwd**返回一个字符串，表示当前工作目录的路径。 如果当前工作目录为根目录，该字符串以反斜杠结尾 ( **\\** )。 如果当前工作目录为根目录之外的目录，则字符串以目录名称结尾，而不是以反斜杠结尾。

**_wgetcwd**是宽字符版本 **_getcwd**;*缓冲区*参数和返回值 **_wgetcwd**都是宽字符字符串。 **_wgetcwd**并 **_getcwd**行为相同。

当 **_DEBUG**和 **_CRTDBG_MAP_ALLOC**定义，则调用 **_getcwd**并 **_wgetcwd**对的调用替换为 **_getcwd_dbg**并 **_wgetcwd_dbg**以便调试内存分配。 有关详细信息，请参阅 [_getcwd_dbg, _wgetcwd_dbg](getcwd-dbg-wgetcwd-dbg.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd**|**_getcwd**|**_getcwd**|**_wgetcwd**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_getcwd**|\<direct.h>|
|**_wgetcwd**|\<direct.h> 或 \<wchar.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_getcwd.c
// This program places the name of the current directory in the
// buffer array, then displays the name of the current directory
// on the screen. Passing NULL as the buffer forces getcwd to allocate
// memory for the path, which allows the code to support file paths
// longer than _MAX_PATH, which are supported by NTFS.

#include <direct.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char* buffer;

   // Get the current working directory:
   if( (buffer = _getcwd( NULL, 0 )) == NULL )
      perror( "_getcwd error" );
   else
   {
      printf( "%s \nLength: %d\n", buffer, strnlen(buffer) );
      free(buffer);
   }
}
```

```Output
C:\Code
```

## <a name="see-also"></a>请参阅

[目录控制](../../c-runtime-library/directory-control.md)<br/>
[_chdir、_wchdir](chdir-wchdir.md)<br/>
[_mkdir、_wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir、_wrmdir](rmdir-wrmdir.md)<br/>
