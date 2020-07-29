---
title: _fullpath、_wfullpath
ms.date: 4/2/2020
api_name:
- _fullpath
- _wfullpath
- _o__fullpath
- _o__wfullpath
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wfullpath
- fullpath
- _wfullpath
- _fullpath
helpviewer_keywords:
- _wfullpath function
- relative file paths
- absolute paths
- wfullpath function
- _fullpath function
- fullpath function
ms.assetid: 4161ec17-0d22-45dd-b07d-0222553afae9
ms.openlocfilehash: 8583ea17930721f8d8b80aa5066dbc07372ce243
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231385"
---
# <a name="_fullpath-_wfullpath"></a>_fullpath、_wfullpath

创建指定相对路径名称的绝对或完整路径名称。

## <a name="syntax"></a>语法

```C
char *_fullpath(
   char *absPath,
   const char *relPath,
   size_t maxLength
);
wchar_t *_wfullpath(
   wchar_t *absPath,
   const wchar_t *relPath,
   size_t maxLength
);
```

### <a name="parameters"></a>参数

*absPath*<br/>
指向包含绝对或完整路径名称的缓冲区的指针或**NULL**。

*relPath*<br/>
相对路径名称。

*maxLength*<br/>
绝对路径名称缓冲区的最大长度（*absPath*）。 对于 **_fullpath** ，此长度以字节为单位，但是 **`wchar_t`** 对于 **_wfullpath**，为宽字符（）。

## <a name="return-value"></a>返回值

其中每个函数都会返回指向包含绝对路径名称（*absPath*）的缓冲区的指针。 如果出现错误（例如，如果*relPath*中传递的值包含一个无效或无法找到的驱动器号，或者创建的绝对路径名称（*absPath*）的长度大于*maxLength*，则该函数将返回**NULL**。

## <a name="remarks"></a>备注

**_Fullpath**函数将*relPath*中的相对路径名称扩展为其完全限定路径或绝对路径，并将此名称存储在*absPath*中。 如果*absPath*为**NULL**，则使用**malloc**分配足够长度的缓冲区来容纳路径名称。 调用方负责释放此缓冲区。 相对路径名称指定从当前位置到另一个位置的路径（如当前工作目录："."）。 绝对路径名称是相对路径名称的扩展，表示需要采用完整路径才能从文件系统的根达到所需的位置。 与 **_makepath**不同， **_fullpath**可用于获取相对路径（*relPath*）的绝对路径名，其中包含 "./" 或 ".。。/"。

例如，若要使用 C 运行时例程，该应用程序必须包括包含例程声明的头文件。 每个头文件包括以相对方式（从应用程序的工作目录）引用文件位置的语句：

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#include <stdlib.h>
```

当文件的绝对路径（实际的文件系统位置）可能是：

`\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h`

**_fullpath**会根据需要自动处理多字节字符串参数，根据当前使用的多字节代码页识别多字节字符序列。 **_wfullpath**是 **_fullpath**的宽字符版本;**_wfullpath**的字符串参数是宽字符字符串。 **_wfullpath**和 **_fullpath**的行为相同，只是 **_wfullpath**不处理多字节字符字符串。

如果同时定义了 **_DEBUG**和 **_CRTDBG_MAP_ALLOC** ，则对 **_fullpath_dbg**和 **_wfullpath_dbg**的调用将替换对 **_fullpath**和 **_wfullpath**的调用，以便调试内存分配。 有关详细信息，请参阅 [_fullpath_dbg、_wfullpath_dbg](fullpath-dbg-wfullpath-dbg.md)。

如果*maxlen*小于或等于0，此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数会将**errno**设置为**EINVAL** ，并返回**NULL**。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath**|**_fullpath**|**_fullpath**|**_wfullpath**|

如果*absPath*缓冲区为**NULL**， **_fullpath**将调用[Malloc](malloc.md)来分配缓冲区，并忽略*maxLength*参数。 调用方负责视情况解除分配此缓冲区（使用 [free](free.md)）。 如果*relPath*参数指定了磁盘驱动器，则该驱动器的当前目录将与路径组合在一起。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_fullpath**|\<stdlib.h>|
|**_wfullpath**|\<stdlib.h> 或 \<wchar.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_fullpath.c
// This program demonstrates how _fullpath
// creates a full path from a partial path.

#include <stdio.h>
#include <conio.h>
#include <stdlib.h>
#include <direct.h>

void PrintFullPath( char * partialPath )
{
   char full[_MAX_PATH];
   if( _fullpath( full, partialPath, _MAX_PATH ) != NULL )
      printf( "Full path is: %s\n", full );
   else
      printf( "Invalid path\n" );
}

int main( void )
{
   PrintFullPath( "test" );
   PrintFullPath( "\\test" );
   PrintFullPath( "..\\test" );
}
```

```Output
Full path is: C:\Documents and Settings\user\My Documents\test
Full path is: C:\test
Full path is: C:\Documents and Settings\user\test
```

## <a name="see-also"></a>另请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_getcwd、_wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdcwd、_wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[_makepath、_wmakepath](makepath-wmakepath.md)<br/>
[_splitpath、_wsplitpath](splitpath-wsplitpath.md)<br/>
