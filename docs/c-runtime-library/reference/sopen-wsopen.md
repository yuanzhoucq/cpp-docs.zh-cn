---
title: _sopen、_wsopen
ms.date: 11/04/2016
api_name:
- _sopen
- _wsopen
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wsopen
- wsopen
- _sopen
- _tsopen
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
ms.openlocfilehash: d337b2353ad15eade15235b4b5217a3b881bab1d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948049"
---
# <a name="_sopen-_wsopen"></a>_sopen、_wsopen

打开文件以供共享。 提供这些函数的更多安全版本：请参阅[_sopen_s，_wsopen_s](sopen-s-wsopen-s.md)。

## <a name="syntax"></a>语法

```C
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

### <a name="parameters"></a>参数

*filename*<br/>
文件名。

*oflag*<br/>
允许的操作类型。

*shflag*<br/>
允许的共享类型。

*pmode*<br/>
权限设置。

## <a name="return-value"></a>返回值

其中每个函数都将为打开的文件返回文件描述符。

如果*filename*或*oflag*是**NULL**指针，或*oflag*或*shflag*不在有效的值范围内，则会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回-1，并将**errno**设置为以下值之一。

|errno 值|条件|
|-|-|
| **EACCES** | 给定路径是目录，或者文件是只读的，但是已尝试打开以供写入操作。 |
| **EEXIST** | 已指定 **_O_CREAT**和 **_O_EXCL**标志，但*filename*已经存在。 |
| **EINVAL** | 无效的*oflag*或*shflag*参数。 |
| **EMFILE** | 没有更多可用的文件描述符。 |
| **ENOENT** | 未找到文件或路径。 |

有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Sopen**函数打开*文件名*指定的文件，并根据*oflag*和*shflag*的定义，准备文件以供共享读取或写入。 **_wsopen**是 **_sopen**的宽字符版本; **_wsopen**的*filename*参数是宽字符字符串。 否则， **_wsopen**和 **_sopen**的行为相同。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen**|**_sopen**|**_sopen**|**_wsopen**|

整数表达式*oflag*是通过合并在 fcntl.h> > 中\<定义的以下一个或多个清单常量而形成的。 当两个或多个常量构成参数*oflag*时，它们将与按位 "或" **&#124;** 运算符（）组合在一起。

|*oflag*常量|行为|
|-|-|
| **_O_APPEND** | 在执行每个写入操作之前，将文件指针移动到文件末尾。 |
| **_O_BINARY** | 在二进制（未转换）模式下打开该文件。 （有关二进制模式的说明，请参阅 [fopen](fopen-wfopen.md)。） |
| **_O_CREAT** | 创建文件并打开它以供写入。 如果*文件名*指定的文件存在，则不起作用。 指定 **_O_CREAT**时， *pmode*参数是必需的。 |
| **_O_CREAT** &#124; **_O_SHORT_LIVED** | 创建一个文件作为临时文件，如果可能，请不要将它刷新到磁盘中。 指定 **_O_CREAT**时， *pmode*参数是必需的。 |
| **_O_CREAT** &#124; **_O_TEMPORARY** | 创建一个文件作为临时文件；在关闭最后一个文件描述符时，删除该文件。 指定 **_O_CREAT**时， *pmode*参数是必需的。 |
| **_O_CREAT** &#124; ` _O_EXCL` | 如果*文件名*指定的文件存在，则返回一个错误值。 仅当与 **_O_CREAT**一起使用时才适用。 |
| **_O_NOINHERIT** | 阻止创建共享文件描述符。 |
| **_O_RANDOM** | 指定缓存针对（但不限于）从磁盘的随机访问进行优化。 |
| **_O_RDONLY** | 打开文件以供只读。 不能与 **_O_RDWR**或 **_O_WRONLY**一起指定。 |
| **_O_RDWR** | 打开文件以供读取和写入。 不能与 **_O_RDONLY**或 **_O_WRONLY**一起指定。 |
| **_O_SEQUENTIAL** | 指定缓存针对（但不限于）从磁盘的顺序访问进行优化。 |
| **_O_TEXT** | 在文本（转换）模式下打开文件。 （有关详细信息，请参阅[文本和二进制模式文件 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和 [fopen](fopen-wfopen.md)。） |
| **_O_TRUNC** | 打开文件并将其长度截断为零；该文件必须具有写入权限。 不能与 **_O_RDONLY**一起指定。 用于 **_O_CREAT**的 **_O_TRUNC**打开现有文件或创建文件。 **注意：** **_O_TRUNC**标志会销毁指定文件的内容。 |
| **_O_WRONLY** | 打开文件以供只写。 不能与 **_O_RDONLY**或 **_O_RDWR**一起指定。 |
| **_O_U16TEXT** | 在 Unicode UTF-16 模式下打开文件。 |
| **_O_U8TEXT** | 在 Unicode UTF-8 模式下打开文件。 |
| **_O_WTEXT** | 在 Unicode 模式下打开文件。 |

若要指定文件访问模式，必须指定 **_O_RDONLY**、 **_O_RDWR**或 **_O_WRONLY**。 对于访问模式，不存在默认值。

使用 **_O_WTEXT**、 **_O_U8TEXT**或 **_O_U16TEXT**在 Unicode 模式下打开文件时，输入函数会将从文件读取的数据转换为存储为类型**wchar_t**的 utf-16 数据。 写入在 Unicode 模式下打开的文件的函数需要包含存储为**wchar_t**类型的 utf-16 数据的缓冲区。 如果将文件编码为 UTF-8，则在写入它时，UTF-16 数据会转换为 UTF-8；在读取它时，该文件的 UTF-8 编码的内容会转换为 UTF-16。 尝试在 Unicode 模式下读取或写入奇数个字节会导致参数验证错误。 若要读取或写入在你的程序中存储为 UTF-8 的数据，请使用文本或二进制文件模式，而不是 Unicode 模式。 你应负责所有必需的编码转换。

如果 **_sopen**是通过 **_O_WRONLY** |  **_O_APPEND** （追加模式）和 **_O_WTEXT**、 **_O_U16TEXT**或 **_O_U8TEXT**调用的，则它首先会尝试打开文件以进行读取和写入、读取 BOM，然后将其重新打开仅限写入。 如果无法打开该文件以供读取和写入，则它将打开该文件以供只写，并使用 Unicode 模式设置的默认值。

自变量*shflag*是一个常量表达式，它包含在 share > 中\<定义的以下清单常量之一。

|*shflag*常量|行为|
|-|-|
| **_SH_DENYRW** | 拒绝对文件的读取和写入访问。 |
| **_SH_DENYWR** | 拒绝对文件的写入访问。 |
| **_SH_DENYRD** | 拒绝对文件的读取访问。 |
| **_SH_DENYNO** | 允许读取和写入访问。 |

仅当指定 **_O_CREAT**时， *pmode*参数是必需的。 如果文件不存在，则*pmode*指定文件的权限设置，该设置是在首次关闭新文件时设置的。 否则，将忽略*pmode* 。 *pmode*是一个整数表达式，它包含 sys\stat.h > 中\<定义的清单常量 **_S_IWRITE**和 **_S_IREAD**。 当给定这两个常量时，将使用按位“或”运算符合并它们。 *Pmode*的含义如下所示。

|*pmode*|含义|
|-|-|
| **_S_IREAD** | 只允许读取。 |
| **_S_IWRITE** | 允许写入。 （实际上，允许读取和写入。） |
| **_S_IREAD** &#124; **_S_IWRITE** | 允许读取和写入。 |

如果未授予写入权限，则该文件为只读。 在 Windows 操作系统中，所有文件均可读；不可能提供只写权限。 因此， **_S_IWRITE**和 **_S_IREAD** |  **_S_IWRITE**模式是等效的。

在设置权限之前， **_sopen**会将当前文件权限掩码应用到*pmode* 。 （请参阅 [_umask](umask.md)。）

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_sopen**|\<io.h>|\<fcntl.h>、\<sys\types.h>、\<sys\stat.h>、\<share.h>|
|**_wsopen**|\<io.h> 或 \<wchar.h>|\<fcntl.h>、\<sys\types.h>、\<sys\stat.h>、\<share.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_locking](locking.md) 的示例。

## <a name="see-also"></a>请参阅

[低级别 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[fopen、_wfopen_wfopen](fopen-wfopen.md)<br/>
[_fsopen、_wfsopen](fsopen-wfsopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
