---
title: "_makepath_s、_wmakepath_s | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wmakepath_s"
  - "_makepath_s"
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
  - "_wmakepath_s"
  - "makepath_s"
  - "_makepath_s"
  - "wmakepath_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_makepath_s 函数"
  - "wmakepath_s 函数"
  - "路径"
  - "_wmakepath_s 函数"
  - "makepath_s 函数"
ms.assetid: 4405e43c-3d63-4697-bb80-9b8dcd21d027
caps.latest.revision: 29
caps.handback.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _makepath_s、_wmakepath_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从组件创建路径名。  [\_makepath, \_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)[CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述）。  
  
## 语法  
  
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
  
#### 参数  
 \[out\] `path`  
 完整路径缓冲区。  
  
 \[in\] `sizeInWords`  
 缓冲区的字大小。  
  
 \[in\] `sizeInBytes`  
 缓冲区的大小（以字节为单位）。  
  
 \[in\] `drive`  
 包含与预期驱动器和一个选项尾部冒号对应的字母\(A，B 等\) 。  如果它丢失，`_makepath_s` 在复合路径自动插入冒号。  如果 `drive` 是`NULL` 或指向空字符串，在复合 `path` 字符串不显示驱动器号。  
  
 \[in\] `dir`  
 包含目录路径，不包括驱动器指示符或实际的文件名。  尾部斜杠是可选的，并且，对于一个正斜杠 \(\/\) 和反斜杠 \(\\\) 或两者都可能用在单个 `dir` 参数中。  如果尾部斜杠 \(\\或\/\) 未指定，它被自动插入。  如果 `dir` 是`NULL` 或指向空字符串，则在复合 `path` 字符串中不插入目录路径。  
  
 \[in\] `fname`  
 包含无任何文件扩展名的基文件名。  如果 `fname` 是`NULL` 或指向空字符串，则在复合 `path` 字符串中不插入文件名。  
  
 \[in\] `ext`  
 包含实际文件扩展名，带或不带前导的句点 \(.\)。  如果不出现在 `ext`，`_makepath_s` 会自动插入时间。  如果 `ext` 是`NULL` 或指向空字符串，则在复合 `path` 字符串中不插入扩展。  
  
## 返回值  
 如果成功，则为零；如果失败，则为错误代码。  
  
### 错误情况  
  
|`path`|`sizeInWords` \/ `sizeInBytes`|返回|`path` 的内容|  
|------------|------------------------------------|--------|----------------|  
|`NULL`|any|`EINVAL`|未修改|  
|any|\<\= 0|`EINVAL`|未修改|  
  
 如果任一以上错误状态发生，这些函数调用无效参数句柄，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，将`errno` 设置为`EINVAL`，并且函数返回`EINVAL`**.** `NULL` 允许参数 `drive`、`fname`和 `ext`。  当这些参数是 null 指针或空字符串时，有关行为的信息，请参见"备注"一节。  
  
## 备注  
 `_makepath_s` 函数在单个组件中创建复合路径字符串，在`path`中存储结果。  `path` 可以包括驱动器号、目录路径、文件名和文件名扩展。  `_wmakepath_s` 是 `_makepath_s` 的宽字符版本；`_wmakepath_s` 的参数是宽字符串。  `_wmakepath_s` 和 `_makepath_s` 行为相同，否则。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tmakepath_s`|`_makepath_s`|`_makepath_s`|`_wmakepath_s`|  
  
 参数 `path` 必须指向足够大空缓冲区以容纳完整路径。  复合 `path` 必须大于 `_MAX_PATH` 常数，在 Stdlib.h中定义。  
  
 如果路径是 `NULL`，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)所述。  此外，将`errno` 设置为 `EINVAL`。  `NULL` 值允许所有其他参数。  
  
 在 C\+\+ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 \(不再需要指定大小参数\)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
 这些函数的调试版本首先用 0xFD 填充缓冲区。  若要禁用此行为，请使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_makepath_s`|\<stdlib.h\>|  
|`_wmakepath_s`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
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
  
## Output  
  
```  
Path created with _makepath_s: c:\sample\crt\crt_makepath_s.c  
  
Path extracted with _splitpath_s:  
  Drive: c:  
  Dir: \sample\crt\  
  Filename: crt_makepath_s  
  Ext: .c  
```  
  
## .NET Framework 等效项  
 [System::IO::File::Create](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)  
  
## 请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [\_fullpath、\_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [\_splitpath\_s、\_wsplitpath\_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)   
 [\_makepath、\_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)