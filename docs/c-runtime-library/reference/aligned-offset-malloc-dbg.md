---
title: _aligned_offset_malloc_dbg | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _aligned_offset_malloc_dbg
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
- _aligned_offset_malloc_dbg
- aligned_offset_malloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- _aligned_offset_malloc_dbg function
- aligned_offset_malloc_dbg function
ms.assetid: 6c242307-c59e-4d63-aae5-d8cbec8e021c
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: afb15a5e132d70b40fa3e816f5271a192df5788a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="alignedoffsetmallocdbg"></a>_aligned_offset_malloc_dbg

在指定对齐边界分配内存（仅限调试版本）。

## <a name="syntax"></a>语法

```C
void * _aligned_offset_malloc_dbg(
   size_t size,
   size_t alignment,
   size_t offset,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>参数

*size*<br/>
请求的内存分配的大小。

*对齐方式*<br/>
对齐值，必须是 2 的整数次幂。

*offset*<br/>
用于强制对齐的内存分配中的偏移量。

*filename*<br/>
指向已请求分配操作的源文件名的指针或 NULL。

*linenumber*<br/>
请求分配操作所在的源文件中的行数或 NULL。

## <a name="return-value"></a>返回值

指向已分配的内存块的指针或**NULL**如果操作失败。

## <a name="remarks"></a>备注

**_aligned_offset_malloc_dbg**是的调试版本[_aligned_offset_malloc](aligned-offset-malloc.md)函数。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，每次调用 **_aligned_offset_malloc_dbg**都会减少到对的调用 **_aligned_offset_malloc**。 同时 **_aligned_offset_malloc**和 **_aligned_offset_malloc_dbg**分配基堆中中的内存块，但 **_aligned_offset_malloc_dbg**提供多个调试功能： 用于测试泄漏，用于跟踪特定分配类型的块类型参数的块的用户部分两侧的缓冲区和*filename*/*linenumber*信息用于确定分配请求的源。

**_aligned_offset_malloc_dbg**分配稍多的空间比请求的内存块*大小*。 其他空间将由调试堆管理器用于链接调试内存块，以及提供具有调试标头信息的应用程序和覆盖缓冲区。 分配该块后，使用值 0xCD 填充该块的用户部分，使用值 0xFD 填充每个覆盖缓冲区。

**_aligned_offset_malloc_dbg**在一个嵌套的元素; 需要对齐方式的位置的情况下有用的示例中，如果嵌套类上需要的对齐方式。

**_aligned_offset_malloc_dbg**基于**malloc**; 有关详细信息，请参阅[malloc](malloc.md)。

此函数将**errno**到**ENOMEM**如果内存分配失败或请求的大小大于 **_HEAP_MAXREQ**。 有关详细信息**errno**，请参阅[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外， **_aligned_offset_malloc**验证其参数。 如果*对齐*不是 2 的幂或如果*偏移量*大于或等于*大小*和非零值，此函数将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则此函数将返回**NULL**和设置**errno**到**EINVAL**。

有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

有关分配块类型及其使用方式的信息，请参阅[调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_aligned_offset_malloc_dbg**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
