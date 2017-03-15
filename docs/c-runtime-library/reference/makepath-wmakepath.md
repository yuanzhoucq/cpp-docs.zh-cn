---
title: "_makepath、_wmakepath | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_makepath"
  - "_wmakepath"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_wmakepath"
  - "_tmakepath"
  - "makepath"
  - "tmakepath"
  - "wmakepath"
  - "_makepath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_makepath 函数"
  - "_tmakepath 函数"
  - "_wmakepath 函数"
  - "makepath 函数"
  - "路径"
  - "tmakepath 函数"
  - "wmakepath 函数"
ms.assetid: 5930b197-a7b8-46eb-8519-2841a58cd026
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# _makepath、_wmakepath
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建组件的路径名。  提供这些函数的更多安全版本；请参见 [\_makepath\_s、\_wmakepath\_s](../../c-runtime-library/reference/makepath-s-wmakepath-s.md)。  
  
## 语法  
  
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
  
#### 参数  
 `path`  
 完整路径缓冲区。  
  
 `drive`  
 包含与预期驱动器和一个选项尾部冒号对应的字母\(A，B 等\) 。  如果它丢失，`_makepath` 在复合路径自动插入冒号。  如果 `drive` 是`NULL` 或指向空字符串，在复合 `path` 字符串不显示驱动器号。  
  
 `dir`  
 包含目录路径，不包括驱动器指示符或实际的文件名。  尾部斜杠是可选的，并且，对于一个正斜杠 \(\/\) 和反斜杠 \(\\\) 或两者都可能用在单个 `dir` 参数中。  如果尾部斜杠 \(\\或\/\) 未指定，它被自动插入。  如果 `dir` 是`NULL` 或指向空字符串，则在复合 `path` 字符串中不插入目录路径。  
  
 `fname`  
 包含无任何文件扩展名的基文件名。  如果 `fname` 是`NULL` 或指向空字符串，则在复合 `path` 字符串中不插入文件名。  
  
 `ext`  
 包含实际文件扩展名，带或不带前导的句点 \(.\)。  如果不出现在 `ext`，`_makepath` 会自动插入时间。  如果 `ext` 是`NULL` 或指向空字符串，则在复合 `path` 字符串中不插入扩展。  
  
## 备注  
 `_makepath` 函数在单个组件中创建复合路径字符串，在`path`中存储结果。  `path` 可以包括驱动器号、目录路径、文件名和文件名扩展。  `_wmakepath` 是 `_makepath` 的宽字符版本；`_wmakepath` 的参数是宽字符串。  `_wmakepath` 和 `_makepath` 行为相同，否则。  
  
 **Security Note**使用以 NULL 结尾的字符串。  若要避免缓冲区溢出，以 null 终止的字符串不能超过 `path` 缓冲区的大小。  `_makepath` 不保证复合路径字符串的长度不超过 `_MAX_PATH`。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tmakepath`|`_makepath`|`_makepath`|`_wmakepath`|  
  
 参数 `path` 必须指向足够大空缓冲区以容纳完整路径。  复合 `path` 必须大于 `_MAX_PATH` 常数，在 Stdlib.h中定义。  
  
 如果路径是 `NULL`，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)所述。  此外，将`errno` 设置为 `EINVAL`。  `NULL` 值允许所有其他参数。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_makepath`|\<stdlib.h\>|  
|`_wmakepath`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
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
  
  **创建\_makepath: c:\\sample\\crt\\makepath.c路径**  
**路径获取 \_splitpath:**  
 **驱动器: c:**  
 **目录: \\sample\\crt\\**  
 **文件名：makepath**  
 **Ext: .c**   
## .NET Framework 等效项  
 [System::IO::File::Create](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)  
  
## 请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [\_fullpath、\_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [\_splitpath、\_wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)   
 [\_makepath\_s、\_wmakepath\_s](../../c-runtime-library/reference/makepath-s-wmakepath-s.md)