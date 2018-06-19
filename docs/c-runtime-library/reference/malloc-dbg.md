---
title: _malloc_dbg | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _malloc_dbg
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
- malloc_dbg
- _malloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- malloc_dbg function
- memory allocation
- _malloc_dbg function
ms.assetid: c97eca51-140b-4461-8bd2-28965b49ecdb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ebc1ff83840631074f04704e6df2a88437b8cc71
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451779"
---
# <a name="mallocdbg"></a>_malloc_dbg

在具有额外空间的堆中为调试标头和覆盖缓冲区分配内存块（仅限调试模式）。

## <a name="syntax"></a>语法

```C
void *_malloc_dbg(
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>参数

*size*<br/>
内存块的请求大小（以字节为单位）。

*blockType*<br/>
内存块的请求类型： **_CLIENT_BLOCK**或 **_NORMAL_BLOCK**。

*filename*<br/>
指向已请求分配操作的源文件名或**NULL**。

*linenumber*<br/>
请求分配操作所在的源文件中的行数或**NULL**。

*Filename*和*linenumber*参数才可用 **_malloc_dbg**显式调用或[_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)已定义预处理器常量。

## <a name="return-value"></a>返回值

在成功完成，此函数将返回指向分配的内存块的用户部分的指针、 调用新处理程序函数，或返回**NULL**。 有关返回行为的完整说明，请参阅以下“备注”部分。 有关如何使用新处理程序函数的详细信息，请参阅 [malloc](malloc.md) 函数。

## <a name="remarks"></a>备注

**_malloc_dbg**是的调试版本[malloc](malloc.md)函数。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，每次调用 **_malloc_dbg**都会减少到对的调用**malloc**。 同时**malloc**和 **_malloc_dbg**分配基堆中中的内存块，但 **_malloc_dbg**提供几种调试功能： 用户两侧的缓冲区用于测试泄漏，用于跟踪特定分配类型的块类型参数的块部分和*filename*/*linenumber*信息用于确定源的分配请求。

**_malloc_dbg**分配稍多的空间比请求的内存块*大小*。 其他空间将由调试堆管理器用于链接调试内存块，以及提供具有调试标头信息的应用程序和覆盖缓冲区。 分配该块后，使用值 0xCD 填充该块的用户部分，使用值 0xFD 填充每个覆盖缓冲区。

**_malloc_dbg**设置**errno**到**ENOMEM**如果内存分配失败或需的内存量 （包括之前提到过的开销） 超过 **_HEAP_MAXREQ**。 有关此代码及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 有关分配块类型及其使用方式的信息，请参阅[调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。 有关在应用程序的调试版本中调用标准堆函数及其调试版本之间差异的信息，请参阅[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_malloc_dbg**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="example"></a>示例

有关如何使用的示例 **_malloc_dbg**，请参阅[crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1)。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[malloc](malloc.md)<br/>
[_calloc_dbg](calloc-dbg.md)<br/>
[_calloc_dbg](calloc-dbg.md)<br/>
