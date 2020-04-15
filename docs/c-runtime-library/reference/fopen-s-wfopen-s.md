---
title: fopen_s、_wfopen_s
ms.date: 4/2/2020
api_name:
- _wfopen_s
- fopen_s
- _o__wfopen_s
- _o_fopen_s
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fopen_s
- _tfopen_s
- _wfopen_s
helpviewer_keywords:
- _wfopen_s function
- opening files, for file I/O
- _tfopen_s function
- tfopen_s function
- wfopen_s function
- fopen_s function
- Unicode [C++], creating files
- Unicode [C++], writing files
- files [C++], opening
- Unicode [C++], files
ms.assetid: c534857e-39ee-4a3f-bd26-dfe551ac96c3
ms.openlocfilehash: 80d04e75637cfab9795bf5dfb9da9786cf4ebd71
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346491"
---
# <a name="fopen_s-_wfopen_s"></a>fopen_s、_wfopen_s

打开文件。 这些版本的 [fopen、_wfopen](fopen-wfopen.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。

## <a name="syntax"></a>语法

```C
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

### <a name="parameters"></a>参数

*pFile*<br/>
指向文件指针的指针，文件指针将接收指向已打开文件的指针。

*文件名*<br/>
文件名。

*模式*<br/>
允许的访问类型。

## <a name="return-value"></a>返回值

如果成功，则为零；如果失败，则为错误代码。 有关这些错误代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>错误条件

|*pFile*|*文件名*|*模式*|返回值|*pFile*的内容|
|-------------|----------------|------------|------------------|------------------------|
|**空**|any|any|**埃因瓦尔**|未更改|
|any|**空**|any|**埃因瓦尔**|未更改|
|any|any|**空**|**埃因瓦尔**|未更改|

## <a name="remarks"></a>备注

**由fopen_s**和 **_wfopen_s**打开的文件不可共享。 如果需要文件是可共享的，请使用[_fsopen，使用](fsopen-wfsopen.md)具有相应共享模式常量_wfsopen，例如 **，_SH_DENYNO**读取/写入共享。

**fopen_s**函数将打开由*文件名*指定的文件。 **_wfopen_s**是**fopen_s**的宽字符版本;要 **_wfopen_s**的参数是宽字符字符串。 **_wfopen_s**和**fopen_s**行为相同。

**fopen_s**接受在执行时文件系统上有效的路径;FOPEN_S接受涉及映射网络驱动器的 UNC 路径和路径 **，只要执行**代码的系统在执行时可以访问共享或映射的网络驱动器。 构造**fopen_s**路径时，不要对执行环境中的驱动器、路径或网络共享的可用性进行假设。 可使用斜杠 (/) 或反斜杠 (\\) 作为路径中的目录分隔符。

这些函数验证其参数。 如果*pFile、**文件名*或*模式*是空指针，则这些函数将生成无效的参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。

请始终先检查返回值，确定该函数是否成功，再对文件执行任何进一步的操作。 如果发生错误，将返回错误代码并设置全局变量**errno。** 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="unicode-support"></a>Unicode 支持

**fopen_s**支持 Unicode 文件流。 要打开新的或现有的 Unicode 文件，请传递一个*ccs*标志，该标志指定所需的编码**以fopen_s**：

**fopen_s（&fp，"newfile.txt"，"rw，ccs_**_编码_**"）;**

允许的*编码*值是 UNICODE、UTF-8 和**UTF-16LE**。 **UNICODE** **UTF-8** 如果没有为*编码*指定值 **，fopen_s**使用 ANSI 编码。

如果文件已存在并已打开以进行读取或追加，则字节顺序标记 (BOM)（如果文件中存在）将确定编码。 BOM 编码优先于*由 ccs*标志指定的编码。 仅当不存在 BOM 或文件是新文件时，才使用*ccs*编码。

> [!NOTE]
> 物料清单检测仅适用于在 Unicode 模式下打开的文件;也就是说，通过传递*ccs*标志。

下表总结了为**fopen_s**和文件中的字节订单标记提供的各种*ccs*标志的模式。

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>基于 ccs 标志和 BOM 使用的编码

|ccs 标志|无 BOM（或新文件）|BOM：UTF-8|BOM：UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**Unicode**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

在 Unicode 模式下打开用于写入的文件将自动在其中写入 BOM。

如果*模式*为 **"a，ccs_**_编码_**"，fopen_s**首先尝试打开具有读取访问和写入访问权限的文件。 **fopen_s** 如果成功，此函数将读取 BOM 以确定文件的编码；如果失败，此函数将使用文件的默认编码。 在这两种情况下 **，fopen_s**然后重新打开具有仅写入访问权限的文件。 （这仅适用于**模式，** 不适用于 **.）**

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen_s**|**fopen_s**|**fopen_s**|**_wfopen_s**|

字符串*模式*指定为文件请求的访问类型，如下所示。

|*模式*|访问|
|-|-|
| **"r"** | 打开以便读取。 如果文件不存在或找不到，则**fopen_s**调用失败。 |
| **"w"** | 打开用于写入的空文件。 如果给定文件存在，则其内容会被销毁。 |
| **"a"** | 在文件末尾打开以进行写入（追加），在新数据写入到文件之前不移除文件末尾 (EOF) 标记。 创建文件（如果文件不存在）。 |
| **"r+"** | 打开以便读取和写入。 文件必须存在。 |
| **"w+"** | 打开用于读取和写入的空文件。 如果文件存在，则其内容会被销毁。 |
| **"a+"** | 打开以进行读取和追加。 追加操作包括在新数据写入文件之前移除 EOF 标记。 写入完成后，EOF 标记不会还原。 创建文件（如果文件不存在）。 |

使用 **"a"** 或 **"a+"** 访问类型打开文件时，所有写入操作都发生在文件的末尾。 可以使用[fseek](fseek-fseeki64.md)或[后退](rewind.md)重新定位文件指针，但在执行任何写入操作之前，该文件指针始终移回文件末尾，以便无法覆盖现有数据。

在追加到文件之前 **，"a"** 模式不会删除 EOF 标记。 追加后，MS-DOS TYPE 命令仅显示原始 EOF 标记之前的数据，不显示追加到文件的任何数据。 **"a+"** 模式在追加到文件之前确实会删除 EOF 标记。 在追加后，MS-DOS TYPE 命令显示文件中的所有数据。 使用 CTRL_Z EOF 标记终止的流文件需要 **"a+"** 模式。

指定 **"r+"、"w+"** 或 **"w+"****"a+"** 访问类型时，允许读取和写入。 （该文件表示为"更新"打开。但是，当您从读取切换到写入时，输入操作必须遇到 EOF 标记。 如果没有 EOF，必须使用对文件定位函数的干预调用。 文件定位函数是**fsetpos、fseek**和[倒带](rewind.md)。 [fseek](fseek-fseeki64.md) 当您从写入切换到读取时，必须使用中间调用来**fflush**或文件定位函数。

除上述值外，还可以在*模式下*包含以下字符，以指定换行符的转换模式：

|*模式*修改器|翻译模式|
|-|-|
| **t** | 在文本（转换）模式下打开。 |
| **B** | 在二进制（未翻译）模式下打开;禁止使用涉及回车符和换行符的翻译。 |

在文本（翻译）模式下，CTRL_Z 被解释为输入时的文件结尾字符。 在打开用于读取/写入 **"a+"** 的文件中 **，fopen_s**检查文件末尾的 CTRL_Z，并尽可能将其删除。 这样做是因为使用[fseek](fseek-fseeki64.md)和**ftell**在以 CTRL_Z 结尾的文件内移动，可能会导致[fseek](fseek-fseeki64.md)在文件末尾附近行为不当。

此外，在文本模式下，在输入时将回料返回行馈送组合转换为单行馈送，在输出时将换行符转换为回车换行换行组合。 当 Unicode 流 I/O 函数在文本模式（默认设置）下运行时，源或目标流将假定为一系列多字节字符。 因此，Unicode 流输入函数将多字节字符转换为宽字符（就像调用 mbtowc**** 函数一样）。 出于同一原因，Unicode 流输出函数将宽字符转换为多字节字符（就像调用 wctomb**** 函数一样）。

如果在*模式下*未给出**t**或**b，** 则默认转换模式由全局变量[_fmode](../../c-runtime-library/fmode.md)定义。 如果**t**或**b**预固定到参数，则函数将失败并返回**NULL**。

有关在 Unicode 和多字节流 I/O 中使用文本和二进制模式的详细信息，请参阅[文本和二进制模式文件 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和[文本和二进制模式下的 Unicode 流 I/O](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)。

|*模式*修改器|行为|
|-|-|
| **C** | 启用关联*文件名*的提交标志，以便在调用**fflush**或 **_flushall**时，文件缓冲区的内容直接写入磁盘。 |
| **n** | 将关联*文件名*的提交标志重置为"不提交"。 这是默认值。 如果将程序显式链接到 COMMODE.OBJ，它还将重写全局提交标志。 除非将程序显式链接到 COMMODE.OBJ，否则全局提交标志默认为“no-commit”（请参阅 [Link Options](../../c-runtime-library/link-options.md)）。 |
| **N** | 指定文件不由子进程继承。 |
| **S** | 指定缓存针对（但不限于）从磁盘的顺序访问进行优化。 |
| **R** | 指定缓存针对（但不限于）从磁盘的随机访问进行优化。 |
| **T** | 将文件指定为临时。 如果可能，它不会刷新到磁盘。 |
| **D** | 将文件指定为临时。 最后一个文件指针关闭时，它将被删除。 |
| **ccs_**_编码_ | 指定要用于此文件的编码字符集 **（UTF-8、UTF-16LE**或**UNICODE**之一）。 **UTF-16LE** 如果需要 ANSI 编码，请不要指定此字符集。 |

**fopen_s**和[_fdopen](fdopen-wfdopen.md)中使用的*模式*字符串的有效字符对应于[_open](open-wopen.md)和[_sopen](sopen-wsopen.md)中使用的*滞后*参数，如下所示。

|*模式*字符串中的字符|_open/_sopen*的滞后*值等值|
|-------------------------------|----------------------------------------------------|
|**a**|**_O_WRONLY** **_O_WRONLY&#124;_O_APPEND（** 通常 **_O_WRONLY**_O_WRONLY&#124;_O_CREAT&#124;*_O_APPEND*） **_O_CREAT**|
|**a+**|**_O_RDWR** **_O_RDWR&#124;_O_APPEND（** 通常 **_O_RDWR****_O_RDWR&#124;_O_APPEND&#124;_O_CREAT）** **_O_CREAT**|
|**R**|**_O_RDONLY**|
|**r+**|**_O_RDWR**|
|**w**|**_O_WRONLY（** 通常 **_O_WRONLY****_O_WRONLY&#124;_O_CREAT&#124;*** _O_TRUNC]）|
|**w***|**_O_RDWR（** 通常 **_O_RDWR****_O_RDWR&#124;_O_CREAT&#124;_O_TRUNC）** **_O_TRUNC**|
|**B**|**_O_BINARY**|
|**t**|**_O_TEXT**|
|**C**|None|
|**n**|None|
|**S**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**D**|**_O_TEMPORARY**|
|**ccs_UNICODE**|**_O_WTEXT**|
|**ccs_UTF-8**|**_O_UTF8**|
|**ccs_UTF-16LE**|**_O_UTF16**|

如果您使用的是**rb**模式，则不需要移植代码，并且希望读取大量文件和/或不关心网络性能，则内存映射的 Win32 文件可能也是一个选项。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fopen_s**|\<stdio.h>|
|**_wfopen_s**|\<stdio.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

**c、n**和**t** *模式*选项是 Microsoft **fopen_s**和[_fdopen](fdopen-wfdopen.md)的扩展，在需要 ANSI 可移植性的情况下不应使用。 **n**

## <a name="example"></a>示例

```C
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

```Output
The file 'crt_fopen_s.c' was opened
The file 'data2' was opened
Number of files closed by _fcloseall: 1
```

## <a name="see-also"></a>另请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_fdopen，_wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen、_wfreopen](freopen-wfreopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
