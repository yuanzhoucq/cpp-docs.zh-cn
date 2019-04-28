---
title: fopen_s、_wfopen_s
ms.date: 11/04/2016
apiname:
- _wfopen_s
- fopen_s
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
ms.openlocfilehash: 1309f991b8251bde7d614aa274d8d2e9da7a8ed3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333321"
---
# <a name="fopens-wfopens"></a>fopen_s、_wfopen_s

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

*filename*<br/>
文件名。

*模式*<br/>
允许的访问类型。

## <a name="return-value"></a>返回值

如果成功，则为零；如果失败，则为错误代码。 有关这些错误代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>错误条件

|*pFile*|*filename*|*模式*|返回值|内容*pFile*|
|-------------|----------------|------------|------------------|------------------------|
|**NULL**|任何|任何|**EINVAL**|未更改|
|任何|**NULL**|任何|**EINVAL**|未更改|
|任何|任何|**NULL**|**EINVAL**|未更改|

## <a name="remarks"></a>备注

通过打开的文件**fopen_s**并 **_wfopen_s**不可共享。 如果您需要一个文件是可共享，使用[_fsopen、 _wfsopen](fsopen-wfsopen.md)与相应的共享模式常量 — 例如， **_SH_DENYNO**用于读/写共享。

**Fopen_s**函数将打开由指定的文件*filename*。 **_wfopen_s**是宽字符版本**fopen_s**; 的自变量 **_wfopen_s**都是宽字符字符串。 **_wfopen_s**并**fopen_s**行为相同。

**fopen_s**接受在执行; 时在文件系统上有效的路径通过接受 UNC 路径和涉及的映射的网络驱动器的路径**fopen_s** ，前提执行代码的系统有权访问该共享，或在执行时映射网络驱动器。 构造路径时**fopen_s**，不要做出有关可用性的驱动器、 路径或网络共享执行环境中。 可使用斜杠 (/) 或反斜杠 (\\) 作为路径中的目录分隔符。

这些函数验证其参数。 如果*pFile*， *filename*，或*模式*是 null 指针，这些函数将生成无效的参数异常，如中所述[参数验证](../../c-runtime-library/parameter-validation.md).

请始终先检查返回值，确定该函数是否成功，再对文件执行任何进一步的操作。 如果发生错误，则返回错误代码和全局变量**errno**设置。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="unicode-support"></a>Unicode 支持

**fopen_s**支持 Unicode 文件流。 若要打开新的或现有的 Unicode 文件，请将传递*ccs*指定为所需的编码的标志**fopen_s**:

**fopen_s(&fp, "newfile.txt", "rw, ccs=**_encoding_**");**

允许的值为*编码*都**UNICODE**， **utf-8**，以及**UTF 16LE**。 如果存在用于不指定任何值*编码*， **fopen_s**使用 ANSI 编码。

如果文件已存在并已打开以进行读取或追加，则字节顺序标记 (BOM)（如果文件中存在）将确定编码。 BOM 编码优先的编码指定的*ccs*标志。 *Ccs*编码时，才使用任何不存在 BOM 或如果文件是新文件。

> [!NOTE]
> BOM 检测仅适用于在 Unicode 模式下; 打开的文件也就是说，通过传递*ccs*标志。

下表汇总的模式为各种*ccs*为指定的标志**fopen_s**和文件中的字节顺序标记。

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>基于 ccs 标志和 BOM 使用的编码

|ccs 标志|无 BOM（或新文件）|物料清单：UTF-8|物料清单：UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

在 Unicode 模式下打开用于写入的文件将自动在其中写入 BOM。

如果*模式下*是 **"，ccs =**_编码_**"**， **fopen_s**首次尝试打开该文件具有两个读取访问和写入访问权限。 如果成功，此函数将读取 BOM 以确定文件的编码；如果失败，此函数将使用文件的默认编码。 在任一情况下， **fopen_s**然后重新打开该文件具有只写访问权限。 (这适用于模式下唯一，非**a +**。)

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen_s**|**fopen_s**|**fopen_s**|**_wfopen_s**|

字符字符串*模式下*指定类型的访问请求时，对于文件，请按如下所示。

|*模式*|Access|
|-|-|
| **“r”** | 打开以便读取。 如果文件不存在或无法找到**fopen_s**调用失败。 |
| **“w”** | 打开用于写入的空文件。 如果给定文件存在，则其内容会被销毁。 |
| **“a”** | 在文件末尾打开以进行写入（追加），在新数据写入到文件之前不移除文件末尾 (EOF) 标记。 创建文件（如果文件不存在）。 |
| **“r+”** | 打开以便读取和写入。 文件必须存在。 |
| **“w+”** | 打开用于读取和写入的空文件。 如果文件存在，则其内容会被销毁。 |
| **“a+”** | 打开以进行读取和追加。 追加操作包括在新数据写入文件之前移除 EOF 标记。 写入完成后，EOF 标记不会还原。 创建文件（如果文件不存在）。 |

通过打开文件时 **"a"** 或 **"a +"** 访问类型，所有写入操作可能出现在文件末尾。 通过使用可重新定位文件指针[fseek](fseek-fseeki64.md)或[rewind](rewind.md)，但它将始终被移回文件末尾之前任何写入操作执行，因此无法覆盖现有数据。

**"A"** 模式不会追加到文件之前移除 EOF 标记。 追加后，MS-DOS TYPE 命令仅显示原始 EOF 标记之前的数据，不显示追加到文件的任何数据。 **"A +"** 模式 does 追加到文件之前移除 EOF 标记。 在追加后，MS-DOS TYPE 命令显示文件中的所有数据。 **"A +"** 模式是所必需的追加到通过使用 CTRL + Z EOF 标记终止的流文件。

当 **"r +"**， **"w +"**，或 **"a +"** 指定访问类型时，允许读取和写入。 （文件将处于打开状态以进行“更新”。）但是，当你从读取切换到写入时，输入操作必须遇到 EOF 标记。 如果没有 EOF，必须使用对文件定位函数的干预调用。 文件定位函数是**fsetpos**， [fseek](fseek-fseeki64.md)，并[后退](rewind.md)。 当您从写入切换到读取时，必须使用为的干预调用**fflush**或对文件定位函数。

除了以上值，可以在包含以下字符*模式下*以指定换行符的转换模式：

|*模式*修饰符|转换模式|
|-|-|
| **t** | 在文本（转换）模式下打开。 |
| **b** | 在二进制（未转换）模式下打开；不进行涉及回车和换行字符的转换。 |

在文本 （转换） 模式下，CTRL + Z 解释为文件尾字符在输入。 以进行读取/写入与打开的文件中 **"a +"**， **fopen_s**检查文件末尾的 CTRL + Z 并在可能的情况下将其移除。 这是因为使用[fseek](fseek-fseeki64.md)并**ftell** CTRL + Z 结尾可能会导致文件内移动[fseek](fseek-fseeki64.md)文件末尾附近运行不当。

此外，在文本模式下，回车-换行组合将转换为单一的换行输入，并换行字符转换为输出回车-换行组合。 当 Unicode 流 I/O 函数在文本模式（默认设置）下运行时，源或目标流将假定为一系列多字节字符。 因此，Unicode 流输入函数将多字节字符转换为宽字符（就像调用 mbtowc 函数一样）。 出于同一原因，Unicode 流输出函数将宽字符转换为多字节字符（就像调用 wctomb 函数一样）。

如果**t**或**b**中未给*模式*，则默认转换模式由全局变量[_fmode](../../c-runtime-library/fmode.md)。 如果**t**或**b**自变量、 函数将失败并返回到前缀**NULL**。

有关在 Unicode 和多字节流 I/O 中使用文本和二进制模式的详细信息，请参阅[文本和二进制模式文件 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和[文本和二进制模式下的 Unicode 流 I/O](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)。

|*模式*修饰符|行为|
|-|-|
| **c** | 启用关联的提交标志*文件名*，以便文件缓冲区的内容直接写入磁盘**fflush**或 **_flushall**调用。 |
| **n** | 重置为关联的提交标志*文件名*到"不提交。" 这是默认设置。 如果将程序显式链接到 COMMODE.OBJ，它还将重写全局提交标志。 除非将程序显式链接到 COMMODE.OBJ，否则全局提交标志默认为“no-commit”（请参阅 [Link Options](../../c-runtime-library/link-options.md)）。 |
| **N** | 指定文件不由子进程继承。 |
| **S** | 指定缓存针对（但不限于）从磁盘的顺序访问进行优化。 |
| **R** | 指定缓存针对（但不限于）从磁盘的随机访问进行优化。 |
| **T** | 将文件指定为临时。 如果可能，它不会刷新到磁盘。 |
| **D** | 将文件指定为临时。 最后一个文件指针关闭时，它将被删除。 |
| **ccs=**_encoding_ | 指定设置为使用的编码的字符 (之一**utf-8**， **UTF 16LE**，或**UNICODE**) 此文件。 如果需要 ANSI 编码，请不要指定此字符集。 |

有效字符*模式下*中使用字符串**fopen_s**并[_fdopen](fdopen-wfdopen.md)对应于*oflag*中使用的参数[_打开](open-wopen.md)并[_sopen](sopen-wsopen.md)，按如下所示。

|中的字符*模式下*字符串|等效*oflag* _open/_sopen 值|
|-------------------------------|----------------------------------------------------|
|**a**|**_O_WRONLY** &#124; **_O_APPEND** (usually **_O_WRONLY** &#124; **_O_CREAT** &#124;** _O_APPEND**)|
|**a+**|**_O_RDWR** &#124; **_O_APPEND** (usually **_O_RDWR** &#124; **_O_APPEND** &#124; **_O_CREAT** )|
|**r**|**_O_RDONLY**|
|**r+**|**_O_RDWR**|
|**w**|**_O_WRONLY** (usually **_O_WRONLY** &#124; **_O_CREAT** &#124;** _O_TRUNC**)|
|**w+**|**_O_RDWR** (usually **_O_RDWR** &#124; **_O_CREAT** &#124; **_O_TRUNC**)|
|**b**|**_O_BINARY**|
|**t**|**_O_TEXT**|
|**c**|None|
|**n**|None|
|**S**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**D**|**_O_TEMPORARY**|
|**ccs=UNICODE**|**_O_WTEXT**|
|**ccs=UTF-8**|**_O_UTF8**|
|**ccs=UTF-16LE**|**_O_UTF16**|

如果使用的**rb**模式下，无需移植代码，并且预计将读取大量文件和/或不关心网络性能、 内存映射的 Win32 文件也可能是一个选项。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fopen_s**|\<stdio.h>|
|**_wfopen_s**|\<stdio.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

**C**， **n**，并**t** *模式*选项是 Microsoft 扩展**fopen_s**和[_fdopen](fdopen-wfdopen.md) ，不应在需要 ANSI 可移植性时使用。

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

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_fdopen、_wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen、_wfreopen](freopen-wfreopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
