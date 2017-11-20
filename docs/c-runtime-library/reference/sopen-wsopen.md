---
title: "_sopen、_wsopen | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _sopen
- _wsopen
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wsopen
- wsopen
- _sopen
- _tsopen
dev_langs: C++
helpviewer_keywords:
- sopen function
- sharing files
- opening files, for sharing
- _sopen function
- wsopen function
- files [C++], opening
- files [C++], sharing
- _wsopen function
ms.assetid: a9d4cccf-06e9-414d-96fa-453fca88cc1f
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2a28e6a05676b7340c4dfbf3e963e6046c7beafa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="sopen-wsopen"></a>_sopen、_wsopen
打开文件以供共享。 提供这些函数的更多安全版本；请参阅 [_sopen_s、_wsopen_s](../../c-runtime-library/reference/sopen-s-wsopen-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
int _sopen(  
   const char *filename,  
   int oflag,  
   int shflag [,  
   int pmode ]   
);  
int _wsopen(  
   const wchar_t *filename,  
   int oflag,  
   int shflag [,  
   int pmode ]   
);  
```  
  
#### <a name="parameters"></a>参数  
 `filename`  
 文件名。  
  
 `oflag`  
 允许的操作类型。  
  
 `shflag`  
 允许的共享类型。  
  
 `pmode`  
 权限设置。  
  
## <a name="return-value"></a>返回值  
 其中每个函数都将为打开的文件返回文件描述符。  
  
 如果 `filename` 或 `oflag` 是 `NULL` 指针，或者如果 `oflag` 或 `shflag` 不在有效值范围内，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回 -1 并将 `errno` 设置为以下值之一。  
  
 `EACCES`  
 给定路径是目录，或者文件是只读的，但是已尝试打开以供写入操作。  
  
 `EEXIST`  
 已指定 `_O_CREAT` 和 `_O_EXCL` 标志，但 `filename` 已经存在。  
  
 `EINVAL`  
 无效的 `oflag` 或 `shflag` 参数。  
  
 `EMFILE`  
 没有更多可用的文件描述符。  
  
 `ENOENT`  
 未找到文件或路径。  
  
 有关这些代码及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 `_sopen` 函数将打开由 `filename` 指定的文件并使该文件做好共享的读写准备，如 `oflag` 和 `shflag` 所定义。 `_wsopen` 是 `_sopen` 的宽字符版本；`filename` 的 `_wsopen` 参数是宽字符字符串。 除此以外，`_wsopen` 和 `_sopen` 的行为完全相同。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tsopen`|`_sopen`|`_sopen`|`_wsopen`|  
  
 整数表达式 `oflag` 是通过合并在 \<fcntl.h> 中定义的以下一个或多个清单常量而形成的。 当两个或多个常量构成 `oflag` 参数时，这些常量将与按位 OR 运算符合并 ( `|` )。  
  
 `_O_APPEND`  
 在执行每个写入操作之前，将文件指针重新定位到文件末尾。  
  
 `_O_BINARY`  
 在二进制（未转换）模式下打开文件。 （有关二进制模式的说明，请参阅 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)。）  
  
 `_O_CREAT`  
 创建文件并打开它以供写入。 如果由 `filename` 指定的文件存在，则不会产生任何影响。 指定 `pmode` 时，需要使用 `_O_CREAT` 参数。  
  
 `_O_CREAT | _O_SHORT_LIVED`  
 创建一个文件作为临时文件，如果可能，请不要将它刷新到磁盘中。 指定 `pmode` 时，需要使用 `_O_CREAT` 参数。  
  
 `_O_CREAT | _O_TEMPORARY`  
 创建一个文件作为临时文件；在关闭最后一个文件描述符时，删除该文件。 指定 `pmode` 时，需要使用 `_O_CREAT` 参数。  
  
 `_O_CREAT | _O_EXCL`  
 如果由 `filename` 指定的文件存在，则返回一个错误值。 仅在与 `_O_CREAT` 一起使用时应用。  
  
 `_O_NOINHERIT`  
 阻止创建共享文件描述符。  
  
 `_O_RANDOM`  
 从磁盘中指定主要随机访问。  
  
 `_O_RDONLY`  
 打开文件以供只读。 无法使用 `_O_RDWR` 或 `_O_WRONLY` 进行指定。  
  
 `_O_RDWR`  
 打开文件以供读取和写入。 无法使用 `_O_RDONLY` 或 `_O_WRONLY` 进行指定。  
  
 `_O_SEQUENTIAL`  
 从磁盘中指定主要顺序访问。  
  
 `_O_TEXT`  
 在文本（转换）模式下打开文件。 （有关详细信息，请参阅[文本和二进制模式文件 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)。）  
  
 `_O_TRUNC`  
 打开文件并将其长度截断为零；该文件必须具有写入权限。 无法使用 `_O_RDONLY` 进行指定。 结合使用 `_O_TRUNC` 和 `_O_CREAT` 来打开现有文件或创建文件。  
  
> [!NOTE]
>  
          `_O_TRUNC` 标志会损坏指定文件的内容。  
  
 `_O_WRONLY`  
 打开文件以供只写。 无法使用 `_O_RDONLY` 或 `_O_RDWR` 进行指定。  
  
 `_O_U16TEXT`  
 在 Unicode UTF-16 模式下打开文件。  
  
 `_O_U8TEXT`  
 在 Unicode UTF-8 模式下打开文件。  
  
 `_O_WTEXT`  
 在 Unicode 模式下打开文件。  
  
 若要指定文件访问模式，你必须指定 `_O_RDONLY`、`_O_RDWR` 或 `_O_WRONLY`。 对于访问模式，不存在默认值。  
  
 使用 `_O_WTEXT`、`_O_U8TEXT` 或 `_O_U16TEXT` 在 Unicode 模式下打开文件时，输入函数会将从该文件中读取的数据转换为存储为 `wchar_t` 类型的 UTF-16 数据。 写入到在 Unicode 模式下打开的文件的函数需要包含存储为 `wchar_t` 类型的 UTF-16 数据的缓冲区。 如果将文件编码为 UTF-8，则在写入它时，UTF-16 数据会转换为 UTF-8；在读取它时，该文件的 UTF-8 编码的内容会转换为 UTF-16。 尝试在 Unicode 模式下读取或写入奇数个字节会导致参数验证错误。 若要读取或写入在你的程序中存储为 UTF-8 的数据，请使用文本或二进制文件模式，而不是 Unicode 模式。 你应负责所有必需的编码转换。  
  
 如果使用 `_sopen`（追加模式）和 `_O_WRONLY | _O_APPEND`、`_O_WTEXT` 或 `_O_U16TEXT` 调用 `_O_U8TEXT`，则它首先会尝试打开该文件以供读取和写入、读取 BOM，然后重新打开它以供只写。 如果无法打开该文件以供读取和写入，则它将打开该文件以供只写，并使用 Unicode 模式设置的默认值。  
  
 `shflag` 参数是常量表达式，它包含在 \<share.h> 中定义的以下清单常量之一。  
  
 `_SH_DENYRW`  
 拒绝对文件的读取和写入访问。  
  
 `_SH_DENYWR`  
 拒绝对文件的写入访问。  
  
 `_SH_DENYRD`  
 拒绝对文件的读取访问。  
  
 `_SH_DENYNO`  
 允许读取和写入访问。  
  
 仅在指定 `pmode` 时，需要使用 `_O_CREAT` 参数。 如果该文件不存在，则 `pmode` 将指定在首次关闭新文件时设置的该文件的权限设置。 否则，将忽略 `pmode`。 `pmode` 是一个整数表达式，它包含在 \<sys\stat.h> 中定义的清单常量 `_S_IWRITE` 和 `_S_IREAD` 中的一个或两个。 当给定这两个常量时，将使用按位“或”运算符合并它们。 
          `pmode` 的含义如下。  
  
 `_S_IWRITE`  
 允许写入。  
  
 `_S_IREAD`  
 允许读取。  
  
 `_S_IREAD | _S_IWRITE`  
 允许读取和写入。  
  
 如果未授予写入权限，则该文件为只读。 在 Windows 操作系统中，所有文件均可读；不可能提供只写权限。 因此，模式 `_S_IWRITE` 和 `_S_IREAD | _S_IWRITE` 是等效的。  
  
 在设置这些权限之前，`_sopen` 会将当前文件权限掩码应用到 `pmode`。 （请参阅 [_umask](../../c-runtime-library/reference/umask.md)。）  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|可选标头|  
|-------------|---------------------|---------------------|  
|`_sopen`|\<io.h>|\<fcntl.h>、\<sys\types.h>、\<sys\stat.h>、\<share.h>|  
|`_wsopen`|\<io.h> 或 \<wchar.h>|\<fcntl.h>、\<sys\types.h>、\<sys\stat.h>、\<share.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 请参阅 [_locking](../../c-runtime-library/reference/locking.md) 的示例。  
  
## <a name="see-also"></a>另请参阅  
 [低级别 I/O](../../c-runtime-library/low-level-i-o.md)   
 [_close](../../c-runtime-library/reference/close.md)   
 [_creat、_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [fopen、_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_fsopen、_wfsopen](../../c-runtime-library/reference/fsopen-wfsopen.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)