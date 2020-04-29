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
ms.openlocfilehash: f18b04cadfa80d7e0be193bbd552efe8486eeeda
ms.sourcegitcommit: fcc3aeb271449f8be80348740cffef39ba543407
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2020
ms.locfileid: "82538608"
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

*.Pfile*<br/>
指向文件指针的指针，文件指针将接收指向已打开文件的指针。

*名字*<br/>
文件名。

*mode*<br/>
允许的访问类型。

## <a name="return-value"></a>返回值

如果成功，则为零；如果失败，则为错误代码。 有关这些错误代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>错误条件

|*.Pfile*|*名字*|*mode*|返回值|*.Pfile*的内容|
|-------------|----------------|------------|------------------|------------------------|
|**无效**|any|any|**EINVAL**|未更改|
|any|**无效**|any|**EINVAL**|未更改|
|any|any|**无效**|**EINVAL**|未更改|

## <a name="remarks"></a>备注

**Fopen_s**和 **_wfopen_s**打开的文件不可共享。 如果需要共享文件，请使用[_fsopen，_wfsopen](fsopen-wfsopen.md)并使用适当的共享模式常量（例如， **_SH_DENYNO**进行读/写共享。

**Fopen_s**函数打开*文件名*指定的文件。 **_wfopen_s**是**fopen_s**的宽字符版本;**_wfopen_s**的参数是宽字符字符串。 否则 **_wfopen_s**和**fopen_s**的行为相同。

**fopen_s**接受在执行时文件系统上有效的路径;只要执行代码的系统在执行时能够访问共享或映射的网络驱动器， **fopen_s**就会接受包含映射的网络驱动器的 UNC 路径和路径。 构造**fopen_s**的路径时，不要对执行环境中的驱动器、路径或网络共享的可用性进行假设。 可使用斜杠 (/) 或反斜杠 (\\) 作为路径中的目录分隔符。

这些函数验证其参数。 如果 *.pfile*、 *filename*或*mode*为空指针，则这些函数将生成无效的参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。

请始终先检查返回值，确定该函数是否成功，再对文件执行任何进一步的操作。 如果发生错误，将返回错误代码并设置全局变量**errno** 。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="unicode-support"></a>Unicode 支持

**fopen_s**支持 Unicode 文件流。 若要打开新的或现有的 Unicode 文件，请将指定所需编码的*ccs*标志传递给**fopen_s**：

**fopen_s （&fp，"newfile .txt"，"rw，ccs =**_encoding_**"）;**

允许的*编码*值为**UNICODE**、 **utf-8**和**utf-16le**。 如果没有为*编码*指定任何值， **FOPEN_S**将使用 ANSI 编码。

如果文件已存在并已打开以进行读取或追加，则字节顺序标记 (BOM)（如果文件中存在）将确定编码。 BOM 编码优先于*ccs*标志指定的编码。 仅在不存在 BOM 或文件是新文件时，才使用*ccs*编码。

> [!NOTE]
> BOM 检测仅适用于在 Unicode 模式下打开的文件;也就是说，传递*ccs*标志。

下表汇总了给定**fopen_s**的各种*ccs*标志的模式以及文件中的字节顺序标记。

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>基于 ccs 标志和 BOM 使用的编码

|ccs 标志|无 BOM（或新文件）|BOM：UTF-8|BOM：UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

在 Unicode 模式下打开用于写入的文件将自动在其中写入 BOM。

如果*mode*为 **"a，ccs =**_encoding_**"**， **fopen_s**首先尝试使用读取访问权限和写入访问权限打开文件。 如果成功，此函数将读取 BOM 以确定文件的编码；如果失败，此函数将使用文件的默认编码。 在任一情况下， **fopen_s**将使用只写访问权限重新打开文件。 （这仅适用**于模式，** 不适用于 **+**。）

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen_s**|**fopen_s**|**fopen_s**|**_wfopen_s**|

字符字符串*模式*指定为文件请求的访问类型，如下所示。

|*mode*|访问|
|-|-|
| **迅驰** | 打开以便读取。 如果文件不存在或找不到，则**fopen_s**调用失败。 |
| **水平** | 打开用于写入的空文件。 如果给定文件存在，则其内容会被销毁。 |
| **的** | 在文件末尾打开以进行写入（追加），在新数据写入到文件之前不移除文件末尾 (EOF) 标记。 创建文件（如果文件不存在）。 |
| **"r +"** | 打开以便读取和写入。 文件必须存在。 |
| **"w +"** | 打开用于读取和写入的空文件。 如果文件存在，则其内容会被销毁。 |
| **"a +"** | 打开以进行读取和追加。 追加操作包括在新数据写入文件之前移除 EOF 标记。 写入完成后，EOF 标记不会还原。 创建文件（如果文件不存在）。 |

使用 **"a"** 或 **"a +"** 访问类型打开文件时，所有写入操作都将在文件末尾进行。 可以通过使用[fseek](fseek-fseeki64.md)或[倒带](rewind.md)重定位文件指针，但在执行任何写入操作之前，将始终将其移回文件末尾，以便不会覆盖现有数据。

**"A"** 模式不会在追加到文件之前删除 EOF 标记。 追加后，MS-DOS TYPE 命令仅显示原始 EOF 标记之前的数据，不显示追加到文件的任何数据。 **"A +"** 模式将在追加到文件之前删除 EOF 标记。 在追加后，MS-DOS TYPE 命令显示文件中的所有数据。 若要追加到使用 CTRL + Z EOF 标记终止的流文件，需要使用 **"a +"** 模式。

指定 **"r +"**、 **"w +"** 或 **"a +"** 访问类型时，允许读取和写入。 （该文件被称为 "更新"。）但是，当你从读取切换到写入时，输入操作必须遇到 EOF 标记。 如果没有 EOF，必须使用对文件定位函数的干预调用。 文件定位函数包括**fsetpos**、 [fseek](fseek-fseeki64.md)和[倒带](rewind.md)。 当从写入切换到读取时，必须使用对**fflush**或文件定位函数的干预调用。

除了以上值之外，还可以在*模式*中包含以下字符以指定换行符的转换模式：

|*模式*修饰符|转换模式|
|-|-|
| **关心** | 在文本（转换）模式下打开。 |
| **b** | 在二进制（未转换）模式下打开;将禁止涉及回车符和换行符的翻译。 |

在文本（已转换）模式下，CTRL + Z 将在输入时解释为文件尾字符。 在使用 **"a +"** 打开以进行读取/写入的文件中， **fopen_s**检查文件末尾的 CTRL + Z 并将其删除（如果可能）。 这是因为，使用[fseek](fseek-fseeki64.md)和**FTELL**在以 CTRL + Z 结尾的文件中移动时，可能会导致[fseek](fseek-fseeki64.md)在文件结尾附近出现错误的行为。

此外，在文本模式中，回车换行符组合在输入时转换为单行馈送，换行符转换为输出时的回车符。 当 Unicode 流 I/O 函数在文本模式（默认设置）下运行时，源或目标流将假定为一系列多字节字符。 因此，Unicode 流输入函数将多字节字符转换为宽字符（就像调用 mbtowc**** 函数一样）。 出于同一原因，Unicode 流输出函数将宽字符转换为多字节字符（就像调用 wctomb**** 函数一样）。

如果在*mode*中未给出**t**或**b** ，则默认转换模式由全局变量[_fmode](../../c-runtime-library/fmode.md)定义。 如果**t**或**b**作为参数的前缀，则函数将失败并返回**NULL**。

有关在 Unicode 和多字节流 I/O 中使用文本和二进制模式的详细信息，请参阅[文本和二进制模式文件 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和[文本和二进制模式下的 Unicode 流 I/O](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)。

|*模式*修饰符|行为|
|-|-|
| **ansi-c** | 启用关联*文件名*的提交标志，以便在调用**fflush**或 **_flushall**时，将文件缓冲区的内容直接写入磁盘。 |
| **n** | 将关联的*文件名*的提交标志重置为 "无提交"。 这是默认设置。 如果将程序显式链接到 COMMODE.OBJ，它还将重写全局提交标志。 除非将程序显式链接到 COMMODE.OBJ，否则全局提交标志默认为“no-commit”（请参阅 [Link Options](../../c-runtime-library/link-options.md)）。 |
| **北** | 指定文件不由子进程继承。 |
| **S** | 指定缓存针对（但不限于）从磁盘的顺序访问进行优化。 |
| **R** | 指定缓存针对（但不限于）从磁盘的随机访问进行优化。 |
| **T** | 将文件指定为临时。 如果可能，它不会刷新到磁盘。 |
| **D** | 将文件指定为临时。 最后一个文件指针关闭时，它将被删除。 |
| **ccs =**_编码_ | 指定要使用的编码字符集（ **utf-8**、 **utf-16le**或**UNICODE**中的一个）。 如果需要 ANSI 编码，请不要指定此字符集。 |

**Fopen_s**和[_fdopen](fdopen-wfdopen.md)中使用的*模式*字符串的有效字符与[_open](open-wopen.md)和[_sopen](sopen-wsopen.md)中使用的*oflag*参数对应，如下所示。

|*模式*字符串中的字符|_Open/_sopen 的等效*oflag*值|
|-------------------------------|----------------------------------------------------|
|**的**|**_O_WRONLY** &#124; **_O_APPEND** （通常 **_O_WRONLY** &#124; **_O_CREAT** &#124; **_O_APPEND）**|
|**a +**|**_O_RDWR** &#124; **_O_APPEND** （通常 **_O_RDWR** &#124; **_O_APPEND** &#124; **_O_CREAT）**|
|**r**|**_O_RDONLY**|
|**r +**|**_O_RDWR**|
|**w**|**_O_WRONLY** （通常 **_O_WRONLY** &#124; **_O_CREAT** &#124; **_O_TRUNC**）|
|**w +**|**_O_RDWR** （通常 **_O_RDWR** &#124; **_O_CREAT** &#124; **_O_TRUNC**）|
|**b**|**_O_BINARY**|
|**关心**|**_O_TEXT**|
|**ansi-c**|无|
|**n**|无|
|**S**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**D**|**_O_TEMPORARY**|
|**ccs = UNICODE**|**_O_WTEXT**|
|**ccs = UTF-8**|**_O_UTF8**|
|**ccs = UTF-16LE**|**_O_UTF16**|

如果你使用的是**rb**模式，则无需移植代码，并希望读取大量文件和/或不关心网络性能，还可以选择内存映射的 Win32 文件。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fopen_s**|\<stdio.h>|
|**_wfopen_s**|\<stdio.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

" **C**"、" **n**" 和 " **t** *" 模式*选项是 Microsoft **fopen_s**和[_fdopen](fdopen-wfdopen.md)的扩展，不应在需要 ANSI 可移植性时使用。

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

## <a name="see-also"></a>请参阅

[流 i/o](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_fdopen，_wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen、_wfreopen](freopen-wfreopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
