---
title: freopen、_wfreopen
ms.date: 4/2/2020
api_name:
- freopen
- _wfreopen
- _o__wfreopen
- _o_freopen
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
- _wfreopen
- _tfreopen
- freopen
helpviewer_keywords:
- _wfreopen function
- file pointers [C++], reassigning
- _tfreopen function
- freopen function
- tfreopen function
- wfreopen function
ms.assetid: de4b73f8-1043-4d62-98ee-30d2022da885
ms.openlocfilehash: 635775469ed6545abd6da43ba27d496d439f80ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345859"
---
# <a name="freopen-_wfreopen"></a>freopen、_wfreopen

重新分配文件指针。 提供这些函数的更安全版本；请参阅 [freopen_s、_wfreopen_s](freopen-s-wfreopen-s.md)。

## <a name="syntax"></a>语法

```C
FILE *freopen(
   const char *path,
   const char *mode,
   FILE *stream
);
FILE *_wfreopen(
   const wchar_t *path,
   const wchar_t *mode,
   FILE *stream
);
```

### <a name="parameters"></a>参数

*路径*<br/>
新文件的路径。

*模式*<br/>
允许的访问类型。

*流*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

这些函数均返回指向新打开的文件的指针。 如果发生错误，原始文件将关闭，并且函数返回**NULL**指针值。 如果*路径*、*模式*或*流*是空指针，或者如果*文件名*是空字符串，则这些函数将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，这些函数将**errno**设置为**EINVAL**并返回**NULL**。

有关这些代码以及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

提供这些函数的更安全版本；请参阅 [freopen_s、_wfreopen_s](freopen-s-wfreopen-s.md)。

**freopen**函数关闭当前与*流*关联的文件，并将*流*重新分配给*路径*指定的文件。 **_wfreopen**是 **_freopen**的宽字符版本;**_wfreopen**的*路径*和*模式*参数是宽字符字符串。 **_wfreopen**和 **_freopen**行为相同。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen**|**freopen**|**freopen**|**_wfreopen**|

**freopen**通常用于将预先打开的文件**stdin、std****和** **stder**重定向到用户指定的文件。 与*流*关联的新文件将打开 mode ，该*模式*是指定文件请求的访问类型的字符串，如下所示：

|*模式*|访问|
|-|-|
| **"r"** | 打开以便读取。 如果文件不存在或找不到，**则 freopen**调用将失败。 |
| **"w"** | 打开用于写入的空文件。 如果给定文件存在，则其内容会被销毁。 |
| **"a"** | 在文件末尾打开以进行写入（追加），在新数据写入到文件之前不移除文件末尾 (EOF) 标记。 创建文件（如果文件不存在）。 |
| **"r+"** | 打开以便读取和写入。 文件必须存在。 |
| **"w+"** | 打开用于读取和写入的空文件。 如果文件存在，则其内容会被销毁。 |
| **"a+"** | 打开以进行读取和追加。 追加操作包括在新数据写入文件之前移除 EOF 标记。 写入完成后，EOF 标记不会还原。 创建文件（如果文件不存在）。 |

小心使用 **"w"** 和 **"w+"** 类型，因为它们可以销毁现有文件。

当使用 **"a"或"a+"** 访问 **"a+"** 类型打开文件时，所有写入操作都发生在文件的末尾。 尽管可以使用[fseek](fseek-fseeki64.md)或[后退](rewind.md)重新定位文件指针，但文件指针始终在进行任何写入操作之前移回文件末尾。因此，无法覆盖现有数据。

在追加到文件之前 **，"a"** 模式不会删除 EOF 标记。 在追加后，MS-DOS TYPE 命令只显示原始 EOF 标记之前的数据，不显示追加到文件的任何数据。 **"a+"** 模式在追加到文件之前确实会删除 EOF 标记。 在追加后，MS-DOS TYPE 命令显示文件中的所有数据。 **"a+"** 模式是追加到使用 CTRL_Z EOF 标记终止的流文件所必需的。

指定 **"r+"、"w+"** 或 **"w+"****"a+"** 访问类型时，允许读取和写入（该文件表示为"更新"打开）。 但是，在读取与写入之间切换时，必须有干预性的 [fsetpos](fsetpos.md)、[fseek](fseek-fseeki64.md) 或 [rewind](rewind.md) 操作。 如果需要，可以为[fsetpos](fsetpos.md)或[fseek](fseek-fseeki64.md)操作指定当前位置。 除了上述值外，*模式*字符串中可能包含以下字符之一，以指定新行的转换模式。

|*模式*修改器|翻译模式|
|-|-|
| **t** | 在文本（转换）模式下打开。 |
| **B** | 在二进制（未翻译）模式下打开;禁止使用涉及回车符和换行符的翻译。 |

在文本（翻译）模式下，车厢返回行馈送 （CR-LF） 组合在输入时转换为单行馈送 （LF） 字符;LF 字符在输出时转换为 CR-LF 组合。 CTRL+Z 也将在输入时解释为文件尾字符。 在打开用于读取或使用 **"a+"** 进行写入和读取的文件中，运行时库会检查文件末尾的 CTRL_Z 并删除它（如果可能）。 这样做是因为使用[fseek](fseek-fseeki64.md)和[ftell](ftell-ftelli64.md)在文件内移动可能会导致[fseek](fseek-fseeki64.md)在文件末尾附近行为不当。 **t**选项是 Microsoft 扩展，在需要 ANSI 可移植性的情况下不应使用。

如果在*模式下*未给出**t**或**b，** 则默认转换模式由全局变量[_fmode](../../c-runtime-library/fmode.md)定义。 如果**t**或**b**预固定到参数，则函数将失败并返回**NULL**。

有关文本模式和二进制模式的讨论，请参阅[文本和二进制模式文件 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**freopen**|\<stdio.h>|
|**_wfreopen**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 （UWP） 应用中不支持该控制台。 在与控制台 **、stdin、stdout**和**stder**关联的标准流句柄必须重定向，C 运行时函数才能在 UWP 应用中使用它们。 **stdout** 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_freopen.c
// compile with: /W3
// This program reassigns stderr to the file
// named FREOPEN.OUT and writes a line to that file.
#include <stdio.h>
#include <stdlib.h>

FILE *stream;

int main( void )
{
   // Reassign "stderr" to "freopen.out":
   stream = freopen( "freopen.out", "w", stderr ); // C4996
   // Note: freopen is deprecated; consider using freopen_s instead

   if( stream == NULL )
      fprintf( stdout, "error on freopen\n" );
   else
   {
      fprintf( stdout, "successfully reassigned\n" ); fflush( stdout );
      fprintf( stream, "This will go to the file 'freopen.out'\n" );
      fclose( stream );
   }
   system( "type freopen.out" );
}
```

```Output
successfully reassigned
This will go to the file 'freopen.out'
```

## <a name="see-also"></a>另请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_fdopen，_wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
