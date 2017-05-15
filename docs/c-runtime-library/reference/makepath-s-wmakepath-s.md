---
title: "_makepath_s、_wmakepath_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wmakepath_s
- _makepath_s
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
- _wmakepath_s
- makepath_s
- _makepath_s
- wmakepath_s
dev_langs:
- C++
helpviewer_keywords:
- _makepath_s function
- wmakepath_s function
- paths
- _wmakepath_s function
- makepath_s function
ms.assetid: 4405e43c-3d63-4697-bb80-9b8dcd21d027
caps.latest.revision: 29
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 0d3ac02a0ac8dfa7f681c8585be7e1b6f41f0f82
ms.contentlocale: zh-cn
ms.lasthandoff: 04/04/2017

---
# <a name="makepaths-wmakepaths"></a>_makepath_s、_wmakepath_s
从组件创建路径名。 这些版本的 [_makepath、_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t _makepath_s(  
   char *path,  
   size_t sizeInBytes,  
   const char *drive,  
   const char *dir,  
   const char *fname,  
   const char *ext   
);  
errno_t _wmakepath_s(  
   wchar_t *path,  
   size_t sizeInWords,  
   const wchar_t *drive,  
   const wchar_t *dir,  
   const wchar_t *fname,  
   const wchar_t *ext   
);  
template <size_t size>  
errno_t _makepath_s(  
   char (&path)[size],  
   const char *drive,  
   const char *dir,  
   const char *fname,  
   const char *ext   
); // C++ only  
template <size_t size>  
errno_t _wmakepath_s(  
   wchar_t (&path)[size],  
   const wchar_t *drive,  
   const wchar_t *dir,  
   const wchar_t *fname,  
   const wchar_t *ext   
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 [out] `path`  
 完整路径缓冲区。  
  
 [in] `sizeInWords`  
 缓冲区大小（以单词为单位）。  
  
 [in] `sizeInBytes`  
 缓冲区的大小（以字节为单位）。  
  
 [in] `drive`  
 包含一个与所需的驱动器对应的字母（A、B 等）和可选的尾随冒号。 如果缺少冒号，则 `_makepath_s` 会自动在复合路径中插入冒号。 如果 `drive` 为 `NULL` 或指向空字符串，则在复合 `path` 字符串中不会显示驱动器号。  
  
 [in] `dir`  
 包含目录路径，但不包括驱动器指示符或实际文件名。 尾随斜杠是可选的，可能会在单个 `dir` 参数中使用正斜杠 (/) 或反斜杠 (\\)，或者同时使用这两种斜杠。 如果未指定尾随斜杠（\ 或 \\），将自动插入。 如果 `dir` 为 `NULL` 或指向空字符串，则在复合 `path` 字符串中不会插入目录路径。  
  
 [in] `fname`  
 包含无任何文件扩展名的基文件名。 如果 `fname` 为 `NULL` 或指向空字符串，则在复合 `path` 字符串中不会插入文件名。  
  
 [in] `ext`  
 包含实际的文件扩展名（带有或不带前导句点 (.)）。 如果 `_makepath_s` 中未显示句点，则 `ext` 会自动插入句点。 如果 `ext` 为 `NULL` 或指向空字符串，则在复合 `path` 字符串中不会插入扩展名。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为零；如果失败，则为错误代码。  
  
### <a name="error-conditions"></a>错误条件  
  
|`path`|`sizeInWords` / `sizeInBytes`|返回|`path` 的内容|  
|------------|------------------------------------|------------|------------------------|  
|`NULL`|任何|`EINVAL`|未修改|  
|any|<= 0|`EINVAL`|未修改|  
  
 如果发生任何以上错误情况，则这些函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则将 `errno` 设置为 `EINVAL` 并且函数将返回 `EINVAL`。 允许参数 `drive`、`fname`、和 `ext` 为 `NULL`。 有关当这些参数是 null 指针或空字符串时的行为的信息，请参见“备注”部分。  
  
## <a name="remarks"></a>备注  
 `_makepath_s` 函数从各个组件创建复合路径字符串，并将结果存储在 `path` 中。 `path` 可能包括驱动器号、目录路径、文件名和文件扩展名。 `_wmakepath_s` 是 `_makepath_s` 的宽字符版本；`_wmakepath_s` 的参数是宽字符串。 除此以外，`_wmakepath_s` 和 `_makepath_s` 的行为完全相同。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tmakepath_s`|`_makepath_s`|`_makepath_s`|`_wmakepath_s`|  
  
 `path` 参数必须指向一个大小足以容纳完整路径的空缓冲区。 复合 `path` 必须不能大于在 Stdlib.h 中定义的 `_MAX_PATH` 常数。  
  
 如果路径是 `NULL`，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 此外，`errno` 将设置为 `EINVAL`。 所有其他参数可设置为 `NULL` 值。  
  
 在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
 这些函数的调试版本首先用 0xFD 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_makepath_s`|\<stdlib.h>|  
|`_wmakepath_s`|\<stdlib.h> 或 \<wchar.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_makepath_s.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char path_buffer[_MAX_PATH];  
   char drive[_MAX_DRIVE];  
   char dir[_MAX_DIR];  
   char fname[_MAX_FNAME];  
   char ext[_MAX_EXT];  
   errno_t err;  
  
   err = _makepath_s( path_buffer, _MAX_PATH, "c", "\\sample\\crt\\",  
                      "crt_makepath_s", "c" );  
   if (err != 0)  
   {  
      printf("Error creating path. Error code %d.\n", err);  
      exit(1);  
   }  
   printf( "Path created with _makepath_s: %s\n\n", path_buffer );  
   err = _splitpath_s( path_buffer, drive, _MAX_DRIVE, dir, _MAX_DIR, fname,  
                       _MAX_FNAME, ext, _MAX_EXT );  
   if (err != 0)  
   {  
      printf("Error splitting the path. Error code %d.\n", err);  
      exit(1);  
   }  
   printf( "Path extracted with _splitpath_s:\n" );  
   printf( "  Drive: %s\n", drive );  
   printf( "  Dir: %s\n", dir );  
   printf( "  Filename: %s\n", fname );  
   printf( "  Ext: %s\n", ext );  
}  
```  
  
## <a name="output"></a>输出  
  
```  
Path created with _makepath_s: c:\sample\crt\crt_makepath_s.c  
  
Path extracted with _splitpath_s:  
  Drive: c:  
  Dir: \sample\crt\  
  Filename: crt_makepath_s  
  Ext: .c  
```  
  
## <a name="see-also"></a>另请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [_fullpath、_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [_splitpath_s、_wsplitpath_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)   
 [_makepath、_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)
