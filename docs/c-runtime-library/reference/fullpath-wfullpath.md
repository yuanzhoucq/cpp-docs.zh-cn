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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 0910cf4f39e00be84e683cd6f3b9afbeb3f2a749
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345487"
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
指向包含绝对或完整路径名称的缓冲区的指针，或**NULL**。

*relPath*<br/>
相对路径名称。

*maxLength*<br/>
绝对路径名称缓冲区 *（absPath*） 的最大长度。 此长度以字节为单位 **_fullpath**但宽字符 **（wchar_t）** 表示 **_wfullpath**。

## <a name="return-value"></a>返回值

每个函数返回一个指向包含绝对路径名称 *（absPath*） 的缓冲区的指针。 如果出现错误（例如，如果*relPath*中传递的值包含无效或找不到的驱动器号，或者如果创建的绝对路径名称 *（absPath）* 的长度大于*maxLength），* 则函数返回**NULL**。

## <a name="remarks"></a>备注

**_fullpath**函数将*relPath*中的相对路径名称扩展到其完全限定或绝对路径，并将此名称存储在*absPath*中。 如果*absPath*为**NULL，****则 malloc**用于分配足够长度的缓冲区来保存路径名称。 调用方负责释放此缓冲区。 相对路径名称指定从当前位置到另一个位置的路径（如当前工作目录："."）。 绝对路径名称是相对路径名称的扩展，表示需要采用完整路径才能从文件系统的根达到所需的位置。 **与_makepath****不同，_fullpath**可用于获取包含"./"或"的相对路径 *（relPath）* 的绝对路径名称。/" 以他们的名字。

例如，若要使用 C 运行时例程，该应用程序必须包括包含例程声明的头文件。 每个头文件包括以相对方式（从应用程序的工作目录）引用文件位置的语句：

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#include <stdlib.h>
```

当文件的绝对路径（实际的文件系统位置）可能是：

`\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h`

**_fullpath**根据需要自动处理多字节字符串参数，根据当前使用的多字节代码页识别多字节字符序列。 **_wfullpath**是 **_fullpath**的宽字符版本;要 **_wfullpath**的字符串参数是宽字符字符串。 **_wfullpath****和_fullpath**行为相同，只是 **_wfullpath**不处理多字节字符串。

如果定义了 **_DEBUG**和 **_CRTDBG_MAP_ALLOC，** 则对 **_fullpath**和 **_wfullpath**的调用将替换为对 **_fullpath_dbg**和 **_wfullpath_dbg**的调用，以允许调试内存分配。 有关详细信息，请参阅 [_fullpath_dbg、_wfullpath_dbg](fullpath-dbg-wfullpath-dbg.md)。

如果*maxlen*小于或等于 0，则此函数调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，此函数将**errno**设置到**EINVAL**并返回**NULL**。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath**|**_fullpath**|**_fullpath**|**_wfullpath**|

如果*absPath*缓冲区为**NULL，_fullpath**调用[malloc](malloc.md)来分配缓冲区并忽略*maxLength 参数*。 **NULL** 调用方负责视情况解除分配此缓冲区（使用 [free](free.md)）。 如果*relPath*参数指定磁盘驱动器，则此驱动器的当前目录将与路径合并。

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
