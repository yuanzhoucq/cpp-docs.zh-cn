---
title: fflush | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fflush
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
- fflush
dev_langs:
- C++
helpviewer_keywords:
- streams, flushing
- flushing
- fflush function
ms.assetid: 8bbc753f-dc74-4e77-b563-74da2835e92b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72f0812e713d0d474363dcc5f79cc11eddb46020
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="fflush"></a>fflush

刷新流。

## <a name="syntax"></a>语法

```C
int fflush(
   FILE *stream
);
```

### <a name="parameters"></a>参数

*流*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

**fflush**返回 0，如果已成功刷新缓冲区。 在指定流无缓冲区或处于打开状态以仅供读取的情况下，也会返回值 0。 返回值**EOF**指示错误。

> [!NOTE]
> 如果**fflush**返回**EOF**，数据可能已经由于写入故障而丢失。 设置时严重错误处理程序，它是最安全的做法是，若要关闭缓冲与**setvbuf**函数或使用低级别 I/O 例程如 **_open**， **_close**，和 **_write**而不是流 I/O 函数。

## <a name="remarks"></a>备注

**Fflush**函数刷新流*流*。 如果以写入模式打开流，或者以更新模式打开并且最后一个操作是写入，则流缓冲区的内容会被写入到基础文件，否则设备和缓冲区将被丢弃。 如果在读取模式下，已打开的流或流并不具有缓冲区，对的调用**fflush**不起作用，并保留任何缓冲区。 调用**fflush**求反的任何调用的效果**ungetc**为流。 调用后，该流保持打开状态。

如果*流*是**NULL**，行为是调用相同**fflush**有关每个打开的流。 最后一次操作是写入的所有以写入模式打开的流以及所有以更新模式打开的流都将被刷新。 调用对其他流无效。

缓冲区通常由操作系统维护，操作系统确定将数据自动写入磁盘的最佳时间：当缓冲区已满时、当流已关闭时或当程序在未关闭流的情况下正常终止时。 利用运行时库的提交到磁盘功能，可以确保将关键数据直接写入磁盘而不是操作系统的缓冲区。 无需重写现有程序，可以通过将程序的对象文件与 COMMODE.OBJ 链接来启用此功能。 在生成的可执行文件中，调用 **_flushall**将所有缓冲区的内容写入到磁盘。 仅 **_flushall**和**fflush**受 COMMODE.OBJ。

有关控制提交到磁盘功能的信息，请参阅[流 I/O](../../c-runtime-library/stream-i-o.md)、[fopen](fopen-wfopen.md) 和 [_fdopen](fdopen-wfdopen.md)。

此函数会锁定调用线程，因此是线程安全的。 有关非锁定版本，请参阅 **_fflush_nolock**。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fflush**|\<stdio.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_fflush.c
#include <stdio.h>
#include <conio.h>

int main( void )
{
   int integer;
   char string[81];

   // Read each word as a string.
   printf( "Enter a sentence of four words with scanf: " );
   for( integer = 0; integer < 4; integer++ )
   {
      scanf_s( "%s", string, sizeof(string) );
      printf( "%s\n", string );
   }

   // You must flush the input buffer before using gets.
   // fflush on input stream is an extension to the C standard
   fflush( stdin );
   printf( "Enter the same sentence with gets: " );
   gets_s( string, sizeof(string) );
   printf( "%s\n", string );
}
```

```Output

      This is a test
This is a test

```

```Output

      This is a test
This is a testEnter a sentence of four words with scanf: This is a test
This
is
a
test
Enter the same sentence with gets: This is a test
This is a test
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_flushall](flushall.md)<br/>
[setvbuf](setvbuf.md)<br/>
