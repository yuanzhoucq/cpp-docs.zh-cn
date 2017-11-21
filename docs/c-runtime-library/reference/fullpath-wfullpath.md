---
title: "_fullpath、_wfullpath | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- _wfullpath function
- relative file paths
- absolute paths
- wfullpath function
- _fullpath function
- fullpath function
ms.assetid: 4161ec17-0d22-45dd-b07d-0222553afae9
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1a1cc6a80609828d084b56ef4f981c9d03de8070
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="fullpath-wfullpath"></a>_fullpath、_wfullpath
创建指定相对路径名称的绝对或完整路径名称。  
  
## <a name="syntax"></a>语法  
  
```  
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
  
#### <a name="parameters"></a>参数  
 `absPath`  
 指向包含绝对路径名称或完整路径名称的缓冲区的指针或 NULL。  
  
 `relPath`  
 相对路径名称。  
  
 `maxLength`  
 绝对路径名称缓冲区 (`absPath`) 的最大长度。 对于 `_fullpath`，此长度以字节为单位，但是对于 `wchar_t`，此长度以宽字符 (`_wfullpath`) 为单位。  
  
## <a name="return-value"></a>返回值  
 其中每个函数都会返回指向包含绝对路径名称 (`absPath`) 的缓冲区的指针。 如果存在错误（例如，如果在 `relPath` 中传递的值包含一个无效或无法找到的驱动器号，或者创建的绝对路径名称 (`absPath`) 的长度大于 `maxLength`），则该函数将返回 `NULL`。  
  
## <a name="remarks"></a>备注  
 `_fullpath`函数扩展中的相对路径名称`relPath`到其完全限定或绝对路径和存储名称中，这`absPath`。 如果 `absPath` 为 NULL，则使用 `malloc` 分配足够长的缓冲区以容纳路径名称。 调用方负责释放此缓冲区。 相对路径名称指定从当前位置到另一个位置的路径（如当前工作目录："."）。 绝对路径名称是相对路径名称的扩展，表示需要采用完整路径才能从文件系统的根达到所需的位置。 与 `_makepath` 不同，`_fullpath` 可用于获取相对路径的绝对路径名称 (`relPath`)，其中相对路径的名称中包括 "./" 或 "../"。  
  
 例如，若要使用 C 运行时例程，该应用程序必须包括包含例程声明的头文件。 每个头文件包括以相对方式（从应用程序的工作目录）引用文件位置的语句：  
  
```  
#include <stdlib.h>  
```  
  
 当文件的绝对路径（实际的文件系统位置）可能是：  
  
```  
\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h  
```  
  
 `_fullpath` 将根据情况自动处理多字节字符串参数，根据当前正在使用的多字节代码页识别多字节字符序列。 `_wfullpath` 是 `_fullpath` 的宽字符版本；`_wfullpath` 的字符串参数是宽字符字符串。 `_wfullpath` 和 `_fullpath` 的行为方式相同，只不过 `_wfullpath` 不处理多字节字符字符串。  
  
 在定义了 `_DEBUG` 和 `_CRTDBG_MAP_ALLOC` 时，对 `_fullpath` 和 `_wfullpath` 的调用将替代对 `_fullpath_dbg` 和 `_wfullpath_dbg` 的调用，以便调试内存分配。 有关详细信息，请参阅 [_fullpath_dbg、_wfullpath_dbg](../../c-runtime-library/reference/fullpath-dbg-wfullpath-dbg.md)。  
  
 如果 `maxlen` 小于或等于 0，此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将 `errno` 设置为 `EINVAL` 并返回 `NULL`。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tfullpath`|`_fullpath`|`_fullpath`|`_wfullpath`|  
  
 如果 `absPath` 缓冲区为 `NULL`，`_fullpath` 调用 [malloc](../../c-runtime-library/reference/malloc.md) 来分配缓冲区，并忽略 `maxLength` 参数。 调用方负责视情况解除分配此缓冲区（使用 [free](../../c-runtime-library/reference/free.md)）。 如果 `relPath` 参数指定一个磁盘驱动器，则该驱动器的当前目录结合使用此路径。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`_fullpath`|\<stdlib.h>|  
|`_wfullpath`|\<stdlib.h> 或 \<wchar.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
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
 [文件处理](../../c-runtime-library/file-handling.md)   
 [_getcwd、_wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [_getdcwd、_wgetdcwd](../../c-runtime-library/reference/getdcwd-wgetdcwd.md)   
 [_makepath、_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)   
 [_splitpath、_wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)