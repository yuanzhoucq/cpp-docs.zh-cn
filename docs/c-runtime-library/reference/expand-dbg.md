---
title: _expand_dbg
ms.date: 11/04/2016
api_name:
- _expand_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- expand_dbg
- _expand_dbg
helpviewer_keywords:
- memory blocks, changing size
- expand_dbg function
- _expand_dbg function
ms.assetid: dc58c91f-72a8-48c6-b643-fe130fb6c1fd
ms.openlocfilehash: 836b9cffcf0367f248a14469b30c1a355e2bdec2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941581"
---
# <a name="_expand_dbg"></a>_expand_dbg

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
已调整大小的块的请求类型： **_CLIENT_BLOCK**或 **_NORMAL_BLOCK**。

*filename*<br/>
指向请求展开操作的源文件名的指针或**NULL**。

*linenumber*<br/>
请求展开操作的源文件中的行号或**NULL**。

仅当已显式调用 **_expand_dbg**或已定义[_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)预处理器常量时， *filename*和*linenumber*参数才可用。

## <a name="return-value"></a>返回值

成功完成后， **_expand_dbg**将返回一个指向已调整大小的内存块的指针。 因为内存未移动，所以地址与 userData 相同。 如果发生错误或块无法扩展到所请求的大小，则返回**NULL**。 如果发生失败， **errno**将会出现有关故障性质的操作系统的信息。 有关**errno**的详细信息，请参阅[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Expand_dbg**函数是 _[expand](expand.md)函数的调试版本。 未定义[_debug](../../c-runtime-library/debug.md)时，对 **_expand_dbg**的每次调用都会减少到对 **_expand**的调用。 **_Expand**和 **_expand_dbg**调整了基堆中的内存块的大小，但 **_expand_dbg**提供了若干调试功能：用于测试泄漏的块的用户部分两侧的缓冲区，要跟踪的块类型参数特定分配类型和*文件名*/*linenumber*信息，用于确定分配请求的源。

**_expand_dbg**会将指定的内存块的大小调整为比请求的*newSize*略多的空间。 *newSize*可能大于或小于最初分配的内存块的大小。 其他空间将由调试堆管理器用于链接调试内存块，以及提供具有调试标头信息的应用程序和覆盖缓冲区。 通过扩展或收缩原始内存块完成调整大小。 **_expand_dbg**不会移动内存块，这与[_realloc_dbg](realloc-dbg.md)函数相同。

当*newSize*大于原始块大小时，将扩展内存块。 在展开过程中，如果内存块无法扩展以容纳请求的大小，则返回**NULL** 。 当*newSize*小于原始块大小时，将会收缩内存块，直到获取新大小。

有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 有关分配块类型及其使用方式的信息，请参阅[调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。 有关在应用程序的调试版本中调用标准堆函数及其调试版本之间差异的信息，请参阅[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

此函数验证其参数。 如果*memblock*为 null 指针，或者如果大小大于 **_HEAP_MAXREQ**，此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将**errno**设置为**EINVAL** ，并且该函数将返回**NULL**。

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
