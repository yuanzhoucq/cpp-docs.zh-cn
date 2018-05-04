---
title: _fsopen、_wfsopen | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wfsopen
- _fsopen
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
- wfsopen
- fsopen
- tfsopen
- _tfsopen
- _wfsopen
- _fsopen
dev_langs:
- C++
helpviewer_keywords:
- opening files, streams
- fsopen function
- tfsopen function
- wfsopen function
- _fsopen function
- files [C++], opening
- _tfsopen function
- _wfsopen function
- file sharing [C++]
ms.assetid: 5e4502ab-48a9-4bee-a263-ebac8d638dec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ce69c6789ba65f61c54957dde3dfa6965bc32e2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="fsopen-wfsopen"></a>_fsopen、_wfsopen

打开具有文件共享的流。

## <a name="syntax"></a>语法

```C
FILE *_fsopen(
   const char *filename,
   const char *mode,
   int shflag
);
FILE *_wfsopen(
   const wchar_t *filename,
   const wchar_t *mode,
   int shflag
);
```

### <a name="parameters"></a>参数

*filename*<br/>
要打开的文件的名称。

*模式*<br/>
允许的访问类型。

*shflag*<br/>
允许的共享类型。

## <a name="return-value"></a>返回值

这些函数均返回指向流的指针。 一个 null 指针值指示错误。 如果*filename*或*模式*是**NULL**或空字符串，这些函数将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md). 如果允许执行继续，则这些函数将返回**NULL**并设置**errno**到**EINVAL**。

有关这些及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Fsopen**函数将打开指定的文件*filename*作为流并使该文件做好准备以进行后续的共享的读写，定义的模式和*shflag*自变量。 **_wfsopen**是宽字符版本的 **_fsopen**; *filename*和*模式*自变量 **_wfsopen**是宽字符字符串。 **_wfsopen**和 **_fsopen**否则具有相同行为。

字符串*模式*下表中所示指定为该文件，请求的访问的类型。

|术语|定义|
|----------|----------------|
|**“r”**|打开以便读取。 如果文件不存在或找不到 **_fsopen**调用将失败。|
|**“w”**|打开用于写入的空文件。 如果给定文件存在，则其内容会被销毁。|
|**“a”**|打开以便在文件末尾进行写入（追加）；如果文件不存在，则首先创建它。|
|**“r+”**|打开以便读取和写入。 （该文件必须存在。）|
|**“w+”**|打开用于读取和写入的空文件。 如果给定文件存在，则其内容会被销毁。|
|**“a+”**|打开以便进行读取和追加；如果文件不存在，则首先创建它。|

使用 **"w"** 和 **"w +"** 类型时要小心，因为它们可能会销毁现有文件。

当用打开文件时 **"a"** 或 **"a +"** 访问类型，所有写入操作发生在文件末尾。 可以使用重新定位文件指针[fseek](fseek-fseeki64.md)或[rewind](rewind.md)，但它将始终被移回文件末尾到任何写入操作执行前。因此，无法覆盖现有数据。 当 **"r +"**， **"w +"**，或 **"a +"** 指定访问类型，允许读取和写入 （文件将状态以执行更新处于打开状态）。 但是，在读取与写入之间切换时，必须有中间 [fsetpos](fsetpos.md)、[fseek](fseek-fseeki64.md) 或 [rewind](rewind.md) 操作。 可以为指定当前位置[fsetpos](fsetpos.md)或[fseek](fseek-fseeki64.md)操作，如果所需的。 除了以上值，以下字符之一可以包含在*模式*以指定换行符和文件管理的转换模式。

|术语|定义|
|----------|----------------|
|**t**|在文本（转换）模式下打开文件。 在此模式下，回车符返回行源 (CR-LF) 组合将转换为单个换行符 (LF) 则在输入和 LF 字符将转换为 CR-LF 组合输出。 CTRL+Z 也将在输入时解释为文件尾字符。 打开以进行读取或读取/写入的文件中 **_fsopen**检查文件末尾的 CTRL + Z 并删除它，如有可能。 这样做是因为使用[fseek](fseek-fseeki64.md)和[ftell](ftell-ftelli64.md)移动的文件中可能会导致 CTRL + Z 结尾[fseek](fseek-fseeki64.md)文件末尾附近运行不当。|
|**b**|在二进制（未转换）模式下打开文件；禁止上述转换。|
|**S**|指定缓存针对（但不限于）从磁盘的顺序访问进行优化。|
|**R**|指定缓存针对（但不限于）从磁盘的随机访问进行优化。|
|**T**|将文件指定为临时。 如果可能，它不会刷新到磁盘。|
|**D**|将文件指定为临时。 最后一个文件指针关闭时，它将被删除。|

如果在 mode 中未给出 t 或 b，则转换模式由默认模式变量 **_fmode** 定义。 如果**t**或**b**将作为自变量，函数将失败并返回前缀**NULL**。 有关文本模式和二进制模式的讨论，请参阅[文本和二进制模式文件 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。

自变量*shflag*是常量表达式包含 Share.h 中定义的以下清单常量之一。

|术语|定义|
|----------|----------------|
|**_SH_COMPAT**|为 16 位应用程序设置兼容性模式。|
|**_SH_DENYNO**|允许读取和写入访问。|
|**_SH_DENYRD**|拒绝对文件的读取访问。|
|**_SH_DENYRW**|拒绝对文件的读取和写入访问。|
|**_SH_DENYWR**|拒绝对文件的写入访问。|

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfsopen**|**_fsopen**|**_fsopen**|**_wfsopen**|

## <a name="requirements"></a>要求

|函数|必需的标头|可选标头|
|--------------|---------------------|----------------------|
|**_fsopen**|\<stdio.h>|\<share.h 1><br /><br /> 为清单常量*shflag*参数。|
|**_wfsopen**|\<stdio.h> 或 \<wchar.h>|\<share.h 1><br /><br /> 为清单常量*shflag*参数。|

## <a name="example"></a>示例

```C
// crt_fsopen.c

#include <stdio.h>
#include <stdlib.h>
#include <share.h>

int main( void )
{
   FILE *stream;

   // Open output file for writing. Using _fsopen allows us to
   // ensure that no one else writes to the file while we are
   // writing to it.
    //
   if( (stream = _fsopen( "outfile", "wt", _SH_DENYWR )) != NULL )
   {
      fprintf( stream, "No one else in the network can write "
                       "to this file until we are done.\n" );
      fclose( stream );
   }
   // Now others can write to the file while we read it.
   system( "type outfile" );
}
```

```Output
No one else in the network can write to this file until we are done.
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_fdopen、_wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[fopen、_wfopen_wfopen](fopen-wfopen.md)<br/>
[freopen、_wfreopen](freopen-wfreopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen、_wsopen](sopen-wsopen.md)<br/>
