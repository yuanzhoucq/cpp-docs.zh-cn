---
title: "文件名搜索函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- file names [C++], searching for
- _find function
- wfind function
- find function
- _wfind function
ms.assetid: 2bc2f8ef-44e4-4271-b3e8-666d36fde828
caps.latest.revision: 26
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
translationtype: Human Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: c802f99eab05ea59971c69c53f999f1b8f12240f
ms.lasthandoff: 04/04/2017

---
# <a name="filename-search-functions"></a>文件名搜索函数
这些函数搜索并关闭搜索指定的文件名称：  
  
-   [_findnext、_wfindnext](../c-runtime-library/reference/findnext-functions.md)  
  
-   [_findfirst、_wfindfirst](../c-runtime-library/reference/findfirst-functions.md)  
  
-   [_findclose](../c-runtime-library/reference/findclose.md)  
  
## <a name="remarks"></a>备注  
 `_findfirst` 函数提供与 `filespec` 参数中指定的文件匹配的文件名的第一个实例的有关信息。 可以在 `filespec` 中使用主机操作系统支持的通配符字符的任意组合。  
  
 函数返回在 IO.h. 中定义的 `_finddata_t` 结构中的文件信息。 系列中的各种函数上使用许多不同 `_finddata_t` 结构。 基本 `_finddata_t` 结构包含以下元素：  
  
 `unsigned attrib`  
 文件属性。  
  
 `time_t time_create`  
 文件的创建时间（对于 FAT 文件系统为 -1L）。 该时间以 UTC 格式存储。 若要转换为本地时间，请使用 [localtime_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)。  
  
 `time_t time_access`  
 文件的上次访问时间（对于 FAT 文件系统为 -1L）。 该时间以 UTC 格式存储。 若要转换为本地时间，请使用 `localtime_s`。  
  
 `time_t time_write`  
 文件的上次写入时间。 该时间以 UTC 格式存储。 若要转换为本地时间，请使用 `localtime_s`。  
  
 `_fsize_t size`  
 文件的长度（以字节为单位）。  
  
 `char name`[ `_MAX_PATH`]  
 匹配的文件或目录（不含路径）的以 null 结尾的名称。  
  
 在不支持文件的创建时间和上次访问时间的文件系统中（例如 FAT 系统）， `time_create` 和 `time_access` 字段始终为 -1L。  
  
 `_MAX_PATH` 在 Stdlib.h 中定义为 260 个字节。  
  
 不能指定目标属性（如 `_A_RDONLY`来限制执行查找操作。 这些属性在 `attrib` 结构的 `_finddata_t` 字段中返回，并且可能具有以下值（在 IO.h 中定义）。 用户不应依赖可能为 `attrib` 字段中的唯一值的这些值。  
  
 `_A_ARCH`  
 存档。 每当通过 **BACKUP** 命令更改或清除文件时进行设置。 值：0x20。  
  
 `_A_HIDDEN`  
 隐藏文件。 使用 DIR 命令时通常不可见，除非使用 **/AH** 选项。 返回普通文件和具有此属性的文件的相关信息。 值：0x02。  
  
 `_A_NORMAL`  
 正常。 文件未设置其他属性，可不受限制地读取或写入文件。 值：0x00。  
  
 `_A_RDONLY`  
 只读。 无法打开文件进行写入且无法创建具有相同名称的文件。 值：0x01。  
  
 `_A_SUBDIR`  
 子目录。 值：0x10。  
  
 `_A_SYSTEM`  
 系统文件。 使用 **DIR** 命令时通常不可见，除非使用 **/A** 或 **/A:S** 选项。 值：0x04。  
  
 `_findnext` 找到下一个名称（若有），该名称匹配对 `_findfirst` 的早期调用中指定的 `filespec` 参数。 `fileinfo` 参数应指向由之前对 `_findfirst`的调用初始化的结构。 如果找到匹配项，则如前文所述， `fileinfo` 结构内容将发生更改。 否则保持不变。 `_findclose` 关闭指定的搜索句柄并释放 `_findfirst` 和 `_findnext` 的所有关联资源。 通过 `_findfirst` 或 `_findnext` 返回的句柄必须首先传递给 `_findclose`，然后才对形成传递路径的目录执行修改操作（例如删除）。  
  
 你可以嵌套 `_find` 函数。 例如，如果对 `_findfirst` 或 `_findnext` 的调用找到作为子目录的文件，则可以使用对 `_findfirst` 或 `_findnext`的另一个调用开始新的搜索。  
  
 `_wfindfirst` 和 `_wfindnext` 是 `_findfirst` 和 `_findnext` 的宽字符版本。 宽字符版本的结构参数具有在 IO.h 和 Wchar.h 中定义的 `_wfinddata_t` 数据类型。 该数据类型的字段与 `_finddata_t` 数据类型中的相同，除非在 `_wfinddata_t` 中，名称字段属于 `wchar_t` 类型，而不属于 `char`类型。 除此之外， `_wfindfirst` 和 `_wfindnext` 的行为与 `_findfirst` 和 `_findnext`完全相同。  
  
 `_findfirst` 和 `_findnext` 使用 64 位时间类型。 如果你必须使用旧的 32 位时间类型，则可以定义 `_USE_32BIT_TIME_T`。 名称中具有 `32` 后缀的这些函数的版本使用 32 位时间类型，而具有 `64` 后缀的那些版本使用 64 位时间类型。  
  
 除了使用并返回 64 位文件长度外，函数 `_findfirst32i64`、`_findnext32i64``_wfindfirst32i64` 和 `_wfindnext32i64` 的行为与 32 位时间类型版本的这些函数相同。 函数 `_findfirst64i32`、`_findnext64i32`、`_wfindfirst64i32` 和 `_wfindnext64i32` 使用 64 位时间类型，但使用 32 位文件长度。 这些函数使用适当 `_finddata_t` 类型变体，其中字段对于时间和文件大小具有不同的类型。  
  
 `_finddata_t` 实际上是计算结果为 `_USE_32BIT_TIME_T` 的宏（或如果定义了 `_finddata32_t`，则为 `_finddata64i32_t`）。 下表总结了 `_finddata_t`上的变体：  
  
|结构|时间类型|文件大小类型|  
|---------------|---------------|--------------------|  
|`_finddata_t`, `_wfinddata_t`|`__time64_t`|`_fsize_t`|  
|`_finddata32_t`, `_wfinddata32_t`|`__time32_t`|`_fsize_t`|  
|`__finddata64_t`, `__wfinddata64_t`|`__time64_t`|`__int64`|  
|`_finddata32i64_t`, `_wfinddata32i64_t`|`__time32_t`|`__int64`|  
|`_finddata64i32_t`, `_wfinddata64i32_t`|`__time64_t`|`_fsize_t`|  
  
 `_fsize_t` 是 `unsigned long` 的 `typedef`（32 位）。  
  
## <a name="example"></a>示例  
  
```  
// crt_find.c  
// This program uses the 32-bit _find functions to print  
// a list of all files (and their attributes) with a .C extension  
// in the current directory.  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <io.h>  
#include <time.h>  
  
int main( void )  
{  
   struct _finddata_t c_file;  
   intptr_t hFile;  
  
   // Find first .c file in current directory   
   if( (hFile = _findfirst( "*.c", &c_file )) == -1L )  
      printf( "No *.c files in current directory!\n" );  
   else  
   {  
      printf( "Listing of .c files\n\n" );  
      printf( "RDO HID SYS ARC  FILE         DATE %25c SIZE\n", ' ' );  
      printf( "--- --- --- ---  ----         ---- %25c ----\n", ' ' );  
      do {  
         char buffer[30];  
         printf( ( c_file.attrib & _A_RDONLY ) ? " Y  " : " N  " );  
         printf( ( c_file.attrib & _A_HIDDEN ) ? " Y  " : " N  " );  
         printf( ( c_file.attrib & _A_SYSTEM ) ? " Y  " : " N  " );  
         printf( ( c_file.attrib & _A_ARCH )   ? " Y  " : " N  " );  
         ctime_s( buffer, _countof(buffer), &c_file.time_write );  
         printf( " %-12s %.24s  %9ld\n",  
            c_file.name, buffer, c_file.size );  
      } while( _findnext( hFile, &c_file ) == 0 );  
      _findclose( hFile );  
   }  
}  
```  
  
```Output  
Listing of .c files  
  
RDO HID SYS ARC  FILE         DATE                           SIZE  
--- --- --- ---  ----         ----                           ----  
 N   N   N   Y   blah.c       Wed Feb 13 09:21:42 2002       1715  
 N   N   N   Y   test.c       Wed Feb 06 14:30:44 2002        312  
```  
  
## <a name="see-also"></a>另请参阅  
 [系统调用](../c-runtime-library/system-calls.md)
