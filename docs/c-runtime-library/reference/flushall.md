---
title: _flushall
ms.date: 11/04/2016
api_name:
- _flushall
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
ms.openlocfilehash: dce7412ccc19d4870494851d366c059ff01de16a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957143"
---
# <a name="_flushall"></a>_flushall

刷新所有流；清除所有缓冲区。

## <a name="syntax"></a>语法

```C
int _flushall( void );
```

## <a name="return-value"></a>返回值

**_flushall**返回打开的流（输入和输出）的数量。 无错误返回。

## <a name="remarks"></a>备注

默认情况下， **_flushall**函数会将与打开的输出流关联的所有缓冲区的内容写入相应的文件中。 与打开的输入流关联的所有缓冲区的当前内容将被清除。 （这些缓冲区通常由操作系统维护，操作系统确定将数据自动写入磁盘的最佳时间：当缓冲区已满时、当流已关闭时或当程序在未关闭流的情况下正常终止时。）

如果读取后跟对 **_flushall**的调用，则会将输入文件中的新数据读取到缓冲区中。 调用 **_flushall**后，所有流将保持打开状态。

利用运行库的提交到磁盘功能，您可以确保将关键数据直接写入磁盘而不是操作系统的缓冲区。 无需重写现有程序，可以通过将程序的对象文件与 Commode.obj 链接来启用此功能。在生成的可执行文件中，对 **_flushall**的调用会将所有缓冲区的内容写入磁盘。 只有 **_flushall**和[fflush](fflush.md)受 commode.obj 影响。

有关控制提交到磁盘功能的信息，请参阅[流 I/O](../../c-runtime-library/stream-i-o.md)、[fopen](fopen-wfopen.md) 和 [_fdopen](fdopen-wfdopen.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_flushall**|\<stdio.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_commit](commit.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[setvbuf](setvbuf.md)<br/>
