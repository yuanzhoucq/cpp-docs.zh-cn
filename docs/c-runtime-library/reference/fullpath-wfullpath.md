---
title: _fullpath、_wfullpath
ms.date: 11/04/2016
apiname:
- _fullpath
- _wfullpath
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: aeacaf581b7f33ee893754c192ae547376ce73ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550392"
---
# <a name="fullpath-wfullpath"></a>_fullpath、_wfullpath

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

*MaxLength*<br/>
绝对路径名称缓冲区的最大长度 (*absPath*)。 此长度以字节为单位的 **_fullpath**但以宽字符 (**wchar_t**) 的 **_wfullpath**。

## <a name="return-value"></a>返回值

每个函数返回指向包含绝对路径名称的缓冲区的指针 (*absPath*)。 如果出现错误 (例如，如果中传递的值*relPath*包含一个驱动器号无效或找不到，或者，如果创建的绝对路径名称的长度 (*absPath*) 大于*maxLength*)，该函数将返回**NULL**。

## <a name="remarks"></a>备注

**_Fullpath**函数可展开中的相对路径名称*relPath*到其完全限定或绝对路径和中存储此名称*absPath*。 如果*absPath*是**NULL**， **malloc**用于分配的缓冲区长度足以容纳路径名称。 调用方负责释放此缓冲区。 相对路径名称指定从当前位置到另一个位置的路径（如当前工作目录："."）。 绝对路径名称是相对路径名称的扩展，表示需要采用完整路径才能从文件系统的根达到所需的位置。 与不同 **_makepath**， **_fullpath**可用于获取相对路径的绝对路径名称 (*relPath*)，包括"。 /".../"在其名称中。

例如，若要使用 C 运行时例程，该应用程序必须包括包含例程声明的头文件。 每个头文件包括以相对方式（从应用程序的工作目录）引用文件位置的语句：

```C
#include <stdlib.h>
```

当文件的绝对路径（实际的文件系统位置）可能是：

`\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h`

**_fullpath**自动处理多字节字符字符串参数，根据需要，根据当前正在使用的多字节代码页识别多字节字符序列。 **_wfullpath**是宽字符版本 **_fullpath**; 的字符串参数 **_wfullpath**都是宽字符字符串。 **_wfullpath**并 **_fullpath**行为方式相同，只不过 **_wfullpath**不处理多字节字符字符串。

如果 **_DEBUG**并 **_CRTDBG_MAP_ALLOC**都是定义，对调用 **_fullpath**并 **_wfullpath** 对的调用替换为 **_fullpath_dbg**并 **_wfullpath_dbg**以便调试内存分配。 有关详细信息，请参阅 [_fullpath_dbg、_wfullpath_dbg](fullpath-dbg-wfullpath-dbg.md)。

此函数将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)，则*maxlen*小于或等于 0。 如果允许执行继续，此函数可设置**errno**到**EINVAL** ，并返回**NULL**。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath**|**_fullpath**|**_fullpath**|**_wfullpath**|

如果*absPath*缓冲区**NULL**， **_fullpath**调用[malloc](malloc.md)来分配缓冲区，并忽略*maxLength*参数。 调用方负责视情况解除分配此缓冲区（使用 [free](free.md)）。 如果*relPath*参数指定的磁盘驱动器，此驱动器的当前目录结合使用的路径。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_fullpath**|\<stdlib.h>|
|**_wfullpath**|\<stdlib.h> 或 \<wchar.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_getcwd、_wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdcwd、_wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[_makepath、_wmakepath](makepath-wmakepath.md)<br/>
[_splitpath、_wsplitpath](splitpath-wsplitpath.md)<br/>
