---
title: _aligned_offset_realloc_dbg
ms.date: 11/04/2016
apiname:
- _aligned_offset_realloc_dbg
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
- aligned_offset_realloc_dbg
- _aligned_offset_realloc_dbg
helpviewer_keywords:
- aligned_offset_realloc_dbg function
- _aligned_offset_realloc_dbg function
ms.assetid: 64e30a12-887e-453b-aea8-aed793fca9d8
ms.openlocfilehash: 7684a752f489eb726b2105b1055b6da1e86e9cd1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341569"
---
# <a name="alignedoffsetreallocdbg"></a>_aligned_offset_realloc_dbg

更改使用 [_aligned_malloc](aligned-malloc.md) 或 [_aligned_offset_malloc](aligned-offset-malloc.md) 分配的内存块的大小（仅限调试版本）。

## <a name="syntax"></a>语法

```C
void * _aligned_offset_realloc_dbg(
   void *memblock,
   size_t size,
   size_t alignment,
   size_t offset,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>参数

*memblock*<br/>
当前的内存块指针。

*size*<br/>
内存分配的大小。

*alignment*<br/>
对齐值，必须是 2 的整数次幂。

*offset*<br/>
用于强制对齐的内存分配中的偏移量。

*filename*<br/>
指向已请求的源文件名**aligned_offset_realloc**操作或**NULL**。

*linenumber*<br/>
源文件中的行数其中**aligned_offset_realloc**请求操作或**NULL**。

## <a name="return-value"></a>返回值

**_aligned_offset_realloc_dbg**返回指向重新分配的 （并且可能已移动的） 内存块的 void 指针。 返回值是**NULL**如果大小为零且缓冲区参数不是**NULL**，或如果没有足够的可用内存将块扩展到给定大小。 在第一种情况下，会释放原始块。 在第二种情况下，将不会更改原始块。 返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要获取指向类型而非 void 的指针，请在返回值上使用类型转换。

## <a name="remarks"></a>备注

**_aligned_offset_realloc_dbg**是调试版[_aligned_offset_realloc](aligned-offset-realloc.md)函数。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，则每次调用 **_aligned_offset_realloc_dbg**缩减为调用 **_aligned_offset_realloc**。 这两 **_aligned_offset_realloc**并 **_aligned_offset_realloc_dbg**重新分配基堆中的内存块，但 **_aligned_offset_realloc_dbg**可容纳几种调试功能： 用于测试泄漏的块的用户部分两侧的缓冲区并*文件名*/*linenumber*的信息来确定的来源分配请求。 跟踪特定分配类型的块类型参数具有不一致的分配的受支持的调试功能。 一致的分配将显示为 _NORMAL_BLOCK 块类型。

像[_aligned_offset_malloc](aligned-offset-malloc.md)， **_aligned_offset_realloc_dbg**允许在结构内的偏移量上对齐结构。

**_realloc_dbg**重新分配与稍多的空间比请求指定的内存块*newSize*。 *newSize*可能会大于或小于最初分配的内存块的大小。 其他空间将由调试堆管理器用于链接调试内存块，以及提供具有调试标头信息的应用程序和覆盖缓冲区。 重新分配可能会导致将原始内存块移动到堆中的其他位置，也可能会导致内存块的大小发生更改。 如果移动内存块，将覆盖原始块中的内容。

此函数将**errno**到**ENOMEM**如果内存分配失败或请求的大小是大于 **_HEAP_MAXREQ**。 有关详细信息**errno**，请参阅[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外， **_aligned_offset_realloc_dbg**验证其参数。 如果*对齐*不是 2 的幂或如果*偏移量*大于或等于*大小*且非零值，此函数调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，此函数返回**NULL** ，并设置**errno**到**EINVAL**。

有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 有关分配块类型及其使用方式的信息，请参阅[调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。 有关在应用程序的调试版本中调用标准堆函数及其调试版本之间差异的信息，请参阅[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_aligned_offset_realloc_dbg**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
