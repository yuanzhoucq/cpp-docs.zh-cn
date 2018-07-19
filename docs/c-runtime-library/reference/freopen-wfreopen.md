---
title: freopen、_wfreopen | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- freopen
- _wfreopen
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
- _wfreopen
- _tfreopen
- freopen
dev_langs:
- C++
helpviewer_keywords:
- _wfreopen function
- file pointers [C++], reassigning
- _tfreopen function
- freopen function
- tfreopen function
- wfreopen function
ms.assetid: de4b73f8-1043-4d62-98ee-30d2022da885
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1d3c121dbe80f2eb6def9e1040b03a7b04d03689
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405583"
---
# <a name="freopen-wfreopen"></a>freopen、_wfreopen

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

*path*<br/>
新文件的路径。

*模式*<br/>
允许的访问类型。

*流*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

这些函数均返回指向新打开的文件的指针。 如果发生错误，则关闭原始文件，该函数将返回**NULL**指针值。 如果*路径*，*模式*，或*流*是 null 指针，或如果*filename*为空字符串，这些函数将调用无效的参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数将设置**errno**到**EINVAL**并返回**NULL**。

有关这些代码以及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

提供这些函数的更安全版本；请参阅 [freopen_s、_wfreopen_s](freopen-s-wfreopen-s.md)。

**Freopen**函数关闭当前与关联的文件*流*，并重新指定*流*到指定的文件*路径*。 **_wfreopen**是宽字符版本的 **_freopen**;*路径*和*模式*自变量 **_wfreopen**是宽字符字符串。 **_wfreopen**和 **_freopen**否则具有相同行为。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen**|**freopen**|**freopen**|**_wfreopen**|

**freopen**通常用于将预先打开的文件重定向**stdin**， **stdout**，和**stderr**到指定的用户文件。 与关联的新文件*流*使用打开*模式*，后者是一个字符串，指定，如下所示为该文件，请求的访问类型：

|*模式*|Access|
|-|-|
**“r”**|打开以便读取。 如果文件不存在或找不到**freopen**调用将失败。
**“w”**|打开用于写入的空文件。 如果给定文件存在，则其内容会被销毁。
**“a”**|在文件末尾打开以进行写入（追加），在新数据写入到文件之前不移除文件末尾 (EOF) 标记。 创建文件（如果文件不存在）。
**“r+”**|打开以便读取和写入。 文件必须存在。
**“w+”**|打开用于读取和写入的空文件。 如果文件存在，则其内容会被销毁。
**“a+”**|打开以进行读取和追加。 追加操作包括在新数据写入文件之前移除 EOF 标记。 写入完成后，EOF 标记不会还原。 创建文件（如果文件不存在）。

使用 **"w"** 和 **"w +"** 类型时要小心，因为它们可能会销毁现有文件。

当用打开文件时 **"a"** 或 **"a +"** 访问类型，所有写入操作均将在文件末尾。 尽管可以使用重新定位文件指针[fseek](fseek-fseeki64.md)或[rewind](rewind.md)，文件指针将始终被移回文件末尾到任何写入操作执行前。因此，无法覆盖现有数据。

**"A"** 模式不会追加到文件之前删除 EOF 标记。 在追加后，MS-DOS TYPE 命令只显示原始 EOF 标记之前的数据，不显示追加到文件的任何数据。 **"A +"** 模式未追加到文件之前移除 EOF 标记。 在追加后，MS-DOS TYPE 命令显示文件中的所有数据。 **"A +"** 模式则需要才能附加到通过 CTRL + Z EOF 标记终止的流文件。

当 **"r +"**， **"w +"**，或 **"a +"** 指定访问类型，允许读取和写入 （文件将状态才能打开进行"更新"）。 但是，在读取与写入之间切换时，必须有干预性的 [fsetpos](fsetpos.md)、[fseek](fseek-fseeki64.md) 或 [rewind](rewind.md) 操作。 可以为指定当前位置[fsetpos](fsetpos.md)或[fseek](fseek-fseeki64.md)操作，如果所需的。 除了以上值，以下字符之一可能包括在*模式*字符串，以指定换行符的转换模式。

|*模式*修饰符|转换模式|
|-|-|
**t**|在文本（转换）模式下打开。
**b**|在二进制（未转换）模式下打开；不进行涉及回车和换行字符的转换。

在文本 （转换） 模式下，回车换行符 (CR-LF) 组合将转换为单一的换行 (LF) 字符输入;LF 字符将转换为 CR-LF 组合输出。 CTRL+Z 也将在输入时解释为文件尾字符。 在打开的文件进行读取或写入和读取与 **"a +"**，运行时库检查文件末尾的 CTRL + Z 并移除它，如有可能。 这样做是因为使用[fseek](fseek-fseeki64.md)和[ftell](ftell-ftelli64.md)在文件内移动可能会导致[fseek](fseek-fseeki64.md)文件末尾附近运行不当。 **T**选项是一个 Microsoft 扩展，不应需要 ANSI 可移植性时使用。

如果**t**或**b**中未给定*模式*，则默认转换模式由全局变量[_fmode](../../c-runtime-library/fmode.md)。 如果**t**或**b**将作为自变量，函数将失败并返回前缀**NULL**。

有关文本模式和二进制模式的讨论，请参阅[文本和二进制模式文件 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**freopen**|\<stdio.h>|
|**_wfreopen**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 应用中不支持控制台。 控制台中，与关联的标准流句柄**stdin**， **stdout**，和**stderr**，必须将 C 运行时函数才能使用它们在 UWP 应用重定向. 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_fdopen、_wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen、_wfopen_wfopen](fopen-wfopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
