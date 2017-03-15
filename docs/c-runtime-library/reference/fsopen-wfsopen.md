---
title: "_fsopen、_wfsopen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wfsopen"
  - "_fsopen"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wfsopen"
  - "fsopen"
  - "tfsopen"
  - "_tfsopen"
  - "_wfsopen"
  - "_fsopen"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fsopen 函数"
  - "_tfsopen 函数"
  - "_wfsopen 函数"
  - "文件共享 [C++]"
  - "文件 [C++], 打开"
  - "fsopen 函数"
  - "打开文件, 流"
  - "tfsopen 函数"
  - "wfsopen 函数"
ms.assetid: 5e4502ab-48a9-4bee-a263-ebac8d638dec
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# _fsopen、_wfsopen
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

打开具有文件共享的流。  
  
## 语法  
  
```  
FILE *_fsopen(   
   const char *filename,  
   const char *mode,  
   int shflag   
);  
FILE *_wfsopen(   
   const wchar_t *filename,  
   const wchar_t *mode,  
   int shflag   
);  
```  
  
#### 参数  
 `filename`  
 要打开的文件的名称。  
  
 `mode`  
 允许的访问类型。  
  
 `shflag`  
 允许的共享类型。  
  
## 返回值  
 这些函数均返回指向流的指针。  一个 null 指针值指示错误。  如果 `filename` 或 `mode` 是 `NULL` 指针或空字符串，这些函数将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许执行继续，则这些函数将返回 `NULL` 并将 `errno` 设置为 `EINVAL`。  
  
 有关这些及其他错误代码的详细信息，请参阅 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `_fsopen` 函数以流的形式打开由 `filename` 指定的文件并使该文件做好准备以进行后续的共享读写，如模式和 `shflag` 参数所定义。  `_wfsopen` 是 `_fsopen` 的宽字符版本；`_wfsopen` 的 `filename` 和 `mode` 参数是宽字符串。  除此以外，`_wfsopen` 和 `_fsopen` 的行为完全相同。  
  
 字符串 `mode` 指定为文件请求的访问类型，如下表所示。  
  
|术语|定义|  
|--------|--------|  
|`"r"`|打开以便读取。  如果文件不存在或找不到，`_fsopen` 调用将失败。|  
|`"w"`|打开用于写入的空文件。  如果给定文件存在，则其内容会被销毁。|  
|`"a"`|打开以便在文件末尾进行写入（追加）；如果文件不存在，则首先创建它。|  
|`"r+"`|打开以便读取和写入。  （该文件必须存在。）|  
|`"w+"`|打开用于读取和写入的空文件。  如果给定文件存在，则其内容会被销毁。|  
|`"a+"`|打开以便进行读取和追加；如果文件不存在，则首先创建它。|  
  
 使用 `"w"` 和 `"w+"` 类型时要小心，因为它们可能会破坏现有文件。  
  
 使用 `"a"` 或 `"a+"` 访问类型打开文件时，所有写入操作均将在文件末尾进行。  使用 `fseek` 或 `rewind` 可重新定位文件指针，但在执行任何写入操作前，文件指针将始终被移回文件末尾。  因此，无法覆盖现有数据。  指定 `"r+"`、`"w+"` 或 `"a+"` 访问类型时，允许读取和写入（文件将处于打开状态以进行更新）。  但是，在读取与写入之间切换时，必须有中间 [fsetpos](../../c-runtime-library/reference/fsetpos.md)、[fseek](../../c-runtime-library/reference/fseek-fseeki64.md) 或 [rewind](../../c-runtime-library/reference/rewind.md) 操作。  如果需要的话，可以为 `fsetpos` 或 `fseek` 操作指定当前位置。  除了以上值之外，可以在 `mode` 中包含以下字符之一以指定换行符和文件管理的转换模式。  
  
|术语|定义|  
|--------|--------|  
|`t`|在文本（转换）模式下打开文件。  在这种模式下，输入时，回车换行 \(CR\-LF\) 组合将转换为单一的换行 \(LF\)；输出时，LF 字符将转换为 CR\-LF 组合。  CTRL\+Z 也将在输入时解释为文件尾字符。  在打开以进行读取或读取\/写入的文件中，`_fsopen` 将检查文件末尾的 Ctrl\+Z 并在可能的情况下将其移除。  这是因为使用 `fseek` 和 `ftell` 在以 CTRL\+Z 结尾的文件中移动时，可能会导致 `fseek` 在文件末尾附近运行不当。|  
|`b`|在二进制（未转换）模式下打开文件；禁止上述转换。|  
|`S`|指定缓存针对（但不限于）从磁盘的顺序访问进行优化。|  
|`R`|指定缓存针对（但不限于）从磁盘的随机访问进行优化。|  
|`T`|将文件指定为临时。  如果可能，它不会刷新到磁盘。|  
|`D`|将文件指定为临时。  最后一个文件指针关闭时，它将被删除。|  
  
 如果 `t` 或 `b` 在 `mode` 中未给出，则转换模式由默认模式变量 `_fmode` 定义。  如果 `t` 或 `b` 是该参数的前缀，则函数将失败并返回 `NULL`。  有关文本和二进制模式的讨论，请参阅[文本和二进制模式文件 I\/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。  
  
 `shflag` 参数是常量表达式，它包含 Share.h 中定义的以下清单常量之一。  
  
|术语|定义|  
|--------|--------|  
|`_SH_COMPAT`|为 16 位应用程序设置兼容性模式。|  
|`_SH_DENYNO`|允许读取和写入访问。|  
|`_SH_DENYRD`|拒绝对文件的读取访问。|  
|`_SH_DENYRW`|拒绝对文件的读取和写入访问。|  
|`_SH_DENYWR`|拒绝对文件的写入访问。|  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tfsopen`|`_fsopen`|`_fsopen`|`_wfsopen`|  
  
## 要求  
  
|函数|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_fsopen`|\<stdio.h\>|\<share.h\><br /><br /> 用于 `shflag` 参数的清单常量。|  
|`_wfsopen`|\<stdio.h\> 或 \<wchar.h\>|\<share.h\><br /><br /> 用于 `shflag` 参数的清单常量。|  
  
## 示例  
  
```  
// crt_fsopen.c  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <share.h>  
  
int main( void )  
{  
   FILE *stream;  
  
   // Open output file for writing. Using _fsopen allows us to  
   // ensure that no one else writes to the file while we are  
   // writing to it.  
    //  
   if( (stream = _fsopen( "outfile", "wt", _SH_DENYWR )) != NULL )  
   {  
      fprintf( stream, "No one else in the network can write "  
                       "to this file until we are done.\n" );  
      fclose( stream );  
   }  
   // Now others can write to the file while we read it.  
   system( "type outfile" );  
}  
```  
  
  **在我们完成之前，网络中的其他任何人都无法写入此文件。**   
## .NET Framework 等效项  
  
-   [System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.file.open.aspx)  
  
-   <xref:System.IO.FileStream.%23ctor%2A>  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fclose、\_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [\_fdopen、\_wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [\_fileno](../../c-runtime-library/reference/fileno.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen、\_wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_setmode](../../c-runtime-library/reference/setmode.md)   
 [\_sopen、\_wsopen](../../c-runtime-library/reference/sopen-wsopen.md)