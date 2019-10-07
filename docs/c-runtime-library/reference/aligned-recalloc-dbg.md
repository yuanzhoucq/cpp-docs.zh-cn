---
title: _aligned_recalloc_dbg
ms.date: 11/04/2016
api_name:
- _aligned_recalloc_dbg
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
- _aligned_recalloc_dbg
- aligned_recalloc_dbg
helpviewer_keywords:
- aligned_recalloc_dbg function
- _aligned_recalloc_dbg function
ms.assetid: 55c3c27e-561c-4d6b-9bf9-1e34cc556e4b
ms.openlocfilehash: f322313557c41c0816fdd3b1e5ec89a50324beda
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944064"
---
# <a name="_aligned_recalloc_dbg"></a>_aligned_recalloc_dbg

更改使用 [_aligned_malloc](aligned-malloc.md) 或 [_aligned_offset_malloc](aligned-offset-malloc.md) 分配的内存块的大小，并将该内存初始化为 0（仅限调试版本）。

## <a name="syntax"></a>语法

```C
void * _aligned_recalloc_dbg(
   void * memblock,
   size_t num,
   size_t size,
   size_t alignment,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>参数

*memblock*<br/>
当前的内存块指针。

*number*<br/>
元素数量。

*size*<br/>
每个元素的大小（以字节为单位）。

*alignment*<br/>
对齐值，必须是 2 的整数次幂。

*filename*<br/>
指向已请求分配操作的源文件名的指针或**NULL**。

*linenumber*<br/>
请求分配操作所在的源文件中的行号或**NULL**。

## <a name="return-value"></a>返回值

**_aligned_recalloc_dbg**返回指向重新分配的（并且可能已移动的）内存块的 void 指针。 如果大小为零且缓冲区参数不为**null**，则返回值为 null; 否则，如果没有足够的可用内存来将块扩展到给定大小，则返回值为**null** 。 在第一种情况下，会释放原始块。 在第二种情况下，将不会更改原始块。 返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要获取指向类型而非 void 的指针，请在返回值上使用类型转换。

重新分配内存并更改块对齐是错误的。

## <a name="remarks"></a>备注

**_aligned_recalloc_dbg**是[_aligned_recalloc](aligned-recalloc.md)函数的调试版本。 未定义[_debug](../../c-runtime-library/debug.md)时，对 **_aligned_recalloc_dbg**的每次调用都会减少到对 **_aligned_recalloc**的调用。 **_Aligned_recalloc**和 **_aligned_recalloc_dbg**都重新分配基堆中的内存块，但 **_aligned_recalloc_dbg**提供了若干调试功能：要测试的块的用户部分两侧的缓冲区泄漏和*filename*/*linenumber*信息，用于确定分配请求的来源。 使用块类型参数跟踪特定分配类型不是用于对齐分配的受支持调试功能。 对齐分配将显示为 _NORMAL_BLOCK 块类型。

**_aligned_recalloc_dbg**重新分配指定的内存块，其空间小于所请求的大小（*数字* * *大小*），可能大于或小于最初分配的内存块的大小。 其他空间将由调试堆管理器用于链接调试内存块，以及提供具有调试标头信息的应用程序和覆盖缓冲区。 重新分配可能会导致将原始内存块移动到堆中的其他位置，也可能会导致内存块的大小发生更改。 使用值 0xCD 填充该块的用户部分，使用值 0xFD 填充覆盖缓冲区。

如果内存分配失败，则 **_aligned_recalloc_dbg**将**Errno**设置为**ENOMEM** ;如果所需的内存量（包括前面提到的开销）超过 **_HEAP_MAXREQ**，则返回**EINVAL** 。 有关此代码及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

此外， **_aligned_recalloc_dbg**还会验证其参数。 如果*对齐*不是2的幂，则此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数将返回**NULL** ，并将**Errno**设置为**EINVAL**。

有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 有关分配块类型及其使用方式的信息，请参阅[调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。 有关在应用程序的调试版本中调用标准堆函数及其调试版本之间差异的信息，请参阅[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_aligned_recalloc_dbg**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
