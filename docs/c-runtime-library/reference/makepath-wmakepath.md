---
title: "_makepath、_wmakepath | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _makepath
- _wmakepath
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
- _wmakepath
- _tmakepath
- makepath
- tmakepath
- wmakepath
- _makepath
dev_langs: C++
helpviewer_keywords:
- _makepath function
- wmakepath function
- makepath function
- _tmakepath function
- paths
- _wmakepath function
- tmakepath function
ms.assetid: 5930b197-a7b8-46eb-8519-2841a58cd026
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b811d4c851ae3c4949378512f5117d0809e8f1e6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="makepath-wmakepath"></a>_makepath、_wmakepath
从组件创建路径名。 提供这些函数的更多安全版本；请参阅 [_makepath_s、_wmakepath_s](../../c-runtime-library/reference/makepath-s-wmakepath-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
void _makepath(  
   char *path,  
   const char *drive,  
   const char *dir,  
   const char *fname,  
   const char *ext   
);  
void _wmakepath(  
   wchar_t *path,  
   const wchar_t *drive,  
   const wchar_t *dir,  
   const wchar_t *fname,  
   const wchar_t *ext   
);  
```  
  
#### <a name="parameters"></a>参数  
 `path`  
 完整路径缓冲区。  
  
 `drive`  
 包含一个与所需的驱动器对应的字母（A、B 等）和可选的尾随冒号。 如果缺少冒号，则 `_makepath` 会自动在复合路径中插入冒号。 如果 `drive` 为 `NULL` 或指向空字符串，则在复合 `path` 字符串中不会显示驱动器号。  
  
 `dir`  
 包含目录路径，但不包括驱动器指示符或实际文件名。 尾随斜杠是可选的，可能会在单个 `dir` 参数中使用正斜杠 (/) 或反斜杠 (\\)，或者同时使用这两种斜杠。 如果未指定尾随斜杠（\ 或 \\），将自动插入。 如果 `dir` 为 `NULL` 或指向空字符串，则在复合 `path` 字符串中不会插入目录路径。  
  
 `fname`  
 包含无任何文件扩展名的基文件名。 如果 `fname` 为 `NULL` 或指向空字符串，则在复合 `path` 字符串中不会插入文件名。  
  
 `ext`  
 包含实际的文件扩展名（带有或不带前导句点 (.)）。 如果 `_makepath` 中未显示句点，则 `ext` 会自动插入句点。 如果 `ext` 为 `NULL` 或指向空字符串，则在复合 `path` 字符串中不会插入扩展名。  
  
## <a name="remarks"></a>备注  
 `_makepath` 函数从各个组件创建复合路径字符串，并将结果存储在 `path` 中。 `path` 可能包括驱动器号、目录路径、文件名和文件扩展名。 `_wmakepath` 是 `_makepath` 的宽字符版本；`_wmakepath` 的参数是宽字符串。 除此以外，`_wmakepath` 和 `_makepath` 的行为完全相同。  
  
 **安全说明** 使用以 null 结尾的字符串。 若要避免缓存区溢出，以 null 结尾的字符串不能超过 `path` 缓冲区的大小。 `_makepath` 不能确保复合路径字符串的长度不超出 `_MAX_PATH`。 有关详细信息，请参阅 [避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tmakepath`|`_makepath`|`_makepath`|`_wmakepath`|  
  
 `path` 参数必须指向一个大小足以容纳完整路径的空缓冲区。 复合 `path` 必须不能大于在 Stdlib.h 中定义的 `_MAX_PATH` 常数。  
  
 如果路径是 `NULL`，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 此外，`errno` 将设置为 `EINVAL`。 所有其他参数可设置为 `NULL` 值。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_makepath`|\<stdlib.h>|  
|`_wmakepath`|\<stdlib.h> 或 \<wchar.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
```  
// crt_makepath.c  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char path_buffer[_MAX_PATH];  
   char drive[_MAX_DRIVE];  
   char dir[_MAX_DIR];  
   char fname[_MAX_FNAME];  
   char ext[_MAX_EXT];  
  
   _makepath( path_buffer, "c", "\\sample\\crt\\", "makepath", "c" ); // C4996  
   // Note: _makepath is deprecated; consider using _makepath_s instead  
   printf( "Path created with _makepath: %s\n\n", path_buffer );  
   _splitpath( path_buffer, drive, dir, fname, ext ); // C4996  
   // Note: _splitpath is deprecated; consider using _splitpath_s instead  
   printf( "Path extracted with _splitpath:\n" );  
   printf( "  Drive: %s\n", drive );  
   printf( "  Dir: %s\n", dir );  
   printf( "  Filename: %s\n", fname );  
   printf( "  Ext: %s\n", ext );  
}  
```  
  
```Output  
Path created with _makepath: c:\sample\crt\makepath.c  
  
Path extracted with _splitpath:  
  Drive: c:  
  Dir: \sample\crt\  
  Filename: makepath  
  Ext: .c  
```  
  
## <a name="see-also"></a>请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [_fullpath、_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [_splitpath、_wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)   
 [_makepath_s、_wmakepath_s](../../c-runtime-library/reference/makepath-s-wmakepath-s.md)