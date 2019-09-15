---
title: _open、_wopen
ms.date: 11/04/2016
api_name:
- _open
- _wopen
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
- _wopen
- _topen
- _open
helpviewer_keywords:
- opening files, for file I/O
- topen function
- _open function
- _topen function
- _wopen function
- files [C++], opening
- wopen function
- open function
ms.assetid: 13f6a0c3-d1aa-450d-a7aa-74abc91b163e
ms.openlocfilehash: aad98844f4d9faf57c7bc5051eebabad09b860a4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951176"
---
# <a name="_open-_wopen"></a>_open、_wopen

打开文件。 已弃用这些函数，因为提供了更安全的版本；请参阅 [_sopen_s、_wsopen_s](sopen-s-wsopen-s.md)。

## <a name="syntax"></a>语法

```C
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

### <a name="parameters"></a>参数

*filename*<br/>
文件名。

*oflag*<br/>
允许的操作类型。

*pmode*<br/>
权限模式。

## <a name="return-value"></a>返回值

其中每个函数都将为打开的文件返回文件描述符。 返回值-1 指示错误;在这种情况下， **errno**设置为以下值之一。

|errno 值|条件|
|-|-|
| **EACCES** | 尝试打开只读文件进行写入，文件的共享模式不允许指定的操作，或给定路径是目录。 |
| **EEXIST** | 已指定 **_O_CREAT**和 **_O_EXCL**标志，但*filename*已经存在。 |
| **EINVAL** | 无效的*oflag*或*pmode*参数。 |
| **EMFILE** | 无法使用更多的文件描述符（打开的文件太多）。 |
| **ENOENT** | 未找到文件或路径。 |

有关这些代码及其他返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Open**函数打开*文件名*指定的文件，并根据*oflag*的指定使其做好读写准备。 **_wopen**是 **_open**的宽字符版本; **_wopen**的*filename*参数是宽字符字符串。 否则， **_wopen**和 **_open**的行为相同。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_topen**|**_open**|**_open**|**_wopen**|

*oflag*是一个由以下一个或多个清单常量或常量组合构成的整数表达式，在 fcntl.h> > 中\<定义。

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

如果 **_O_WTEXT**用于打开要读取的文件，则 **_open**将读取该文件的开头并检查字节顺序标记（BOM）。 如果存在 BOM，则将该文件视为 UTF-8 或 UTF-16LE，具体取决于该 BOM。 如果不存在 BOM，则将该文件视为 ANSI。 使用 **_O_WTEXT**打开文件进行写入时，将使用 utf-16。 无论前面的设置或字节顺序标记如何，如果使用 **_O_U8TEXT** ，文件始终以 utf-8 形式打开;如果使用了 **_O_U16TEXT** ，则文件始终以 utf-16 的形式打开。

使用 **_O_WTEXT**、 **_O_U8TEXT**或 **_O_U16TEXT**在 Unicode 模式下打开文件时，输入函数会将从文件读取的数据转换为存储为类型**wchar_t**的 utf-16 数据。 写入在 Unicode 模式下打开的文件的函数需要包含存储为**wchar_t**类型的 utf-16 数据的缓冲区。 如果将文件编码为 UTF-8，则在写入它时，UTF-16 数据会转换为 UTF-8；在读取它时，该文件的 UTF-8 编码的内容会转换为 UTF-16。 尝试在 Unicode 模式下读取或写入奇数个字节会导致参数验证错误。 若要读取或写入在你的程序中存储为 UTF-8 的数据，请使用文本或二进制文件模式，而不是 Unicode 模式。 你应负责所有必需的编码转换。

如果 **_open**是通过 **_O_WRONLY** |  **_O_APPEND** （追加模式）和 **_O_WTEXT**、 **_O_U16TEXT**或 **_O_U8TEXT**调用的，则它首先会尝试打开文件以进行读取和写入、读取 BOM，然后将其重新打开仅限写入。 如果无法打开该文件以供读取和写入，则它将打开该文件以供只写，并使用 Unicode 模式设置的默认值。

当使用两个或多个清单常量构成*oflag*参数时，这些常量将与按位 "或" 运算符（ **&#124;** ）组合在一起。 有关二进制模式和文本模式的讨论，请参阅[文本和二进制模式文件 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。

仅当指定 **_O_CREAT**时， *pmode*参数是必需的。 如果文件已存在，则会忽略*pmode* 。 否则， *pmode*将指定在首次关闭新文件时设置的文件权限设置。 在设置权限之前， **_open**会将当前文件权限掩码应用到*pmode* 。 （有关详细信息，请参阅[_umask](umask.md)。）*pmode*是一个整数表达式，它包含在 sys\stat.h > 中\<定义的以下一个或两个清单常量。

|*pmode*|含义|
|-|-|
| **_S_IREAD** | 只允许读取。 |
| **_S_IWRITE** | 允许写入。 （实际上，允许读取和写入。） |
| **_S_IREAD** &#124; **_S_IWRITE** | 允许读取和写入。 |

当提供两个常量时，它们将与按位 "或" 运算符 **&#124;** （）联接。 在 Windows 中，所有文件均可读；不会提供只写权限。 因此， **_S_IWRITE**和 **_S_IREAD** |  **_S_IWRITE**模式是等效的。

如果为*pmode*指定了 **_S_IREAD**和 **_S_IWRITE**的某个组合以外的值，即使它会在另一个操作系统中指定有效的*pmode* ，或除允许的*oflag*值以外的任何值也是如此。指定，函数将在调试模式下生成断言并调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将返回-1，并将**errno**设置为**EINVAL**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_open**|\<io.h>|\<fcntl.h>、\<sys\types.h>、\<sys\stat.h>|
|**_wopen**|\<io.h> 或 \<wchar.h>|\<fcntl.h>、\<sys\types.h>、\<sys\stat.h>|

**_open**和 **_wopen**是 Microsoft 扩展。 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
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

### <a name="output"></a>Output

```Output
Open succeeded on input file
Open succeeded on output file
```

## <a name="see-also"></a>请参阅

[低级别 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod、_wchmod](chmod-wchmod.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_dup、_dup2](dup-dup2.md)<br/>
[fopen、_wfopen_wfopen](fopen-wfopen.md)<br/>
[_sopen、_wsopen](sopen-wsopen.md)<br/>
