---
title: "_getcwd、_wgetcwd | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- getcwd function
- working directory
- _wgetcwd function
- _getcwd function
- current working directory
- wgetcwd function
- directories [C++], current working
ms.assetid: 888dc8c6-5595-4071-be55-816b38e3e739
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e72618467666a98bdda5867b23d9ef2ce37319f2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="getcwd-wgetcwd"></a>_getcwd、_wgetcwd
获取当前工作目录。  
  
## <a name="syntax"></a>语法  
  
```  
char *_getcwd(   
   char *buffer,  
   int maxlen   
);  
wchar_t *_wgetcwd(   
   wchar_t *buffer,  
   int maxlen   
);  
```  
  
#### <a name="parameters"></a>参数  
 `buffer`  
 路径的存储位置。  
  
 `maxlen`  
 路径的最大长度（以字符为单位）：`char` 的 `_getcwd` 和 `wchar_t` 的 `_wgetcwd`。  
  
## <a name="return-value"></a>返回值  
 返回指向 `buffer`的指针。 `NULL` 返回值指示错误，并将 `errno` 设置为 `ENOMEM`，指示内存不足，无法分配 `maxlen` 个字节（当将 `NULL` 参数给定为 `buffer`时），或设置为 `ERANGE`，指示该路径长于 `maxlen` 个字符。 如果 `maxlen` 小于或等于零，则此函数调用无效的参数处理程序，如 [Parameter Validation](../../c-runtime-library/parameter-validation.md)。  
  
 有关这些代码及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 `_getcwd` 函数获取默认驱动器的当前工作目录的完整路径，并将其存储在 `buffer`中。 整数参数 `maxlen` 指定路径的最大长度。 如果路径 （包括终止 null 字符） 的长度超过，则会发生错误`maxlen`。 `buffer` 参数可为 `NULL`；使用 `malloc` 自动分配大小至少为 `maxlen`（仅在必需时超过）的缓冲区，以存储路径。 之后可通过调用 `free` 并向其传递 `_getcwd` 返回值（指向已分配缓冲区的指针）来释放此缓冲区。  
  
 `_getcwd` 返回一个字符串，它表示当前工作目录的路径。 如果当前工作目录为根目录，则字符串以反斜杠 ( `\` ) 结尾。 如果当前工作目录为根目录之外的目录，则字符串以目录名称结尾，而不是以反斜杠结尾。  
  
 `_wgetcwd` 是 `_getcwd`的宽字符版本； `buffer` 参数和 `_wgetcwd` 的返回值都是宽字符字符串。 除此以外，`_wgetcwd` 和 `_getcwd` 的行为完全相同。  
  
 在定义了 `_DEBUG` 和 `_CRTDBG_MAP_ALLOC` 时，对 `_getcwd` 和 `_wgetcwd` 的调用将替代对 `_getcwd_dbg` 和 `_wgetcwd_dbg` 的调用，以便调试内存分配。 有关详细信息，请参阅 [_getcwd_dbg, _wgetcwd_dbg](../../c-runtime-library/reference/getcwd-dbg-wgetcwd-dbg.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tgetcwd`|`_getcwd`|`_getcwd`|`_wgetcwd`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_getcwd`|\<direct.h>|  
|`_wgetcwd`|\<direct.h> 或 \<wchar.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
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
  
## <a name="see-also"></a>另请参阅  
 [目录控制](../../c-runtime-library/directory-control.md)   
 [_chdir、_wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [_mkdir、_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [_rmdir、_wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)