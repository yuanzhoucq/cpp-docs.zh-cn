---
title: _calloc_dbg
ms.date: 11/04/2016
apiname:
- _calloc_dbg
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
apitype: DLLExport
f1_keywords:
- _calloc_dbg
- calloc_dbg
helpviewer_keywords:
- _calloc_dbg function
- calloc_dbg function
ms.assetid: 7f62c42b-eb9f-4de5-87d0-df57036c87de
ms.openlocfilehash: c525aa2f19b39ba3cb8304c59c96196707ad859c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454387"
---
# <a name="callocdbg"></a>_calloc_dbg

在具有额外空间的堆中为调试标头和覆盖缓冲区分配大量内存块（仅限调试版本）。

## <a name="syntax"></a>语法

```C
void *_calloc_dbg(
   size_t num,
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>参数

*数量*<br/>
内存块的请求数量。

*size*<br/>
每个内存块的请求大小（以字节为单位）。

*blockType*<br/>
内存块的请求类型： **_CLIENT_BLOCK**或 **_NORMAL_BLOCK**。

有关分配块类型及其使用方式的信息，请参阅[调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。

*filename*<br/>
指向已请求分配操作的源文件名或**NULL**。

*linenumber*<br/>
请求分配操作所在的源文件中的行数或**NULL**。

*文件名*并*linenumber*参数才可用 **_calloc_dbg**已显式调用或[_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)预处理器常量已定义。

## <a name="return-value"></a>返回值

成功完成后，此函数将返回指向最后一个已分配的内存块用户部分的指针、 调用新处理程序函数，或返回**NULL**。 有关返回行为的完整说明，请参阅“备注”部分。 有关如何使用新处理程序函数的详细信息，请参阅 [calloc](calloc.md) 函数。

## <a name="remarks"></a>备注

**_calloc_dbg**是调试版[calloc](calloc.md)函数。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，则每次调用 **_calloc_dbg**缩减为调用**calloc**。 这两**calloc**并 **_calloc_dbg**分配*数*基堆中的内存块，但 **_calloc_dbg**提供了多个调试功能：

- 用于测试泄漏的块的用户部分两侧的缓冲区。

- 用于跟踪特定分配类型的块类型参数。

- *文件名*/*linenumber*信息用于确定分配请求的源。

**_calloc_dbg**分配稍多的空间比请求与每个内存块*大小*。 其他空间将由调试堆管理器用于链接调试内存块，以及提供具有调试标头信息的应用程序和覆盖缓冲区。 分配该块后，使用值 0xCD 填充该块的用户部分，使用值 0xFD 填充每个覆盖缓冲区。

**_calloc_dbg**设置**errno**到**ENOMEM**如果内存分配失败;**EINVAL**返回如果 （包括之前提到过的开销） 所需的内存量超出 **_HEAP_MAXREQ**。 有关此代码及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 有关在应用程序的调试版本中调用标准堆函数与调试版本之间的差异的信息，请参阅[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_calloc_dbg**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_callocd.c
// This program uses _calloc_dbg to allocate space for
// 40 long integers. It initializes each element to zero.

#include <stdio.h>
#include <malloc.h>
#include <crtdbg.h>

int main( void )
{
    long *bufferN, *bufferC;

    // Call _calloc_dbg to include the filename and line number
    // of our allocation request in the header and also so we can
    // allocate CLIENT type blocks specifically
    bufferN = (long *)_calloc_dbg( 40, sizeof(long), _NORMAL_BLOCK, __FILE__, __LINE__ );
    bufferC = (long *)_calloc_dbg( 40, sizeof(long), _CLIENT_BLOCK, __FILE__, __LINE__ );
    if( bufferN != NULL && bufferC != NULL )
        printf( "Allocated memory successfully\n" );
    else
        printf( "Problem allocating memory\n" );

    / _free_dbg must be called to free CLIENT type blocks
    free( bufferN );
    _free_dbg( bufferC, _CLIENT_BLOCK );
}
```

```Output
Allocated memory successfully
```

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[calloc](calloc.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
