---
title: _getcwd、_wgetcwd
description: C 运行时库函数_getcwd，_wgetcwd获取当前工作目录。
ms.date: 4/2/2020
api_name:
- _wgetcwd
- _getcwd
- _o__getcwd
- _o__wgetcwd
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: bc19a416ebebeb901e8dbb435971e6d5f33e4067
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344432"
---
# <a name="_getcwd-_wgetcwd"></a>_getcwd、_wgetcwd

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

*缓冲区*\
路径的存储位置。

*马克斯伦*\
以字符表示路径的最大长度 **：_getcwd**的**字符****，_wgetcwd**的**wchar_t。**

## <a name="return-value"></a>返回值

返回指向缓冲区的*指针*。 **NULL**返回值指示错误 **，errno**设置为**ENOMEM，** 指示内存不足以分配*maxlen*字节（当**NULL**参数作为*缓冲区*时）或**ERANGE，** 指示路径长于*maxlen*字符。 如果*maxlen*小于或等于零，则此函数将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。

有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_getcwd**函数获取默认驱动器当前工作目录的完整路径并将其存储在*缓冲区*中。 整数参数*maxlen*指定路径的最大长度。 如果路径的长度（包括终止空字符）超过*maxlen，* 则会发生错误。 *缓冲区*参数可以是**NULL**;使用**malloc**自动分配至少大小*最大 len*的缓冲区（仅在必要时更多），以存储路径。 稍后可以通过调用**空闲**并传递 **_getcwd**返回值（指向已分配的缓冲区的指针）来释放此缓冲区。

**_getcwd**返回表示当前工作目录路径的字符串。 如果当前工作目录是根目录，则字符串以反斜杠结束 。`\` 如果当前工作目录为根目录之外的目录，则字符串以目录名称结尾，而不是以反斜杠结尾。

**_wgetcwd**是 **_getcwd**的宽字符版本;*缓冲区*参数和 **_wgetcwd**的返回值是宽字符字符串。 **_wgetcwd**和 **_getcwd**行为相同。

定义 **_DEBUG**和 **_CRTDBG_MAP_ALLOC**时，对 **_getcwd**和 **_wgetcwd**的调用将替换为对 **_getcwd_dbg**和 **_wgetcwd_dbg**的调用，以允许调试内存分配。 有关详细信息，请参阅 [_getcwd_dbg, _wgetcwd_dbg](getcwd-dbg-wgetcwd-dbg.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd**|**_getcwd**|**_getcwd**|**_wgetcwd**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_getcwd**|\<direct.h>|
|**_wgetcwd**|\<direct.h> 或 \<wchar.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_getcwd.c
// Compile with: cl /W4 crt_getcwd.c
// This program places the name of the current directory in the
// buffer array, then displays the name of the current directory
// on the screen. Passing NULL as the buffer forces getcwd to allocate
// memory for the path, which allows the code to support file paths
// longer than _MAX_PATH, which are supported by NTFS.

#include <direct.h> // _getcwd
#include <stdlib.h> // free, perror
#include <stdio.h>  // printf
#include <string.h> // strlen

int main( void )
{
   char* buffer;

   // Get the current working directory:
   if ( (buffer = _getcwd( NULL, 0 )) == NULL )
      perror( "_getcwd error" );
   else
   {
      printf( "%s \nLength: %zu\n", buffer, strlen(buffer) );
      free(buffer);
   }
}
```

```Output
C:\Code
```

## <a name="see-also"></a>另请参阅

[目录控制](../../c-runtime-library/directory-control.md)\
[_wchdir，_chdir](chdir-wchdir.md)\
[_mkdir，_wmkdir](mkdir-wmkdir.md)\
[_rmdir、_wrmdir](rmdir-wrmdir.md)
