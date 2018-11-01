---
title: _expand_dbg
ms.date: 11/04/2016
apiname:
- _expand_dbg
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
- expand_dbg
- _expand_dbg
helpviewer_keywords:
- memory blocks, changing size
- expand_dbg function
- _expand_dbg function
ms.assetid: dc58c91f-72a8-48c6-b643-fe130fb6c1fd
ms.openlocfilehash: cc3aa2b7e39b52eb71ac10a9b5c4a221ba6fb70c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663796"
---
# <a name="expanddbg"></a>_expand_dbg

通过展开或收缩块调整指定堆的内存块大小（仅限调试版本）。

## <a name="syntax"></a>语法

```C
void *_expand_dbg(
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
请求块的新大小（以字节为单位）。

*blockType*<br/>
请求的调整大小的块类型： **_CLIENT_BLOCK**或 **_NORMAL_BLOCK**。

*filename*<br/>
指向已请求的源文件名展开操作或**NULL**。

*linenumber*<br/>
请求扩展操作所在的源文件中的行数或**NULL**。

*文件名*并*linenumber*参数才可用 **_expand_dbg**已显式调用或[_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)预处理器常量已定义。

## <a name="return-value"></a>返回值

成功完成后， **_expand_dbg**返回指向已调整大小的内存块的指针。 因为内存未移动，所以地址与 userData 相同。 如果出现错误或块无法扩展到所请求的大小，则返回**NULL**。 如果失败，则**errno**是性质的信息从操作系统故障的使用。 有关详细信息**errno**，请参阅[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Expand_dbg**函数是 _ 的调试版本[展开](expand.md)函数。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，则每次调用 **_expand_dbg**缩减为调用 **_expand**。 这两 **_expand**并 **_expand_dbg**调整基堆中的内存块的大小，但 **_expand_dbg**还包含几种调试功能： 用户两侧的缓冲区用于测试泄漏，用于跟踪特定分配类型的块类型参数的块部分和*文件名*/*linenumber*的信息来确定的来源分配请求。

**_expand_dbg**调整稍多的空间比请求与指定的内存块的大小*newSize*。 *newSize*可能会大于或小于最初分配的内存块的大小。 其他空间将由调试堆管理器用于链接调试内存块，以及提供具有调试标头信息的应用程序和覆盖缓冲区。 通过扩展或收缩原始内存块完成调整大小。 **_expand_dbg**不会移动内存块，如同[_realloc_dbg](realloc-dbg.md)函数。

当*newSize*大于原始块大小，内存块已展开。 扩展期间，如果内存块无法扩展以容纳所请求的大小， **NULL**返回。 当*newSize*小于原始块大小，内存块进行收缩，直至获取新的大小。

有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 有关分配块类型及其使用方式的信息，请参阅[调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。 有关在应用程序的调试版本中调用标准堆函数及其调试版本之间差异的信息，请参阅[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

此函数验证其参数。 如果*memblock*是空指针，或如果大小大于 **_HEAP_MAXREQ**，此函数将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则**errno**设置为**EINVAL**并且该函数返回**NULL**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_expand_dbg**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="example"></a>示例

```C
// crt_expand_dbg.c
//
// This program allocates a block of memory using _malloc_dbg
// and then calls _msize_dbg to display the size of that block.
// Next, it uses _expand_dbg to expand the amount of
// memory used by the buffer and then calls _msize_dbg again to
// display the new amount of memory allocated to the buffer.
//

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>
#include <crtdbg.h>

int main( void )
{
   long *buffer;
   size_t size;

   // Call _malloc_dbg to include the filename and line number
   // of our allocation request in the header
   buffer = (long *)_malloc_dbg( 40 * sizeof(long),
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );
   if( buffer == NULL )
      exit( 1 );

   // Get the size of the buffer by calling _msize_dbg
   size = _msize_dbg( buffer, _NORMAL_BLOCK );
   printf( "Size of block after _malloc_dbg of 40 longs: %u\n", size );

   // Expand the buffer using _expand_dbg and show the new size
   buffer = (long *)_expand_dbg( buffer, size + sizeof(long),
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );

   if( buffer == NULL )
      exit( 1 );
   size = _msize_dbg( buffer, _NORMAL_BLOCK );
   printf( "Size of block after _expand_dbg of 1 more long: %u\n",
           size );

   free( buffer );
   exit( 0 );
}
```

```Output
Size of block after _malloc_dbg of 40 longs: 160
Size of block after _expand_dbg of 1 more long: 164
```

## <a name="comment"></a>注释

此程序的输出取决于你的计算机扩展所有部分的能力。 如果对所有部分都进行了扩展，则会在输出部分反映该输出。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
