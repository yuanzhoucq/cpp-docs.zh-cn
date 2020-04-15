---
title: _flushall
ms.date: 4/2/2020
api_name:
- _flushall
- _o__flushall
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
- _flushall
helpviewer_keywords:
- flushall function
- flushing streams
- streams, flushing
- _flushall function
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
ms.openlocfilehash: 93181c0fe941a1c5e259e706771495666329bcb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346624"
---
# <a name="_flushall"></a>_flushall

刷新所有流；清除所有缓冲区。

## <a name="syntax"></a>语法

```C
int _flushall( void );
```

## <a name="return-value"></a>返回值

**_flushall**返回打开的流数（输入和输出）。 无错误返回。

## <a name="remarks"></a>备注

默认情况下 **，_flushall**函数将与打开的输出流关联的所有缓冲区的内容写入相应的文件。 与打开的输入流关联的所有缓冲区的当前内容将被清除。 （这些缓冲区通常由操作系统维护，操作系统确定将数据自动写入磁盘的最佳时间：当缓冲区已满时、当流已关闭时或当程序在未关闭流的情况下正常终止时。）

如果读取跟随调用 **_flushall，** 则从输入文件中读取新数据到缓冲区中。 调用 **_flushall**后，所有流保持打开状态。

利用运行库的提交到磁盘功能，您可以确保将关键数据直接写入磁盘而不是操作系统的缓冲区。 无需重写现有程序，您可以通过将程序的对象文件与 Commode.obj 链接来启用此功能。在生成的可执行文件中，调用 **_flushall**将所有缓冲区的内容写入磁盘。 只有 **_flushall**和[fflush](fflush.md)受Commode.obj的影响。

有关控制提交到磁盘功能的信息，请参阅[流 I/O](../../c-runtime-library/stream-i-o.md)、[fopen](fopen-wfopen.md) 和 [_fdopen](fdopen-wfdopen.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_flushall**|\<stdio.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_flushall.c
// This program uses _flushall
// to flush all open buffers.

#include <stdio.h>

int main( void )
{
   int numflushed;

   numflushed = _flushall();
   printf( "There were %d streams flushed\n", numflushed );
}
```

```Output
There were 3 streams flushed
```

## <a name="see-also"></a>另请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_commit](commit.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[setvbuf](setvbuf.md)<br/>
