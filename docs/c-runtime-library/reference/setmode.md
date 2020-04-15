---
title: _setmode
ms.date: 4/2/2020
api_name:
- _setmode
- _o__setmode
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
- _setmode
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
ms.openlocfilehash: 36d2130d4039f1f87f7f54fc26ad02cb8d519b4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353839"
---
# <a name="_setmode"></a>_setmode

设置文件转换模式。

## <a name="syntax"></a>语法

```C
int _setmode (
   int fd,
   int mode
);
```

### <a name="parameters"></a>参数

*Fd*<br/>
文件描述符。

*模式*<br/>
新转换模式。

## <a name="return-value"></a>返回值

如果成功，将返回之前的转换模式。

如果传递到此函数的参数无效，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，此函数将返回 -1 并将**errno**设置给**EBADF**，指示无效的文件描述符，或**EINVAL**，指示无效*的模式*参数。

有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_setmode**函数集以*模式* *fd*给出的文件的转换模式。 传递 **_O_TEXT***模式*设置文本（即已翻译）模式。 车厢返回线馈送 （CR-LF） 组合在输入时转换为单个换行字符。 输出时换行符将转换为 CR-LF 组合。 传递 **_O_BINARY**设置二进制（未翻译）模式，其中将抑制这些翻译。

您还可以通过 **_O_U16TEXT、_O_U8TEXT****_O_U8TEXT**或 **_O_WTEXT**来启用 Unicode 模式，本文档后面的第二个示例将演示。

> [!CAUTION]
> Unicode 模式适用于宽打印功能（例如），`wprintf`对于窄打印功能，不支持。 在 Unicode 模式流上使用窄打印函数会触发断言。

**_setmode**通常用于修改**stdin**和**stdout**的默认转换模式，但您可以在任何文件上使用它。 如果将 **_setmode**应用于流的文件描述符，请**先调用_setmode，** 然后再对流执行任何输入或输出操作。

> [!CAUTION]
> 如果将数据写入文件流，则在使用 **_setmode**更改模式之前，请使用[fflush](fflush.md)显式刷新代码。 如果不刷新代码，可能会导致意外行为。 如果尚未将数据写入流，则不必刷新代码。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|----------------------|
|**_setmode**|\<io.h>|\<fcntl.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_setmode.c
// This program uses _setmode to change
// stdin from text mode to binary mode.

#include <stdio.h>
#include <fcntl.h>
#include <io.h>

int main( void )
{
   int result;

   // Set "stdin" to have binary mode:
   result = _setmode( _fileno( stdin ), _O_BINARY );
   if( result == -1 )
      perror( "Cannot set mode" );
   else
      printf( "'stdin' successfully changed to binary mode\n" );
}
```

```Output
'stdin' successfully changed to binary mode
```

## <a name="example"></a>示例

```C
// crt_setmodeunicode.c
// This program uses _setmode to change
// stdout to Unicode. Cyrillic and Ideographic
// characters will appear on the console (if
// your console font supports those character sets).

#include <fcntl.h>
#include <io.h>
#include <stdio.h>

int main(void) {
    _setmode(_fileno(stdout), _O_U16TEXT);
    wprintf(L"\x043a\x043e\x0448\x043a\x0430 \x65e5\x672c\x56fd\n");
    return 0;
}
```

## <a name="see-also"></a>另请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_set_fmode](set-fmode.md)<br/>
