---
title: fopen、_wfopen
ms.date: 11/04/2016
apiname:
- _wfopen
- fopen
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
- fopen
- _wfopen
- _tfopen
- corecrt_wstdio/_wfopen
- stdio/fopen
helpviewer_keywords:
- opening files, for file I/O
- wfopen function
- tfopen function
- _tfopen function
- _wfopen function
- files [C++], opening
- fopen function
ms.assetid: e868993f-738c-4920-b5e4-d8f2f41f933d
ms.openlocfilehash: 0b1dbc72124188d06da48f47e47c11ae6d06e771
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376191"
---
# <a name="fopen-wfopen"></a>fopen、_wfopen

打开文件。 这些执行附加参数验证并返回错误代码的函数有更安全的版本可用；请参阅 [fopen_s、_wfopen_s](fopen-s-wfopen-s.md)。

## <a name="syntax"></a>语法

```C
FILE *fopen(
   const char *filename,
   const char *mode
);
FILE *_wfopen(
   const wchar_t *filename,
   const wchar_t *mode
);
```

### <a name="parameters"></a>参数

*filename*<br/>
文件名。

*模式*<br/>
启用的访问类型。

## <a name="return-value"></a>返回值

这些函数均返回指向打开文件的指针。 一个 null 指针值指示错误。 如果*filename*或*mode*为**NULL**或空字符串, 这些函数将触发无效的参数处理程序, 如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续, 则这些函数将返回**NULL** , 并将**Errno**设置为**EINVAL**。

有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**Fopen**函数打开*文件名*指定的文件。 默认情况下, 使用 ANSI 代码页 (CP_ACP) 解释窄*文件名*字符串。 在 Windows 桌面应用程序中，可以通过使用 [SetFileApisToOEM](/windows/desktop/api/fileapi/nf-fileapi-setfileapistooem) 函数将此更改为 OEM 代码页 (CP_OEMCP)。 您可以使用[AreFileApisANSI](/windows/desktop/api/fileapi/nf-fileapi-arefileapisansi)函数来确定是使用 ANSI 还是系统默认的 OEM 代码页来解释*文件名*。 **_wfopen**是**fopen**的宽字符版本; **_wfopen**的参数是宽字符字符串。 否则, **_wfopen**和**fopen**的行为方式相同。 只使用 **_wfopen**不会影响在文件流中使用的编码字符集。

**fopen**接受在执行时文件系统上有效的路径;**fopen**接受 UNC 路径和包含映射的网络驱动器的路径, 前提是执行代码的系统在执行时能够访问共享或映射的驱动器。 构造**fopen**的路径时, 请确保驱动器、路径或网络共享在执行环境中可用。 可使用斜杠 (/) 或反斜杠 (\\) 作为路径中的目录分隔符。

对文件执行任何其他操作前，请始终检查返回值以确定指针是否为 NULL。 如果发生错误, 则会设置全局变量**errno** , 并可将其用于获取特定错误信息。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="unicode-support"></a>Unicode 支持

**fopen**支持 Unicode 文件流。 若要打开 Unicode 文件, 请将指定所需编码的**ccs**标志传递给**fopen**, 如下所示。

> **FILE \*fp = fopen("newfile.txt", "rt+, ccs=** _encoding_ **");**

允许的*编码*值为**UNICODE**、 **utf-8**和**utf-16le**。

在 Unicode 模式下打开文件时, 输入函数会将从文件读取的数据转换为存储为**wchar_t**类型的 utf-16 数据。 写入在 Unicode 模式下打开的文件的函数需要包含存储为**wchar_t**类型的 utf-16 数据的缓冲区。 如果将文件编码为 UTF-8，则在写入它时，UTF-16 数据会转换为 UTF-8；在读取它时，该文件的 UTF-8 编码的内容会转换为 UTF-16。 尝试在 Unicode 模式下读取或写入奇数个字节会导致 [参数验证](../../c-runtime-library/parameter-validation.md) 错误。 若要读取或写入在你的程序中存储为 UTF-8 的数据，请使用文本或二进制文件模式，而不是 Unicode 模式。 你应负责所有必需的编码转换。

如果文件已存在并已打开以进行读取或追加，字节顺序标记 (BOM)（如果文件中有）将确定编码。 BOM 编码优先于**ccs**标志指定的编码。 仅在不存在 BOM 或文件是新文件时, 才使用**ccs**编码。

> [!NOTE]
> BOM 检测仅适用于在 Unicode 模式下打开的文件 (即, 通过传递**ccs**标志)。

下表总结了在文件中提供给**fopen**和字节顺序标记的各种**ccs**标志所使用的模式。

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>基于 ccs 标志和 BOM 使用的编码

|ccs 标志|无 BOM（或新文件）|BOMUTF-8|BOMUTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

在 Unicode 模式下打开以进行写入的文件将自动写入 BOM。

如果*mode*为 **"a, ccs =** _encoding_ **"** , 则**fopen**将首先尝试使用读取和写入访问权限打开文件。 如果成功，此函数将读取 BOM 以确定文件的编码；如果失败，此函数将使用文件的默认编码。 在这两种情况下, **fopen**将使用只写访问权限重新打开文件。 (这仅适用于 **"a"** 模式, 不适用于 **"a +"** 模式。)

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen**|**fopen**|**fopen**|**_wfopen**|

字符字符串*模式*指定为文件请求的访问类型, 如下所示。

|*模式*|Access|
|-|-|
| **“r”** | 打开以便读取。 如果文件不存在或找不到, 则**fopen**调用失败。 |
| **“w”** | 打开用于写入的空文件。 如果给定文件存在，则其内容会被销毁。 |
| **“a”** | 在文件末尾打开以进行写入（追加），在新数据写入到文件之前不移除文件末尾 (EOF) 标记。 创建文件（如果文件不存在）。 |
| **“r+”** | 打开以便读取和写入。 文件必须存在。 |
| **“w+”** | 打开用于读取和写入的空文件。 如果文件存在，则其内容会被销毁。 |
| **“a+”** | 打开以进行读取和追加。 追加操作包括在新数据写入文件之前移除 EOF 标记。 写入完成后，EOF 标记不会还原。 创建文件（如果文件不存在）。 |

使用 **"a"** 访问类型或 **"a +"** 访问类型打开文件时, 所有写入操作都将在文件末尾进行。 可以通过使用[fseek](fseek-fseeki64.md)或[倒带](rewind.md)重定位文件指针, 但在执行任何写入操作之前, 始终会将其移回文件末尾。 因此，无法覆盖现有数据。

**"A"** 模式不会在将 EOF 标记追加到文件之前将其删除。 在追加后，MS-DOS TYPE 命令只显示原始 EOF 标记之前的数据，不显示追加到文件的任何数据。 在将其追加到文件之前, **"a +"** 模式将删除 EOF 标记。 在追加后，MS-DOS TYPE 命令显示文件中的所有数据。 附加到使用 CTRL + Z EOF 标记终止的流文件需要 **"a +"** 模式。

当指定了 **"r +"** 、 **"w +"** 或 **"a +"** 访问类型时, 将同时启用读取和写入 (该文件称为 "更新")。 但是，当你从读取切换到写入时，输入操作必须遇到 EOF 标记。 如果没有 EOF，必须使用对文件定位函数的干预调用。 文件定位函数包括**fsetpos**、 [fseek](fseek-fseeki64.md)和[倒带](rewind.md)。 当从写入切换到读取时, 必须使用对**fflush**或文件定位函数的干预调用。

除了前面的值以外, 还可以将以下字符追加到*mode*以指定换行符的转换模式。

|*模式*修饰符|转换模式|
|-|-|
| **t** | 在文本（转换）模式下打开。 |
| **b** | 在二进制 (未转换) 模式下打开;将禁止涉及回车符和换行符的翻译。 |

在文本模式下, CTRL + Z 将在输入时解释为 EOF 字符。 在使用 **"a +"** 打开以进行读取/写入的文件中, **fopen**将检查文件末尾的 CTRL + Z 并将其删除 (如果可能)。 这样做的原因是, 使用[fseek](fseek-fseeki64.md)和**FTELL**在以 CTRL + Z 结尾的文件中移动时, 可能会导致[fseek](fseek-fseeki64.md)在文件结尾附近出现错误的行为。

在文本模式下, 回车换行符组合在输入时转换为单行馈送, 换行字符将转换为输出上的回车换行符组合。 当 Unicode 流 I/O 函数在文本模式（默认设置）下运行时，源或目标流将假定为一系列多字节字符。 因此，Unicode 流输入函数将多字节字符转换为宽字符（就像调用 mbtowc  函数一样）。 出于同一原因，Unicode 流输出函数将宽字符转换为多字节字符（就像调用 wctomb  函数一样）。

如果在*mode*中未给出**t**或**b** , 则默认转换模式由全局变量[_fmode](../../c-runtime-library/fmode.md)定义。 如果**t**或**b**作为参数的前缀, 则函数将失败并返回**NULL**。

有关如何在 Unicode 和多字节流 I/O 中使用文本和二进制模式的详细信息，请参阅 [Text and Binary Mode File I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和 [文本和二进制模式下的 Unicode 流 I/O](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)。

可以将以下选项追加到*模式*, 以指定其他行为。

|*模式*修饰符|行为|
|-|-|
| **c** | 启用关联*文件名*的提交标志, 以便在调用**fflush**或 **_flushall**时, 将文件缓冲区的内容直接写入磁盘。 |
| **n** | 将关联的*文件名*的提交标志重置为 "无提交"。 这是默认设置。 如果将程序显式链接到 COMMODE.OBJ，它还将重写全局提交标志。 除非将程序显式链接到 COMMODE.OBJ，否则全局提交标志默认为“no-commit”（请参阅 [Link Options](../../c-runtime-library/link-options.md)）。 |
| **N** | 指定文件不由子进程继承。 |
| **S** | 指定缓存针对（但不限于）从磁盘的顺序访问进行优化。 |
| **R** | 指定缓存针对（但不限于）从磁盘的随机访问进行优化。 |
| **T** | 将文件指定为临时。 如果可能，它不会刷新到磁盘。 |
| **D** | 将文件指定为临时。 最后一个文件指针关闭时，它将被删除。 |
| **ccs=** _encoding_ | 指定要使用的编码字符集 ( **utf-8**、 **utf-16le**或**UNICODE**中的一个)。 如果需要 ANSI 编码，请不要指定此字符集。 |

**Fopen**和 **_fdopen**中使用的*模式*字符串的有效字符与[_open](open-wopen.md)和[_sopen](sopen-wsopen.md)中使用的*oflag*参数对应, 如下所示。

|*模式*字符串中的字符|Open  \_/\_sopen 的等效 oflag 值|
|-------------------------------|----------------------------------------------------|
|**a**|**\_O\_WRONLY** &#124; **oAPPEND\_(通常是 o WRONLY o 的\_** &#124;  **\_\_** &#124;  **\_\_**  **\_O\_追加**)|
|**a+**|**\_O\_RDWR** &#124; &#124; **oappend\_(通常是 o RDWR o append \_**  **\_\_** &#124;  **\_\_**  **\_O\_** 的|
|**r**|\_O\_RDONLY |
|**r+**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** &#124; **( \_WRONLY\_** &#124; o TRUNC **) \_\_**  **\_\_**|
|**w+**|**\_O\_RDWR** (usually **\_O\_RDWR** &#124; **\_O\_CREAT** &#124; **\_O\_TRUNC**)|
|**b**|**\_O\_BINARY**|
|**t**|\_O\_TEXT |
|**c**|None|
|**n**|无|
|**S**|**\_O\_顺序**|
|**R**|**\_O\_RANDOM**|
|**T**|**\_O\_SHORTLIVED**|
|**D**|**\_O\_暂时性**|
|**ccs=UNICODE**|\_O\_WTEXT |
|**ccs=UTF-8**|**\_O\_UTF8**|
|**ccs=UTF-16LE**|**\_O\_UTF16**|

如果你使用的是**rb**模式, 则无需移植代码, 如果你希望读取大文件中的大部分, 或者不关心网络性能, 你还可以考虑是否使用内存映射的 Win32 文件作为选项。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fopen**|\<stdio.h>|
|**_wfopen**|\<stdio.h> 或 \<wchar.h>|

**_wfopen**是 Microsoft 扩展。 有关兼容性的更多信息，请参见 [兼容性](../../c-runtime-library/compatibility.md)。

" **C**"、" **n**"、" **t**"、" **S**"、" **R**"、" **t**" 和 " **D** "*模式*选项是 Microsoft **fopen**和 **_fdopen**的扩展, 不应在需要 ANSI 可移植性时使用。

## <a name="example-1"></a>示例 1

以下程序打开两个文件。  它使用**fclose**关闭第一个文件, 并使用 **_fcloseall**关闭所有剩余文件。

```C
// crt_fopen.c
// compile with: /W3
// This program opens two files. It uses
// fclose to close the first file and
// _fcloseall to close all remaining files.

#include <stdio.h>

FILE *stream, *stream2;

int main( void )
{
   int numclosed;

   // Open for read (will fail if file "crt_fopen.c" does not exist)
   if( (stream  = fopen( "crt_fopen.c", "r" )) == NULL ) // C4996
   // Note: fopen is deprecated; consider using fopen_s instead
      printf( "The file 'crt_fopen.c' was not opened\n" );
   else
      printf( "The file 'crt_fopen.c' was opened\n" );

   // Open for write
   if( (stream2 = fopen( "data2", "w+" )) == NULL ) // C4996
      printf( "The file 'data2' was not opened\n" );
   else
      printf( "The file 'data2' was opened\n" );

   // Close stream if it is not NULL
   if( stream)
   {
      if ( fclose( stream ) )
      {
         printf( "The file 'crt_fopen.c' was not closed\n" );
      }
   }

   // All other files are closed:
   numclosed = _fcloseall( );
   printf( "Number of files closed by _fcloseall: %u\n", numclosed );
}
```

```Output
The file 'crt_fopen.c' was opened
The file 'data2' was opened
Number of files closed by _fcloseall: 1
```

## <a name="example-2"></a>示例 2

以下程序在具有 Unicode 编码的文本模式下创建文件（或在文件存在时覆盖文件）。  然后，它将两个字符串写入文件并关闭文件。 输出是名为 _wfopen_test.xml 的文件，其中包含输出部分中的数据。

```C
// crt__wfopen.c
// compile with: /W3
// This program creates a file (or overwrites one if
// it exists), in text mode using Unicode encoding.
// It then writes two strings into the file
// and then closes the file.

#include <stdio.h>
#include <stddef.h>
#include <stdlib.h>
#include <wchar.h>

#define BUFFER_SIZE 50

int main(int argc, char** argv)
{
    wchar_t str[BUFFER_SIZE];
    size_t  strSize;
    FILE*   fileHandle;

    // Create an the xml file in text and Unicode encoding mode.
    if ((fileHandle = _wfopen( L"_wfopen_test.xml",L"wt+,ccs=UNICODE")) == NULL) // C4996
    // Note: _wfopen is deprecated; consider using _wfopen_s instead
    {
        wprintf(L"_wfopen failed!\n");
        return(0);
    }

    // Write a string into the file.
    wcscpy_s(str, sizeof(str)/sizeof(wchar_t), L"<xmlTag>\n");
    strSize = wcslen(str);
    if (fwrite(str, sizeof(wchar_t), strSize, fileHandle) != strSize)
    {
        wprintf(L"fwrite failed!\n");
    }

    // Write a string into the file.
    wcscpy_s(str, sizeof(str)/sizeof(wchar_t), L"</xmlTag>");
    strSize = wcslen(str);
    if (fwrite(str, sizeof(wchar_t), strSize, fileHandle) != strSize)
    {
        wprintf(L"fwrite failed!\n");
    }

    // Close the file.
    if (fclose(fileHandle))
    {
        wprintf(L"fclose failed!\n");
    }
    return 0;
}
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_fdopen、_wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen、_wfreopen](freopen-wfreopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen、_wsopen](sopen-wsopen.md)<br/>
