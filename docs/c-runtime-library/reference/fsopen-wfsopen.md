---
title: _fsopen、_wfsopen
ms.date: 4/2/2020
api_name:
- _wfsopen
- _fsopen
- _o__fsopen
- _o__wfsopen
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
- wfsopen
- fsopen
- tfsopen
- _tfsopen
- _wfsopen
- _fsopen
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
ms.openlocfilehash: 49907808729375e3bea18a5f4bbf204852e0072a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345701"
---
# <a name="_fsopen-_wfsopen"></a>_fsopen、_wfsopen

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

*文件名*<br/>
要打开的文件的名称。

*模式*<br/>
允许的访问类型。

*什弗拉格*<br/>
允许的共享类型。

## <a name="return-value"></a>返回值

这些函数均返回指向流的指针。 一个 null 指针值指示错误。 如果*文件名*或*模式*为**NULL**或空字符串，这些函数将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，这些函数将返回**NULL**并将**errno**设置为**EINVAL**。

有关这些及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_fsopen**函数将*文件名*指定的文件作为流打开，并为文件准备供后续共享读取或写入（由模式定义）和 *"鞭打*参数"。 **_wfsopen**是 **_fsopen**的宽字符版本;要 **_wfsopen***的文件名*和*模式*参数是宽字符字符串。 **_wfsopen**和 **_fsopen**行为相同。

字符字符串*模式*指定为文件请求的访问类型，如下表所示。

|术语|定义|
|----------|----------------|
|**"r"**|打开以便读取。 如果文件不存在或找不到，**则_fsopen**调用失败。|
|**"w"**|打开用于写入的空文件。 如果给定文件存在，则其内容会被销毁。|
|**"a"**|打开以便在文件末尾进行写入（追加）；如果文件不存在，则首先创建它。|
|**"r+"**|打开以便读取和写入。 （该文件必须存在。）|
|**"w+"**|打开用于读取和写入的空文件。 如果给定文件存在，则其内容会被销毁。|
|**"a+"**|打开以便进行读取和追加；如果文件不存在，则首先创建它。|

小心使用 **"w"** 和 **"w+"** 类型，因为它们可以销毁现有文件。

当使用 **"a"或"a+"** 访问 **"a+"** 类型打开文件时，所有写入操作都发生在文件的末尾。 可以使用[fseek](fseek-fseeki64.md)或[后退](rewind.md)重新定位文件指针，但在执行任何写入操作之前，该文件指针始终被移回文件末尾。因此，无法覆盖现有数据。 指定 **"r+"、"w+"** 或 **"w+"****"a+"** 访问类型时，允许读取和写入（该文件表示打开以进行更新）。 但是，在读取与写入之间切换时，必须有中间 [fsetpos](fsetpos.md)、[fseek](fseek-fseeki64.md) 或 [rewind](rewind.md) 操作。 如果需要，可以为[fsetpos](fsetpos.md)或[fseek](fseek-fseeki64.md)操作指定当前位置。 除了上述值之外，还可以将以下字符之一包含在*模式下*，以指定新行的转换模式和文件管理。

|术语|定义|
|----------|----------------|
|**t**|在文本（转换）模式下打开文件。 在此模式下，车厢回线馈送 （CR-LF） 组合在输入时转换为单行馈送 （LF），在输出时将 LF 字符转换为 CR-LF 组合。 CTRL+Z 也将在输入时解释为文件尾字符。 在打开用于读取或读取/写入的文件中 **，_fsopen**检查文件末尾的 CTRL_Z 并尽可能将其删除。 这样做是因为使用[fseek](fseek-fseeki64.md)和[ftell](ftell-ftelli64.md)在以 CTRL_Z 结尾的文件内移动可能会导致[fseek](fseek-fseeki64.md)在文件末尾附近行为不当。|
|**B**|在二进制（未转换）模式下打开文件；禁止上述转换。|
|**S**|指定缓存针对（但不限于）从磁盘的顺序访问进行优化。|
|**R**|指定缓存针对（但不限于）从磁盘的随机访问进行优化。|
|**T**|将文件指定为临时。 如果可能，它不会刷新到磁盘。|
|**D**|将文件指定为临时。 最后一个文件指针关闭时，它将被删除。|

如果在 mode** 中未给出 t**** 或 b****，则转换模式由默认模式变量 **_fmode** 定义。 如果**t**或**b**预固定到参数，则函数将失败并返回**NULL**。 有关文本模式和二进制模式的讨论，请参阅[文本和二进制模式文件 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。

参数*shflag*是一个常量表达式，由以下清单常量之一组成，在 Share.h 中定义。

|术语|定义|
|----------|----------------|
|**_SH_COMPAT**|为 16 位应用程序设置兼容性模式。|
|**_SH_DENYNO**|允许读取和写入访问。|
|**_SH_DENYRD**|拒绝对文件的读取访问。|
|**_SH_DENYRW**|拒绝对文件的读取和写入访问。|
|**_SH_DENYWR**|拒绝对文件的写入访问。|

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfsopen**|**_fsopen**|**_fsopen**|**_wfsopen**|

## <a name="requirements"></a>要求

|函数|必需的标头|可选标头|
|--------------|---------------------|----------------------|
|**_fsopen**|\<stdio.h>|\<share.h 1><br /><br /> 对于*shflag*参数的清单常量。|
|**_wfsopen**|\<stdio.h> 或 \<wchar.h>|\<share.h 1><br /><br /> 对于*shflag*参数的清单常量。|

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

## <a name="see-also"></a>另请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_fdopen，_wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[freopen、_wfreopen](freopen-wfreopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen、_wsopen](sopen-wsopen.md)<br/>
