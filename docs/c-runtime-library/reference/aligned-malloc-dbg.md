---
title: _aligned_malloc_dbg
ms.date: 11/04/2016
api_name:
- _aligned_malloc_dbg
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
- _aligned_malloc_dbg
- aligned_malloc_dbg
helpviewer_keywords:
- aligned_malloc_dbg function
- _aligned_malloc_dbg function
ms.assetid: fb0429c3-685d-4826-9075-2515c5bdc5c6
ms.openlocfilehash: 3db61d494ea94c9ccbf2844c9f47df66dad87ff7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939885"
---
# <a name="_aligned_malloc_dbg"></a>_aligned_malloc_dbg

在指定内存边界上为调试标头和覆盖缓冲区分配内存（仅限调试模式）。

## <a name="syntax"></a>语法

```C
void * _aligned_malloc_dbg(
    size_t size,
    size_t alignment,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>参数

*size*<br/>
请求的内存分配的大小。

*alignment*<br/>
对齐值，必须是 2 的整数次幂。

*filename*<br/>
指向已请求分配操作的源文件名的指针或 NULL。

*linenumber*<br/>
请求分配操作所在的源文件中的行数或 NULL。

## <a name="return-value"></a>返回值

指向分配的内存块的指针; 如果操作失败，则为 NULL。

## <a name="remarks"></a>备注

**_aligned_malloc_dbg**是[_aligned_malloc](aligned-malloc.md)函数的调试版本。 未定义[_debug](../../c-runtime-library/debug.md)时，对 **_aligned_malloc_dbg** `_aligned_malloc`的每次调用都会减少到对的调用。 和 _aligned_malloc_dbg 在基堆中分配内存块，但 **_aligned_malloc_dbg**提供若干调试功能：块的用户部分两侧的缓冲区，用于测试泄漏和文件名 `_aligned_malloc`用于确定分配请求的源的 linenumber 信息。 / 使用块类型参数跟踪特定分配类型不是用于对齐分配的受支持调试功能。 对齐分配将显示为 _NORMAL_BLOCK 块类型。

**_aligned_malloc_dbg**分配的内存块的空间稍微大于所请求的*大小*。 其他空间将由调试堆管理器用于链接调试内存块，以及提供具有调试标头信息的应用程序和覆盖缓冲区。 分配该块后，使用值 0xCD 填充该块的用户部分，使用值 0xFD 填充每个覆盖缓冲区。

如果内存`errno`分配`ENOMEM`失败或所需的内存量（包括前面提到的开销）超过`_HEAP_MAXREQ`，则将设置为 **_aligned_malloc_dbg** 。 有关此代码及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外， **_aligned_malloc_dbg**还会验证其参数。 如果*对齐*不是2的幂或*大小*为零，则此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数将返回 NULL，并`errno`将`EINVAL`设置为。

有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 有关分配块类型及其使用方式的信息，请参阅[调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。 有关在应用程序的调试版本中调用标准堆函数及其调试版本之间差异的信息，请参阅[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_aligned_malloc_dbg**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)