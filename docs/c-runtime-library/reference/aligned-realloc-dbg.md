---
title: _aligned_realloc_dbg | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _aligned_realloc_dbg
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
- aligned_realloc_dbg
- _aligned_realloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- _aligned_realloc_dbg function
- aligned_realloc_dbg function
ms.assetid: 8aede920-991e-44cd-867f-83dc2165db47
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1fd5854bc18cecda1fd3ffee4f28ec2fa5d2a68a
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/22/2018
---
# <a name="alignedreallocdbg"></a>_aligned_realloc_dbg

更改使用 [_aligned_malloc](aligned-malloc.md) 或 [_aligned_offset_malloc](aligned-offset-malloc.md) 分配的内存块的大小（仅限调试版本）。

## <a name="syntax"></a>语法

```C
void * _aligned_realloc_dbg(
   void *memblock,
   size_t size,
   size_t alignment,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>参数

*memblock*<br/>
当前的内存块指针。

*size*<br/>
请求的内存分配的大小。

*对齐方式*<br/>
对齐值，必须是 2 的整数次幂。

*filename*<br/>
指向已请求的源文件名**realloc**操作或**NULL**。

*linenumber*<br/>
源文件中的行数其中**realloc**请求操作或**NULL**。

## <a name="return-value"></a>返回值

**_aligned_realloc_dbg**返回指向重新分配的 （并且可能已移动的） 内存块的 void 指针。 返回值是**NULL**如果大小为零且缓冲区自变量不**NULL**，或如果没有内存不足以将块展开到给定的大小。 在第一种情况下，会释放原始块。 在第二种情况下，将不会更改原始块。 返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要获取指向类型而非 void 的指针，请在返回值上使用类型转换。

重新分配内存并更改块对齐是错误的。

## <a name="remarks"></a>备注

**_aligned_realloc_dbg**是的调试版本[_aligned_realloc](aligned-realloc.md)函数。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，每次调用 **_aligned_realloc_dbg**都会减少到对的调用 **_aligned_realloc**。 同时 **_aligned_realloc**和 **_aligned_realloc_dbg**都可重新分配基堆中中的内存块，但 **_aligned_realloc_dbg**还包含几种调试功能： 用于测试泄漏，用于跟踪特定分配类型的块类型参数的块的用户部分两侧的缓冲区和*filename*/*linenumber*用于确定分配请求的源的信息。

**_aligned_realloc_dbg**重新分配指定的内存块具有比请求的略有更多空间*newSize*。 *newSize*可能会大于或小于最初分配的内存块的大小。 其他空间将由调试堆管理器用于链接调试内存块，以及提供具有调试标头信息的应用程序和覆盖缓冲区。 重新分配可能会导致将原始内存块移动到堆中的其他位置，也可能会导致内存块的大小发生更改。 如果移动内存块，将覆盖原始块中的内容。

**_aligned_realloc_dbg**设置**errno**到**ENOMEM**如果内存分配失败或需的内存量 （包括之前提到过的开销） 超过 **_HEAP_MAXREQ**。 有关此代码及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

此外， **_aligned_realloc_dbg**验证其参数。 如果*对齐*不是为 2，此函数将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则此函数将返回**NULL**和设置**errno**到**EINVAL**。

有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 有关分配块类型及其使用方式的信息，请参阅[调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。 有关在应用程序的调试版本中调用标准堆函数及其调试版本之间差异的信息，请参阅[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_aligned_realloc_dbg**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
