---
title: "_open、_wopen | Microsoft Docs"
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
  - "_open"
  - "_wopen"
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
  - "_wopen"
  - "_topen"
  - "_open"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_open 函数"
  - "_topen 函数"
  - "_wopen 函数"
  - "文件 [C++], 打开"
  - "open 函数"
  - "打开文件, 用于文件 I/O"
  - "topen 函数"
  - "wopen 函数"
ms.assetid: 13f6a0c3-d1aa-450d-a7aa-74abc91b163e
caps.latest.revision: 31
caps.handback.revision: 31
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _open、_wopen
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

打开文件。  已弃用这些函数，因为提供了更安全的版本；请参阅 [\_sopen\_s、\_wsopen\_s](../../c-runtime-library/reference/sopen-s-wsopen-s.md)。  
  
## 语法  
  
```  
int _open(  
   const char *filename,  
   int oflag [,  
   int pmode]   
);  
int _wopen(  
   const wchar_t *filename,  
   int oflag [,  
   int pmode]   
);  
```  
  
#### 参数  
 `filename`  
 文件名。  
  
 `oflag`  
 允许的操作类型。  
  
 `pmode`  
 权限模式。  
  
## 返回值  
 其中每个函数都将为打开的文件返回文件描述符。  返回值 \-1 指示错误；在这种情况下，请将 `errno` 设置为以下值之一。  
  
 `EACCES`  
 尝试打开只读文件进行写入，文件的共享模式不允许指定的操作，或给定路径是目录。  
  
 `EEXIST`  
 已指定 `_O_CREAT` 和 `_O_EXCL` 标志，但 `filename` 已经存在。  
  
 `EINVAL`  
 无效的 `oflag` 或 `pmode` 参数。  
  
 `EMFILE`  
 无法使用更多的文件描述符（打开的文件太多）。  
  
 `ENOENT`  
 未找到文件或路径。  
  
 有关这些属性和其他的更多信息返回代码示例，请参见 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `_open` 函数将打开由 `filename` 指定的文件并使其做好读写准备，如 `oflag` 所指定。  `_wopen` 是 `_open` 的宽字符版本；`filename` 的 `_wopen` 参数是宽字符字符串。  除此以外，`_wopen` 和 `_open` 的行为完全相同。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_topen`|`_open`|`_open`|`_wopen`|  
  
 `oflag` 是一个整数表达式，是由在 \<fcntl.h\> 中定义的以下一个或多个清单常量或常量组合构成的。  
  
 `_O_APPEND`  
 在执行每个写入操作之前，将文件指针移动到文件末尾。  
  
 `_O_BINARY`  
 在二进制（未转换）模式下打开该文件。  （有关二进制模式说明，请参阅 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)。）  
  
 `_O_CREAT`  
 创建文件并打开它以供写入。  如果由 `filename` 指定的文件存在，则不会产生任何影响。  指定 `pmode` 时，需要使用 `_O_CREAT` 参数。  
  
 `_O_CREAT` &#124; `_O_SHORT_LIVED`  
 创建一个文件作为临时文件，如果可能，请不要将它刷新到磁盘中。  指定 `pmode` 时，需要使用 `_O_CREAT` 参数。  
  
 `_O_CREAT` &#124; `_O_TEMPORARY`  
 创建一个文件作为临时文件；在关闭最后一个文件描述符时，删除该文件。  指定 `pmode` 时，需要使用 `_O_CREAT` 参数。  
  
 `_O_CREAT` &#124; `_O_EXCL`  
 如果由 `filename` 指定的文件存在，则返回一个错误值。  仅在与 `_O_CREAT` 一起使用时应用。  
  
 `_O_NOINHERIT`  
 阻止创建共享文件描述符。  
  
 `_O_RANDOM`  
 指定缓存针对（但不限于）从磁盘的随机访问进行优化。  
  
 `_O_RDONLY`  
 打开文件以供只读。  无法使用 `_O_RDWR` 或 `_O_WRONLY` 进行指定。  
  
 `_O_RDWR`  
 打开文件以供读取和写入。  无法使用 `_O_RDONLY` 或 `_O_WRONLY` 进行指定。  
  
 `_O_SEQUENTIAL`  
 指定缓存针对（但不限于）从磁盘的顺序访问进行优化。  
  
 `_O_TEXT`  
 在文本（转换）模式下打开文件。  （有关详细信息，请参阅[文本和二进制模式文件 I\/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)。）  
  
 `_O_TRUNC`  
 打开文件并将其长度截断为零；该文件必须具有写入权限。  无法使用 `_O_RDONLY` 进行指定。  结合使用 `_O_TRUNC` 和 `_O_CREAT` 来打开现有文件或创建文件。  
  
> [!NOTE]
>  `_O_TRUNC` 标志会损坏指定文件的内容。  
  
 `_O_WRONLY`  
 打开文件以仅只写。  无法使用 `_O_RDONLY` 或 `_O_RDWR` 进行指定。  
  
 `_O_U16TEXT`  
 在 Unicode UTF\-16 模式下打开该文件。  
  
 `_O_U8TEXT`  
 在 Unicode UTF\-8 模式下打开该文件。  
  
 `_O_WTEXT`  
 在 Unicode 模式下打开该文件。  
  
 若要指定文件访问模式，你必须指定 `_O_RDONLY`、`_O_RDWR` 或 `_O_WRONLY`。  对于访问模式，不存在默认值。  
  
 如果使用 `_O_WTEXT` 打开文件以供读取，则 `_open` 将读取文件开头并检查字节顺序标记 \(BOM\)。  如果存在 BOM，则将该文件视为 UTF\-8 或 UTF\-16LE，具体取决于该 BOM。  如果不存在 BOM，则将该文件视为 ANSI。  通过使用 `_O_WTEXT` 打开文件以供写入时，将使用 UTF\-16。  如果使用 `_O_U8TEXT`，则文件将始终作为 UTF\-8 打开；如果使用 `_O_U16TEXT`，则文件将始终作为 UTF\-16 打开，无需考虑任何之前的设置或字节顺序标记。  
  
 使用 `_O_WTEXT`、`_O_U8TEXT` 或 `_O_U16TEXT` 在 Unicode 模式下打开文件时，输入函数会将从该文件中读取的数据转换为存储为 `wchar_t` 类型的 UTF\-16 数据。  写入到在 Unicode 模式下打开的文件的函数需要包含存储为 `wchar_t` 类型的 UTF\-16 数据的缓冲区。  如果将文件编码为 UTF\-8，则在写入它时，UTF\-16 数据会转换为 UTF\-8；在读取它时，该文件的 UTF\-8 编码的内容会转换为 UTF\-16。  尝试在 Unicode 模式下读取或写入奇数个字节会导致参数验证错误。  若要读取或写入在你的程序中存储为 UTF\-8 的数据，请使用文本或二进制文件模式，而不是 Unicode 模式。  你应负责所有必需的编码转换。  
  
 如果使用 `_open`（追加模式）和 `_O_WRONLY|_O_APPEND`、`_O_WTEXT` 或 `_O_U16TEXT` 调用 `_O_U8TEXT`，则它首先会尝试打开该文件以供读取和写入、读取 BOM，然后重新打开它以供只写。  如果无法打开该文件以供读取和写入，则它将打开该文件以供只写，并使用 Unicode 模式设置的默认值。  
  
 当使用两个或多个清单常量来形成 `oflag` 参数时，这些常量将与按位“或”运算符合并 \(                       `|` ）。  有关二进制模式和文本模式的讨论，请参阅[文本和二进制模式文件 I\/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。  
  
 仅在指定 `pmode` 时，需要使用 `_O_CREAT` 参数。  如果该文件已存在，则将忽略 `pmode`。  否则，`pmode` 将指定首次关闭新文件时设置的文件权限设置。   在设置这些权限之前，`_open` 会将当前文件权限掩码应用到 `pmode`。  （有关详细信息，请参阅 [\_umask](../../c-runtime-library/reference/umask.md)。）`pmode` 是一个整数表达式，它包含在 \<sys\\stat.h\> 中定义的以下一个或两个清单常量。  
  
 `_S_IREAD`  
 只允许读取。  
  
 `_S_IWRITE`  
 允许写入。  （实际上，允许读取和写入。）  
  
 `_S_IREAD`  `|`  `_S_IWRITE`  
 允许读取和写入。  
  
 当给定这两个常量时，将使用按位“或”运算符连接它们 \(                       `|` ）。  在 Windows 中，所有文件均可读；不会提供只写权限。  因此，模式 `_S_IWRITE` 和 `_S_IREAD` `|` `_S_IWRITE` 是等效的。  
  
 如果为 `pmode` 指定一个值，而非 `_S_IREAD` 和 `_S_IWRITE` 的某种组合（即使它会在另一个操作系统中指定有效的 `pmode`），或指定除了允许的 `oflag` 值以外的任一值，则该函数将在调试模式下生成断言并调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许执行继续，则该函数将返回 \-1 并将 `errno` 设置为 `EINVAL`。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_open`|\<io.h\>|\<fcntl.h\>、\<sys\\types.h\>、\<sys\\stat.h\>|  
|`_wopen`|\<io.h\> 或 \<wchar.h\>|\<fcntl.h\>、\<sys\\types.h\>、\<sys\\stat.h\>|  
  
 `_open` 和 `_wopen` 是 Microsoft 扩展。  有关更多兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_open.c  
// compile with: /W3  
/* This program uses _open to open a file  
 * named CRT_OPEN.C for input and a file named CRT_OPEN.OUT  
 * for output. The files are then closed.  
 */  
#include <fcntl.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <io.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int fh1, fh2;  
  
   fh1 = _open( "CRT_OPEN.C", _O_RDONLY ); // C4996  
   // Note: _open is deprecated; consider using _sopen_s instead  
   if( fh1 == -1 )  
      perror( "Open failed on input file" );  
   else  
   {  
      printf( "Open succeeded on input file\n" );  
      _close( fh1 );  
   }  
  
   fh2 = _open( "CRT_OPEN.OUT", _O_WRONLY | _O_CREAT, _S_IREAD |   
                            _S_IWRITE ); // C4996  
   if( fh2 == -1 )  
      perror( "Open failed on output file" );  
   else  
   {  
      printf( "Open succeeded on output file\n" );  
      _close( fh2 );  
   }  
}  
```  
  
## 输出  
  
```  
Open succeeded on input file  
Open succeeded on output file  
```  
  
## .NET Framework 等效项  
  
-   [System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.file.open.aspx)  
  
-   <xref:System.IO.FileStream.%23ctor%2A>  
  
## 请参阅  
 [低级别 I\/O](../../c-runtime-library/low-level-i-o.md)   
 [\_chmod、\_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_dup、\_dup2](../../c-runtime-library/reference/dup-dup2.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [\_sopen、\_wsopen](../../c-runtime-library/reference/sopen-wsopen.md)