---
title: freopen_s、_wfreopen_s | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wfreopen_s
- freopen_s
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
- freopen_s
- _tfreopen_s
- _wfreopen_s
dev_langs:
- C++
helpviewer_keywords:
- _tfreopen_s function
- _wfreopen_s function
- file pointers [C++], reassigning
- tfreopen_s function
- wfreopen_s function
- freopen_s function
ms.assetid: ad25a4da-6ad4-476b-a86d-660b221ca84d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04b136a46672838fd6ee554668353d92796abc7e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="freopens-wfreopens"></a>freopen_s、_wfreopen_s

重新分配文件指针。 这些版本的 [freopen、_wfreopen](freopen-wfreopen.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。

## <a name="syntax"></a>语法

```C
errno_t freopen(
   FILE** pFile,
   const char *path,
   const char *mode,
   FILE *stream
);
errno_t _wfreopen(
   FILE** pFile,
   const wchar_t *path,
   const wchar_t *mode,
   FILE *stream
);
```

### <a name="parameters"></a>参数

*pFile*<br/>
一个指针，指向由调用提供的文件指针。

*path*<br/>
新文件的路径。

*模式*<br/>
允许的访问类型。

*流*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

其中每个函数会返回一个错误代码。 如果发生错误，则关闭原始文件。

## <a name="remarks"></a>备注

**Freopen_s**函数关闭当前与关联的文件*流*，并重新指定*流*到指定的文件*路径*. **_wfreopen_s**是宽字符版本的 **_freopen_s**;*路径*和*模式*自变量 **_wfreopen_s**是宽字符字符串。 **_wfreopen_s**和 **_freopen_s**否则具有相同行为。

如果任一*pFile*，*路径*，*模式*，或*流*是**NULL**，或者如果*路径*为空字符串，这些函数将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数将设置**errno**到**EINVAL**并返回**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen_s**|**freopen_s**|**freopen_s**|**_wfreopen_s**|

**freopen_s**通常用于将预先打开的文件重定向**stdin**， **stdout**，和**stderr**到指定的用户文件。 与关联的新文件*流*使用打开*模式*，后者是一个字符串，指定，如下所示为该文件，请求的访问类型：

|*模式*|Access|
|-|-|
**“r”**|打开以便读取。 如果文件不存在或找不到**freopen_s**调用将失败。
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
|**freopen_s**|\<stdio.h>|
|**_wfreopen_s**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 应用中不支持控制台。 控制台中，与关联的标准流句柄**stdin**， **stdout**，和**stderr**，必须将 C 运行时函数才能使用它们在 UWP 应用重定向. 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_freopen_s.c
// This program reassigns stderr to the file
// named FREOPEN.OUT and writes a line to that file.

#include <stdio.h>
#include <stdlib.h>

FILE *stream;

int main( void )
{
   errno_t err;
   // Reassign "stderr" to "freopen.out":
   err = freopen_s( &stream, "freopen.out", "w", stderr );

   if( err != 0 )
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
[freopen、_wfreopen](freopen-wfreopen.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_fdopen、_wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen、_wfopen_wfopen](fopen-wfopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
