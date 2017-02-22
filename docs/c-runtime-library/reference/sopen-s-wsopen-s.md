---
title: "_sopen_s、_wsopen_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_sopen_s"
  - "_wsopen_s"
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
  - "_sopen_s"
  - "wsopen_s"
  - "_wsopen_s"
  - "sopen_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_sopen_s 函数"
  - "_wsopen_s 函数"
  - "文件 [C++], 打开"
  - "文件 [C++], 共享"
  - "打开文件, 用于共享"
  - "sopen_s 函数"
  - "wsopen_s 函数"
ms.assetid: 059a0084-d08c-4973-9174-55e391b72aa2
caps.latest.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 29
---
# _sopen_s、_wsopen_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

打开文件以供共享。  这些版本的 [\_sopen and \_wsopen](../../c-runtime-library/reference/sopen-wsopen.md) 提供了安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 语法  
  
```  
errno_t _sopen_s(    int* pfh,    const char *filename,    int oflag,    int shflag,    int pmode ); errno_t _wsopen_s(    int* pfh,    const wchar_t *filename,    int oflag,    int shflag,    int pmode, );  
```  
  
#### 参数  
 \[out\] `pfh`  
 文件句柄或 \-1（如果出现错误）。  
  
 \[in\] `filename`  
 文件名。  
  
 \[in\] `oflag`  
 允许的操作类型。  
  
 \[in\] `shflag`  
 允许的共享类型。  
  
 \[in\] `pmode`  
 权限设置。  
  
## 返回值  
 非零返回值指示错误；在这种情况下，请将 `errno` 设置为以下值之一。  
  
 `EACCES`  
 给定路径是目录，或者文件是只读的，但是已尝试打开以供写入操作。  
  
 `EEXIST`  
 已指定 `_O_CREAT` 和 `_O_EXCL` 标志，但 `filename` 已经存在。  
  
 `EINVAL`  
 `oflag`、`shflag` 或 `pmode` 参数无效，或者 `pfh` 或 `filename` 是空指针。  
  
 `EMFILE`  
 没有更多可用的文件描述符。  
  
 `ENOENT`  
 未找到文件或路径。  
  
 如果将无效参数传递到该函数，则调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。   如果允许执行继续，则将 `errno` 设置为 `EINVAL` 并返回 `EINVAL`。  
  
 有关这些属性和其他的更多信息返回代码示例，请参见 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 如果出现错误，则将通过 `pfh` 返回 \-1（除非 `pfh` 是空指针）。  
  
## 备注  
 `_sopen_s` 函数将打开由 `filename` 指定的文件并使该文件做好共享的读写准备，如 `oflag` 和 `shflag` 所定义。  `_wsopen_s` 是 `_sopen_s` 的宽字符版本；`_wsopen_s` 的 `filename` 参数是宽字符字符串。  除此以外，`_wsopen_s` 和 `_sopen_s` 的行为完全相同。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tsopen_s`|`_sopen_s`|`_sopen_s`|`_wsopen_s`|  
  
 整数表达式 `oflag` 是通过合并在 \<fcntl.h\> 中定义的一个或多个清单常量而形成的。  当两个或多个常量构成 `oflag` 参数时，使用按位“或”运算符合并它们：\(  `|` \).  
  
 `_O_APPEND`  
 在执行每个写入操作之前，将文件指针重新定位到文件末尾。  
  
 `_O_BINARY`  
 在二进制（未转换）模式下打开文件。  （有关二进制模式说明，请参阅 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)。）  
  
 `_O_CREAT`  
 创建文件并打开它以供写入。  如果由 `filename` 指定的文件存在，则不会产生任何影响。  
  
 `_O_CREAT | _O_SHORT_LIVED`  
 创建一个文件作为临时文件，如果可能，请不要将它刷新到磁盘中。  
  
 `_O_CREAT | _O_TEMPORARY`  
 创建一个文件作为临时文件；在关闭最后一个文件描述符时，删除该文件。  
  
 `_O_CREAT | _O_EXCL`  
 如果由 `filename` 指定的文件存在，则返回一个错误值。  仅在与 `_O_CREAT` 一起使用时应用。  
  
 `_O_NOINHERIT`  
 阻止创建共享文件描述符。  
  
 `_O_RANDOM`  
 从磁盘中指定主要随机访问。  
  
 `_O_RDONLY`  
 打开文件以供只读。  无法使用 `_O_RDWR` 或 `_O_WRONLY` 进行指定。  
  
 `_O_RDWR`  
 打开文件以供读取和写入。  无法使用 `_O_RDONLY` 或 `_O_WRONLY` 进行指定。  
  
 `_O_SEQUENTIAL`  
 从磁盘中指定主要顺序访问。  
  
 `_O_TEXT`  
 在文本（转换）模式下打开文件。  （有关详细信息，请参阅[文本和二进制模式文件 I\/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)。）  
  
 `_O_TRUNC`  
 打开文件并将其长度截断为零；该文件必须具有写入权限。  无法使用 `_O_RDONLY` 进行指定。  结合使用 `_O_TRUNC` 和 `_O_CREAT` 来打开现有文件或创建文件。  
  
> [!NOTE]
>  `_O_TRUNC` 标志会损坏指定文件的内容。  
  
 `_O_WRONLY`  
 打开文件以供只写。  无法使用 `_O_RDONLY` 或 `_O_RDWR` 进行指定。  
  
 `_O_U16TEXT`  
 在 Unicode UTF\-16 模式下打开文件。  
  
 `_O_U8TEXT`  
 在 Unicode UTF\-8 模式下打开文件。  
  
 `_O_WTEXT`  
 在 Unicode 模式下打开文件。  
  
 若要指定文件访问模式，你必须指定 `_O_RDONLY`、`_O_RDWR` 或 `_O_WRONLY`。  对于访问模式，不存在默认值。  
  
 使用 `_O_WTEXT`、`_O_U8TEXT` 或 `_O_U16TEXT` 在 Unicode 模式下打开文件时，输入函数会将从该文件中读取的数据转换为存储为 `wchar_t` 类型的 UTF\-16 数据。  写入到在 Unicode 模式下打开的文件的函数需要包含存储为 `wchar_t` 类型的 UTF\-16 数据的缓冲区。  如果将文件编码为 UTF\-8，则在写入它时，UTF\-16 数据会转换为 UTF\-8；在读取它时，该文件的 UTF\-8 编码的内容会转换为 UTF\-16。  尝试在 Unicode 模式下读取或写入奇数个字节会导致参数验证错误。  若要读取或写入在你的程序中存储为 UTF\-8 的数据，请使用文本或二进制文件模式，而不是 Unicode 模式。  你应负责所有必需的编码转换。  
  
 如果使用 `_O_WRONLY | _O_APPEND`（追加模式）和 `_O_WTEXT`、`_O_U16TEXT` 或 `_O_U8TEXT` 调用 `_sopen_s`，则它首先会尝试打开该文件以供读取和写入、读取 BOM，然后重新打开它以供只写。  如果无法打开该文件以供读取和写入，则它将打开该文件以供只写，并使用 Unicode 模式设置的默认值。  
  
 `shflag` 参数是常量表达式，它包含在 \<share.h\> 中定义的以下清单常量之一。  
  
 `_SH_DENYRW`  
 拒绝对文件的读取和写入访问。  
  
 `_SH_DENYWR`  
 拒绝对文件的写入访问。  
  
 `_SH_DENYRD`  
 拒绝对文件的读取访问。  
  
 `_SH_DENYNO`  
 允许读取和写入访问。  
  
 不同于 `_sopen`，始终需要 `pmode` 参数。  指定 `_O_CREAT` 时，如果该文件不存在，则 `pmode` 将指定在首次关闭新文件时设置的该文件的权限设置。  否则，将忽略 `pmode`。  `pmode` 是一个整数表达式，它包含在 \<sys\\stat.h\> 中定义的以下 `_S_IWRITE` 和 `_S_IREAD` 常量之一或两个。  当给定这两个常量时，将使用按位“或”运算符合并它们。  `pmode` 的含义如下。  
  
 `_S_IWRITE`  
 允许写入。  
  
 `_S_IREAD`  
 允许读取。  
  
 `_S_IREAD | _S_IWRITE`  
 允许读取和写入。  
  
 如果未授予写入权限，则该文件为只读。  在 Windows 操作系统中，所有文件均可读；不可能提供只写权限。  因此，模式 `_S_IWRITE` 和 `_S_IREAD | _S_IWRITE` 是等效的。  
  
 在设置这些权限之前，`_sopen_s` 会将当前文件权限掩码应用到 `pmode`。  （请参阅 [\_umask](../../c-runtime-library/reference/umask.md)。）  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_sopen_s`|\<io.h\>|\<fcntl.h\>、\<sys\\types.h\>、\<sys\\stat.h\>、\<share.h\>|  
|`_wsopen_s`|\<io.h\> 或 \<wchar.h\>|\<fcntl.h\>、\<sys\/types.h\>、\<sys\/stat.h\>、\<share.h\>|  
  
 `_sopen_s` 和 `_wsopen_s` 是 Microsoft 扩展。  有关更多兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参阅 [\_locking](../../c-runtime-library/reference/locking.md) 示例。  
  
## 请参阅  
 [低级别 I\/O](../../c-runtime-library/low-level-i-o.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [\_fsopen、\_wfsopen](../../c-runtime-library/reference/fsopen-wfsopen.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)