---
title: fopen、_wfopen | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- opening files, for file I/O
- wfopen function
- tfopen function
- _tfopen function
- _wfopen function
- files [C++], opening
- fopen function
ms.assetid: e868993f-738c-4920-b5e4-d8f2f41f933d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b606f168448f833a8e244ad35e52faf4f0afd75
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405401"
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

这些函数均返回指向打开文件的指针。 一个 null 指针值指示错误。 如果*filename*或*模式*是**NULL**或空字符串，这些函数将触发的无效参数处理程序中, 所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数将返回**NULL**并设置**errno**到**EINVAL**。

有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**Fopen**函数将打开由指定的文件*filename*。 默认情况下，窄*filename*使用 ANSI 代码页 (CP_ACP) 解释字符串。 在 Windows 桌面应用程序中，可以通过使用 [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534\(v=vs.85\).aspx) 函数将此更改为 OEM 代码页 (CP_OEMCP)。 你可以使用[AreFileApisANSI](https://msdn.microsoft.com/library/windows/desktop/aa363781\(v=vs.85\).aspx)函数来确定是否*filename*解释使用 ANSI 还是系统默认 OEM 代码页。 **_wfopen**是宽字符版本的**fopen**; 的自变量 **_wfopen**是宽字符字符串。 否则为 **_wfopen**和**fopen**具有相同行为。 仅使用 **_wfopen**不会影响在文件流中使用的编码的字符集。

**fopen**接受在执行; 在文件系统上有效的路径**fopen**接受 UNC 路径和涉及的路径映射网络驱动器，前提是执行代码的系统具有访问共享或映射的执行时间的驱动器。 构造路径时**fopen**，请确保驱动器、 路径或网络共享将在执行环境中可用。 可使用斜杠 (/) 或反斜杠 (\\) 作为路径中的目录分隔符。

对文件执行任何其他操作前，请始终检查返回值以确定指针是否为 NULL。 如果发生错误，全局变量**errno**设置和可用于获取特定错误信息。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="unicode-support"></a>Unicode 支持

**fopen**支持 Unicode 文件流。 若要打开 Unicode 文件，请将传递**ccs**指定到所需的编码的标志**fopen**、，如下所示。

> **文件*fp = fopen ("newfile.txt"，"rt + ccs =**_编码_**");**

允许的值的*编码*是**UNICODE**， **utf-8**，和**UTF 16LE**。

当在 Unicode 模式下打开文件时，输入的函数将从文件读取到存储为类型的 utf-16 数据的数据转换**wchar_t**。 写入到在 Unicode 模式下打开的文件的函数需要包含存储为类型的 utf-16 数据的缓冲区**wchar_t**。 如果将文件编码为 UTF-8，则在写入它时，UTF-16 数据会转换为 UTF-8；在读取它时，该文件的 UTF-8 编码的内容会转换为 UTF-16。 尝试在 Unicode 模式下读取或写入奇数个字节会导致 [参数验证](../../c-runtime-library/parameter-validation.md) 错误。 若要读取或写入在你的程序中存储为 UTF-8 的数据，请使用文本或二进制文件模式，而不是 Unicode 模式。 你应负责所有必需的编码转换。

如果文件已存在并已打开以进行读取或追加，字节顺序标记 (BOM)（如果文件中有）将确定编码。 BOM 编码优先于的编码指定**ccs**标志。 **Ccs**没有 bom 或文件是新文件时仅使用编码。

> [!NOTE]
> BOM 检测仅适用于在 Unicode 模式下打开的文件 (即，通过传递**ccs**标志)。

下表总结了用于各种模式**ccs**识别分配给标志**fopen**和文件中的字节顺序标记。

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>基于 ccs 标志和 BOM 使用的编码

|ccs 标志|无 BOM（或新文件）|BOM：UTF-8|BOM：UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

在 Unicode 模式下打开以进行写入的文件将自动写入 BOM。

如果*模式*是 **"，ccs =**_编码_**"**， **fopen**首次尝试通过使用这两个读取打开文件和写入访问权限。 如果成功，此函数将读取 BOM 以确定文件的编码；如果失败，此函数将使用文件的默认编码。 在任一情况下， **fopen**随后将重新打开该文件使用只写访问权限。 (这适用于 **"a"** 模式不适用于仅限 **"a +"** 模式。)

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen**|**fopen**|**fopen**|**_wfopen**|

字符串*模式*指定的请求的文件，如下所示的访问类型。

|*模式*|Access|
|-|-|
**“r”**|打开以便读取。 如果文件不存在或找不到**fopen**调用将失败。
**“w”**|打开用于写入的空文件。 如果给定文件存在，则其内容会被销毁。
**“a”**|在文件末尾打开以进行写入（追加），在新数据写入到文件之前不移除文件末尾 (EOF) 标记。 创建文件（如果文件不存在）。
**“r+”**|打开以便读取和写入。 文件必须存在。
**“w+”**|打开用于读取和写入的空文件。 如果文件存在，则其内容会被销毁。
**“a+”**|打开以进行读取和追加。 追加操作包括在新数据写入文件之前移除 EOF 标记。 写入完成后，EOF 标记不会还原。 创建文件（如果文件不存在）。

通过打开文件时 **"a"** 访问类型或 **"a +"** 访问类型，所有写入操作发生在文件末尾。 通过使用可重新定位文件指针[fseek](fseek-fseeki64.md)或[rewind](rewind.md)，但将始终被移回文件末尾到任何写入操作执行前。 因此，无法覆盖现有数据。

**"A"** 模式不会删除 EOF 标记追加到文件之前。 在追加后，MS-DOS TYPE 命令只显示原始 EOF 标记之前的数据，不显示追加到文件的任何数据。 追加到文件中之前, **"a +"** 模式未删除 EOF 标记。 在追加后，MS-DOS TYPE 命令显示文件中的所有数据。 **"A +"** 模式则需要才能附加到通过 CTRL + Z EOF 标记终止的流文件。

当 **"r +"**， **"w +"**，或 **"a +"** 指定访问类型时，启用读取和写入 （文件将状态才能打开进行"更新"）。 但是，当你从读取切换到写入时，输入操作必须遇到 EOF 标记。 如果没有 EOF，必须使用对文件定位函数的干预调用。 文件定位函数是**fsetpos**， [fseek](fseek-fseeki64.md)，和[rewind](rewind.md)。 当你从写入切换到读取时，你必须使用为的干预调用**fflush**或文件定位函数。

除了前面的值，可以将以下字符追加到*模式*以指定换行符的转换模式。

|*模式*修饰符|转换模式|
|-|-|
**t**|在文本（转换）模式下打开。
**b**|在二进制（未转换）模式下打开；不进行涉及回车和换行字符的转换。

在文本模式下，CTRL + Z 解释为 EOF 字符输入。 以进行读取/写入使用打开的文件中 **"a +"**， **fopen**检查文件末尾的 CTRL + Z 并移除它，如果有可能。 这样做是因为使用[fseek](fseek-fseeki64.md)和**ftell**移动的文件中可能会导致 CTRL + Z 结尾[fseek](fseek-fseeki64.md)文件末尾附近错误运行。

在文本模式下回车换行符组合将转换为单一的换行输入，并换行字符将转换为输出回车返回换行组合。 当 Unicode 流 I/O 函数在文本模式（默认设置）下运行时，源或目标流将假定为一系列多字节字符。 因此，Unicode 流输入函数将多字节字符转换为宽字符（就像调用 mbtowc 函数一样）。 出于同一原因，Unicode 流输出函数将宽字符转换为多字节字符（就像调用 wctomb 函数一样）。

如果**t**或**b**中未给定*模式*，则默认转换模式由全局变量[_fmode](../../c-runtime-library/fmode.md)。 如果**t**或**b**将作为自变量，函数将失败并返回前缀**NULL**。

有关如何在 Unicode 和多字节流 I/O 中使用文本和二进制模式的详细信息，请参阅 [Text and Binary Mode File I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和 [Unicode Stream I/O in Text and Binary Modes](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)。

以下选项可以追加到*模式*以指定其他行为。

|*模式*修饰符|行为|
|-|-|
**c**|启用关联的提交标志*filename* ，以便将文件缓冲区的内容直接写入磁盘如果**fflush**或 **_flushall**调用。
**n**|关联的提交标志重置*filename*为"no-commit。" 这是默认设置。 如果将程序显式链接到 COMMODE.OBJ，它还将重写全局提交标志。 除非将程序显式链接到 COMMODE.OBJ，否则全局提交标志默认为“no-commit”（请参阅 [Link Options](../../c-runtime-library/link-options.md)）。
**N**|指定文件不由子进程继承。
**S**|指定缓存针对（但不限于）从磁盘的顺序访问进行优化。
**R**|指定缓存针对（但不限于）从磁盘的随机访问进行优化。
**T**|将文件指定为临时。 如果可能，它不会刷新到磁盘。
**D**|将文件指定为临时。 最后一个文件指针关闭时，它将被删除。
**ccs =**_编码_|指定将使用的编码的字符集 (之一**utf-8**， **UTF 16LE**，或**UNICODE**) 此文件。 如果需要 ANSI 编码，请不要指定此字符集。

有效字符*模式*中使用的字符串**fopen**和 **_fdopen**对应于*oflag* 中使用的自变量[_open](open-wopen.md)和[_sopen](sopen-wsopen.md)、，如下所示。

|中的字符*模式*字符串|等效*oflag* _open/_sopen 值|
|-------------------------------|----------------------------------------------------|
|**a**|**_O_WRONLY** &#124; **_O_APPEND** (通常 **_O_WRONLY** &#124; **_O_CREAT** &#124;* * _O_APPEND * *)|
|**+**|**_O_RDWR** &#124; **_O_APPEND** (通常 **_O_RDWR** &#124; **_O_APPEND** &#124; **_O_CREAT** )|
|**r**|**_O_RDONLY**|
|**r +**|**_O_RDWR**|
|**w**|**_O_WRONLY** (通常 **_O_WRONLY** &#124; **_O_CREAT** &#124;* * _O_TRUNC * *)|
|**w +**|**_O_RDWR** (通常 **_O_RDWR** &#124; **_O_CREAT** &#124; **_O_TRUNC**)|
|**b**|**_O_BINARY**|
|**t**|**_O_TEXT**|
|**c**|无|
|**n**|无|
|**S**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**D**|**_O_TEMPORARY**|
|**ccs = UNICODE**|**_O_WTEXT**|
|**ccs = utf-8**|**_O_UTF8**|
|**ccs = UTF 16LE**|**_O_UTF16**|

如果你使用**rb**模式下，你无需移植代码，并且如果你希望读取大文件中的大部分或不担心网络性能，你还可以考虑是否使用内存映射的 Win32 文件方式。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fopen**|\<stdio.h>|
|**_wfopen**|\<stdio.h> 或 \<wchar.h>|

**_wfopen**是 Microsoft 扩展。 有关兼容性的更多信息，请参见 [兼容性](../../c-runtime-library/compatibility.md)。

**C**， **n**， **t**， **S**， **R**， **T**，和**D** *模式*选项是 Microsoft 扩展**fopen**和 **_fdopen**和不应需要 ANSI 可移植性时使用。

## <a name="example-1"></a>示例 1

以下程序打开两个文件。  它使用**fclose**关闭第一个文件和 **_fcloseall**关闭所有剩余文件。

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
