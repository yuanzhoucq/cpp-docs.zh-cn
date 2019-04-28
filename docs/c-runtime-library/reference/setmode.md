---
title: _setmode
ms.date: 11/04/2016
apiname:
- _setmode
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
- _setmode
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
ms.openlocfilehash: 67cca27ba03a99d7e192d438a98f1bb3a93845ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356379"
---
# <a name="setmode"></a>_setmode

设置文件转换模式。

## <a name="syntax"></a>语法

```C
int _setmode (
   int fd,
   int mode
);
```

### <a name="parameters"></a>参数

*fd*<br/>
文件描述符。

*模式*<br/>
新转换模式。

## <a name="return-value"></a>返回值

如果成功，将返回之前的转换模式。

如果传递到此函数的参数无效，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数将返回-1 并集**errno**至任一**EBADF**，这表示一个无效文件说明符，或**EINVAL**，它表示无效*模式下*参数。

有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Setmode**函数设置为*模式*由给定的文件的转换模式*fd*。 传递 **_O_TEXT**作为*模式*设置文本 （即转换） 模式。 回车符-源 (CR-LF) 组合将转换为单个行上输入源字符。 输出时换行符将转换为 CR-LF 组合。 传递 **_O_BINARY**集二进制 （未转换） 模式下，会禁止这些转换。

你还可以传递 **_O_U16TEXT**， **_O_U8TEXT**，或 **_O_WTEXT**启用 Unicode 模式下，在本文档后面的第二个示例中所示。

> [!CAUTION]
> Unicode 模式下是用于宽打印功能 (例如， `wprintf`) 和不支持用于窄的打印功能。 使用有限的打印功能在 Unicode 模式下流触发 assert。

**_setmode**通常用于修改的默认转换模式**stdin**并**stdout**，但可以对任何文件使用它。 如果将应用 **_setmode**到流的文件描述符，调用 **_setmode**执行流上的执行任何输入或输出操作之前。

> [!CAUTION]
> 如果将数据写入文件流，显式刷新代码通过使用[fflush](fflush.md)在使用之前 **_setmode**更改的模式。 如果不刷新代码，可能会导致意外行为。 如果尚未将数据写入流，则不必刷新代码。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|----------------------|
|**_setmode**|\<io.h>|\<fcntl.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[fopen、_wfopen_wfopen](fopen-wfopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_set_fmode](set-fmode.md)<br/>
