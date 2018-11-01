---
title: _realloc_dbg
ms.date: 11/04/2016
apiname:
- _realloc_dbg
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
- _realloc_dbg
- realloc_dbg
helpviewer_keywords:
- reallocating memory blocks
- realloc_dbg function
- memory blocks, reallocating
- memory, reallocating
- _realloc_dbg function
ms.assetid: 7c3cb780-51ed-4d9c-9929-cdde606d846a
ms.openlocfilehash: 9b30dfd6fbae9a4831ff53e7896aeb995657da03
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640279"
---
# <a name="reallocdbg"></a>_realloc_dbg

通过移动和/或调整块的大小重新分配一个指定堆上的内存块（仅限调试版本）。

## <a name="syntax"></a>语法

```C
void *_realloc_dbg(
   void *userData,
   size_t newSize,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>参数

*userData*<br/>
指向之前分配的内存块的指针。

*newSize*<br/>
重新分配块的请求大小（字节）。

*blockType*<br/>
重新分配块的请求类型： **_CLIENT_BLOCK**或 **_NORMAL_BLOCK**。

*filename*<br/>
指向已请求的源文件名**realloc**操作或**NULL**。

*linenumber*<br/>
源文件中的行数其中**realloc**请求操作或**NULL**。

*文件名*并*linenumber*参数才可用 **_realloc_dbg**已显式调用或[_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)已定义预处理器常量。

## <a name="return-value"></a>返回值

成功完成后，此函数返回指向重新分配的内存块用户部分的指针、 调用新处理程序函数，或返回**NULL**。 有关返回行为的完整说明，请参阅以下“备注”部分。 有关如何使用新处理程序函数的详细信息，请参阅 [realloc](realloc.md) 函数。

## <a name="remarks"></a>备注

**_realloc_dbg**是调试版[realloc](realloc.md)函数。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，则每次调用 **_realloc_dbg**缩减为调用**realloc**。 这两**realloc**并 **_realloc_dbg**重新分配基堆中的内存块，但 **_realloc_dbg**还包含几种调试功能： 两侧的缓冲区用于测试泄漏，用于跟踪特定分配类型的块类型参数的块用户部分和*文件名*/*linenumber*的信息来确定的来源分配请求。

**_realloc_dbg**重新分配与稍多的空间比请求指定的内存块*newSize*。 *newSize*可能会大于或小于最初分配的内存块的大小。 其他空间将由调试堆管理器用于链接调试内存块，以及提供具有调试标头信息的应用程序和覆盖缓冲区。 重新分配可能会导致将原始内存块移动到堆中的其他位置，也可能会导致内存块的大小发生更改。 如果移动内存块，将覆盖原始块中的内容。

**_realloc_dbg**设置**errno**到**ENOMEM**如果内存分配失败或 （包括之前提到过的开销） 所需的内存量超过 **_HEAP_MAXREQ**。 有关此代码及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 有关分配块类型及其使用方式的信息，请参阅[调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。 有关在应用程序的调试版本中调用标准堆函数及其调试版本之间差异的信息，请参阅[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_realloc_dbg**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="example"></a>示例

请参阅 [_msize_dbg](msize-dbg.md) 主题中的示例。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
