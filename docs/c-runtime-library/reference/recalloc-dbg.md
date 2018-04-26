---
title: _recalloc_dbg | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _recalloc_dbg
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
- recalloc_dbg
- _recalloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- _recalloc_dbg function
- recalloc_dbg function
ms.assetid: 43c3e9b2-be6d-4508-9b0f-3220c8a47ca3
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 78246b18a5706d5f69990c01bac473587be5c62a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="recallocdbg"></a>_recalloc_dbg

重新分配数组并将其元素初始化为 0（仅限调试版本）。

## <a name="syntax"></a>语法

```C
void *_recalloc_dbg(
   void *userData,
   size_t num,
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>参数

*UserData*<br/>
指向之前分配的内存块的指针。

*数*<br/>
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

*Filename*和*linenumber*参数才可用 **_recalloc_dbg**显式调用或[_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)已定义预处理器常量。

## <a name="return-value"></a>返回值

成功完成时，此函数将返回指向重新分配的内存块的用户部分的指针、调用新处理程序函数，或者返回 NULL。 有关返回行为的完整说明，请参阅以下“备注”部分。 有关如何使用新处理程序函数的详细信息，请参阅 [_recalloc](recalloc.md) 函数。

## <a name="remarks"></a>备注

**_recalloc_dbg**是的调试版本[_recalloc](recalloc.md)函数。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，每次调用 **_recalloc_dbg**都会减少到对的调用 **_recalloc**。 同时 **_recalloc**和 **_recalloc_dbg**都可重新分配基堆中中的内存块，但 **_recalloc_dbg**还包含几种调试功能： 两侧的缓冲区块的用于测试泄漏的块的用户部分中，键入用于跟踪特定分配类型参数和*filename*/*linenumber*的信息来确定源的分配请求。

**_recalloc_dbg**重新分配指定的内存块与稍多的空间比请求的大小 (*数* * *大小*) 可能大于或小于的大小最初分配的内存块。 其他空间将由调试堆管理器用于链接调试内存块，以及提供具有调试标头信息的应用程序和覆盖缓冲区。 重新分配可能会导致将原始内存块移动到堆中的其他位置，也可能会导致内存块的大小发生更改。 使用值 0xCD 填充该块的用户部分，使用值 0xFD 填充每个覆盖缓冲区。

**_recalloc_dbg**设置**errno**到**ENOMEM**如果内存分配失败;**EINVAL**如果 （包括之前提到过的开销） 所需的内存量超过返回 **_HEAP_MAXREQ**。 有关此代码及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 有关在应用程序的调试版本中调用标准堆函数及其调试版本之间差异的信息，请参阅[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_recalloc_dbg**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
