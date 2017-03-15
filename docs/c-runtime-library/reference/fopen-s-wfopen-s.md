---
title: "fopen_s、_wfopen_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wfopen_s"
  - "fopen_s"
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
  - "fopen_s"
  - "_tfopen_s"
  - "_wfopen_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tfopen_s 函数"
  - "_wfopen_s 函数"
  - "文件 [C++], 打开"
  - "fopen_s 函数"
  - "打开文件, 用于文件 I/O"
  - "tfopen_s 函数"
  - "Unicode [C++], 创建文件"
  - "Unicode [C++], 文件"
  - "Unicode [C++], 写入文件"
  - "wfopen_s 函数"
ms.assetid: c534857e-39ee-4a3f-bd26-dfe551ac96c3
caps.latest.revision: 41
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 41
---
# fopen_s、_wfopen_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

打开文件。  如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述，这些版本的 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md) 具有安全增强功能。  
  
## 语法  
  
```  
errno_t fopen_s(   
   FILE** pFile,  
   const char *filename,  
   const char *mode   
);  
errno_t _wfopen_s(  
   FILE** pFile,  
   const wchar_t *filename,  
   const wchar_t *mode   
);  
```  
  
#### 参数  
 \[out\] `pFile`  
 指向文件指针的指针，文件指针将接收指向已打开文件的指针。  
  
 \[in\] `filename`  
 文件名。  
  
 \[in\] `mode`  
 允许的访问类型。  
  
## 返回值  
 如果成功，则为零；如果失败，则为错误代码。  有关这些错误代码的详细信息，请参阅 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
### 错误条件  
  
|`pFile`|`filename`|`mode`|返回值|`pFile` 的内容|  
|-------------|----------------|------------|---------|-----------------|  
|`NULL`|任何|任何|`EINVAL`|未更改|  
|任何|`NULL`|任何|`EINVAL`|未更改|  
|any|any|NULL|`EINVAL`|未更改|  
  
## 备注  
 通过 `fopen_s` 和 `_wfopen_s` 打开的文件不可共享。  如果要求可共享文件，请将 [\_fsopen、\_wfsopen](../../c-runtime-library/reference/fsopen-wfsopen.md) 与相应的共享模式常量（例如用于读\/写共享的`_SH_DENYNO`）一起使用。  
  
 `fopen_s` 函数将打开 `filename` 指定的文件。  `_wfopen_s` 是 `fopen_s` 的宽字符版本；`_wfopen_s` 的参数是宽字符串。  除此以外，`_wfopen_s` 和 `fopen_s` 的行为完全相同。  
  
 `fopen_s` 接受执行时文件系统上有效的路径；`fopen_s` 接受 UNC 路径以及包含所映射网络驱动器的路径，前提是执行代码的系统在执行时能够访问共享或映射的网络驱动器。  为 `fopen_s` 构造路径时，请勿做出有关驱动器、路径或执行环境中网络共享的可用性假设。  可使用斜杠 \(\/\) 或反斜杠 \(\\\) 作为路径中的目录分隔符。  
  
 这些函数验证其参数。  如果 `pFile`、`filename` 或 `mode` 为 null 指针，则这些函数将生成无效的参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  
  
 请始终先检查返回值，确定该函数是否成功，再对文件执行任何进一步的操作。  如果出现错误，则将返回错误代码并且将设置全局变量 `errno`。  有关详细信息，请参阅 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## Unicode 支持  
 `fopen_s` 支持 Unicode 文件流。  若要打开新的或现有的 Unicode 文件，请将指定所需编码的 `ccs` 标志传递到 `fopen_s`：  
  
 `fopen_s(&fp, "newfile.txt", "rw,`   `ccs=`  `encoding` `");`  
  
 允许使用的 `encoding` 值为 `UNICODE`、`UTF-8` 和 `UTF-16LE`。  如果未对 `encoding` 指定值，则 `fopen_s` 将使用 ANSI 编码。  
  
 如果文件已存在并已打开以进行读取或追加，则字节顺序标记 \(BOM\)（如果文件中存在）将确定编码。  BOM 编码优先于 `ccs` 标志指定的编码。  仅在不存在 BOM 或如果文件是新文件时，才使用 `ccs` 编码。  
  
> [!NOTE]
>  BOM 检测仅适用于在 Unicode 模式下打开的文件；即，通过传递 `ccs` 标志打开的文件。  
  
 下表汇总了提供给 `fopen_s` 的各种 `ccs` 标志的模式以及文件中字节顺序标记的模式。  
  
### 基于 ccs 标志和 BOM 使用的编码  
  
|`ccs` 标志|无 BOM（或新文件）|BOM：UTF\-8|BOM：UTF\-16|  
|--------------|-----------------|----------------|-----------------|  
|`UNICODE`|`UTF-16LE`|`UTF-8`|`UTF-16LE`|  
|`UTF-8`|`UTF-8`|`UTF-8`|`UTF-16LE`|  
|`UTF-16LE`|`UTF-16LE`|`UTF-8`|`UTF-16LE`|  
  
 在 Unicode 模式下打开用于写入的文件将自动在其中写入 BOM。  
  
 如果 `mode` 为“`a, ccs=<encoding>`”，`fopen_s` 将先尝试使用读取和写入访问权限打开文件。  如果成功，此函数将读取 BOM 以确定文件的编码；如果失败，此函数将使用文件的默认编码。  在任一情况下，`fopen_s` 随后均将使用只写访问权限打开文件。  （这仅适用于`a` 模式，不适用于 `a+`。）  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tfopen_s`|`fopen_s`|`fopen_s`|`_wfopen_s`|  
  
 字符串 `mode` 指定对文件请求的访问类型，如下所示。  
  
 `"r"`  
 打开以便读取。  如果文件不存在或找不到，`fopen_s` 调用将失败。  
  
 `"w"`  
 打开用于写入的空文件。  如果文件存在，则其内容会被销毁。  
  
 `"a"`  
 在文件末尾打开以进行写入（追加），在将新数据写入到文件之前请勿删除 EOF 标记。  如果文件不存在，则创建文件。  
  
 `"r+"`  
 打开以便读取和写入。  （该文件必须存在。）  
  
 `"w+"`  
 打开用于读取和写入的空文件。  如果文件存在，则其内容会被销毁。  
  
 `"a+"`  
 打开以进行读取和追加。  追加操作包括在将新数据写入文件之前删除 EOF 标记并在写入完成后还原 EOF 标记。  如果文件不存在，则创建文件。  
  
 通过使用 `"a"` 或 `"a+"` 访问类型打开文件时，所有写入操作均将在文件末尾进行。  使用 `fseek` 或 `rewind` 可重新定位文件指针，但在执行任何写入操作前，文件指针将始终被移回文件末尾，以确保不会覆盖现有数据。  
  
 在 EOF 标记追加到文件之前，`"a"` 模式不会将其删除。  追加后，MS\-DOS TYPE 命令仅显示原始 EOF 标记之前的数据，不显示追加到文件的任何数据。  在 EOF 标记追加到文件之前，`"a+"` 模式会将其删除。  在追加后，MS\-DOS TYPE 命令显示文件中的所有数据。  需使用 `"a+"` 模式才能追加到使用 CTRL\+Z EOF 标记终止的流文件。  
  
 当指定 `"r+",` `"w+",` 或 `"a+"` 访问类型时，允许读取和写入。  （文件将处于打开状态以进行“更新”。） 但是，当你从读取切换到写入时，输入操作必须遇到 EOF 标记。  如果没有 EOF，必须使用对文件定位函数的干预调用。  文件定位函数是 `fsetpos`、`fseek` 和 `rewind`。  从写入切换到读取时，必须使用对 `fflush` 或文件定位函数的干预调用。  
  
 除了以上值之外，可以在 `mode` 中包含以下字符以指定换行符的转换模式：  
  
 `t`  
 在文本（转换）模式下打开。  在此模式中，CTRL\+Z 将在输入时解释为文件尾字符。  在打开使用 `"a+"` 进行读取\/写入的文件中，`fopen_s` 将检查文件末尾的 Ctrl\+Z 并在可能的情况下将其删除。  这是因为使用 `fseek` 和 `ftell` 在以 CTRL\+Z 结尾的文件中移动时，可能会导致 `fseek` 在文件末尾附近运行不当。  
  
 此外，在文本模式下，输入时，回车\-换行组合将转换为单一的换行，输出时，换行字符将转换为回车\-换行组合。  当 Unicode 流 I\/O 函数在文本模式（默认设置）下运行时，源或目标流将假定为一系列多字节字符。  因此，Unicode 流输入函数将多字节字符转换为宽字符（就像调用 `mbtowc` 函数一样）。  出于同一原因，Unicode 流输出函数将宽字符转换为多字节字符（就像调用 `wctomb` 函数一样）。  
  
 `b`  
 在二进制（未转换）模式下打开；不进行涉及回车和换行字符的转换。  
  
 如果 `t` 或 `b` 在 `mode` 中未给出，则默认转换模式由全局变量 [\_fmode](../../c-runtime-library/fmode.md) 定义。  如果 `t` 或 `b` 是该参数的前缀，则函数将失败并返回 `NULL`。  
  
 有关在 Unicode 和多字节流 I\/O 中使用文本和二进制模式的详细信息，请参阅[文本和二进制模式文件 I\/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和[文本和二进制模式下的 Unicode 流 I\/O](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)。  
  
 `c`  
 启用关联 `filename` 的提交标志，以便在调用 `fflush` 或 `_flushall` 时将文件缓冲区的内容直接写入磁盘。  
  
 `n`  
 将关联 `filename` 的提交标志重置为“no\-commit”。 这是默认设置。  如果将程序显式链接到 COMMODE.OBJ，它还将重写全局提交标志。  除非将程序显式链接到 COMMODE.OBJ，否则全局提交标志默认为“no\-commit”（请参阅[链接选项](../../c-runtime-library/link-options.md)）。  
  
 `N`  
 指定文件不由子进程继承。  
  
 `S`  
 指定缓存针对（但不限于）从磁盘的顺序访问进行优化。  
  
 `R`  
 指定缓存针对（但不限于）从磁盘的随机访问进行优化。  
  
 `T`  
 将文件指定为临时。  如果可能，它不会刷新到磁盘。  
  
 `D`  
 将文件指定为临时。  最后一个文件指针关闭时，它将被删除。  
  
 `ccs=ENCODING`  
 指定此文件使用的编码字符集 （UTF\-8、UTF\-16LE 和 UNICODE）。  如果需要 ANSI 编码，请保留此选项不指定。  
  
 `fopen_s` 和 `_fdopen` 中所使用 `mode` 字符串的有效字符对应于 [\_open](../../c-runtime-library/reference/open-wopen.md) 和 [\_sopen](../../c-runtime-library/reference/sopen-wsopen.md) 中使用的 `oflag` 参数。  
  
|模式字符串中的字符|`oflag`\/`_open` 的等效 `_sopen` 值。|  
|---------------|--------------------------------------|  
|`a`|`_O_WRONLY &#124; _O_APPEND`（通常为 `_O_WRONLY &#124; _O_CREAT &#124;``_O_APPEND`）|  
|`a+`|`_O_RDWR &#124; _O_APPEND`（通常为 `_O_RDWR &#124; _O_APPEND &#124; _O_CREAT`）|  
|`r`|`_O_RDONLY`|  
|`r+`|`_O_RDWR`|  
|`w`|`_O_WRONLY`（通常为 `_O_WRONLY &#124;``_O_CREAT &#124; _O_TRUNC`）|  
|`w+`|`_O_RDWR`（通常为 `_O_RDWR &#124; _O_CREAT &#124; _O_TRUNC`）|  
|`b`|`_O_BINARY`|  
|`t`|`_O_TEXT`|  
|`c`|无|  
|`n`|无|  
|`S`|`_O_SEQUENTIAL`|  
|`R`|`_O_RANDOM`|  
|`T`|`_O_SHORTLIVED`|  
|`D`|`_O_TEMPORARY`|  
|`ccs=UNICODE`|`_O_WTEXT`|  
|`ccs=UTF-8`|`_O_UTF8`|  
|`ccs=UTF-16LE`|`_O_UTF16`|  
  
 如果使用 `rb` 模式，则无需移植代码，并且预计将读取大量文件以及\/或者不关心网络性能，内存映射的 Win32 文件可能也是一个选项。  
  
## 要求  
  
|函数|必需的标头|  
|--------|-----------|  
|`fopen_s`|\<stdio.h\>|  
|`_wfopen_s`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
 `c`、`n` 和 `t` `mode` 选项是 `fopen_s` 和 `_fdopen` 的 Microsoft 扩展，不应在需要 ANSI 可移植性时使用。  
  
## 示例  
  
```  
// crt_fopen_s.c  
// This program opens two files. It uses  
// fclose to close the first file and  
// _fcloseall to close all remaining files.  
  
#include <stdio.h>  
  
FILE *stream, *stream2;  
  
int main( void )  
{  
   errno_t err;  
  
   // Open for read (will fail if file "crt_fopen_s.c" does not exist)  
   err  = fopen_s( &stream, "crt_fopen_s.c", "r" );  
   if( err == 0 )  
   {  
      printf( "The file 'crt_fopen_s.c' was opened\n" );  
   }  
   else  
   {  
      printf( "The file 'crt_fopen_s.c' was not opened\n" );  
   }  
  
   // Open for write   
   err = fopen_s( &stream2, "data2", "w+" );  
   if( err == 0 )  
   {  
      printf( "The file 'data2' was opened\n" );  
   }  
   else  
   {  
      printf( "The file 'data2' was not opened\n" );  
   }  
  
   // Close stream if it is not NULL   
   if( stream )  
   {  
      err = fclose( stream );  
      if ( err == 0 )  
      {  
         printf( "The file 'crt_fopen_s.c' was closed\n" );  
      }  
      else  
      {  
         printf( "The file 'crt_fopen_s.c' was not closed\n" );  
      }  
   }  
  
   // All other files are closed:  
   int numclosed = _fcloseall( );  
   printf( "Number of files closed by _fcloseall: %u\n", numclosed );  
}  
```  
  
  **文件“crt\_fopen\_s.c”已打开**  
**文件“data2”已打开**  
**由 \_fcloseall 所关闭的文件数量为：1**   
## .NET Framework 等效项  
  
-   [System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.file.open.aspx)  
  
-   <xref:System.IO.FileStream.%23ctor%2A>  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fclose、\_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [\_fdopen、\_wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [\_fileno](../../c-runtime-library/reference/fileno.md)   
 [freopen、\_wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_setmode](../../c-runtime-library/reference/setmode.md)