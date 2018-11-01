---
title: _aligned_msize_dbg
ms.date: 11/04/2016
apiname:
- _aligned_msize_dbg
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
- _aligned_msize_dbg
helpviewer_keywords:
- _aligned_msize_dbg
ms.assetid: f1c44af0-3f66-4033-81d1-d71d3afecba0
ms.openlocfilehash: 054f7b88f93eef37a9a88fbb7895452f7c158716
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451293"
---
# <a name="alignedmsizedbg"></a>_aligned_msize_dbg

返回在堆中分配的内存块的大小（仅限调试版本）。

## <a name="syntax"></a>语法

```C
size_t _aligned_msize_dbg(
   void *memblock,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>参数

*memblock*<br/>
指向内存块的指针。

*对齐方式*<br/>
对齐值，必须是 2 的整数次幂。

*offset*<br/>
用于强制对齐的内存分配中的偏移量。

## <a name="return-value"></a>返回值

返回无符号整数形式的大小（以字节为单位）。

## <a name="remarks"></a>备注

*对齐*并*偏移量*值必须与传递给分配该块的函数的值相同。

**_aligned_msize_dbg**是调试版[_aligned_msize](aligned-msize.md)函数。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，则每次调用 **_aligned_msize_dbg**缩减为调用 **_aligned_msize**。 这两 **_aligned_msize**并 **_aligned_msize_dbg**计算基堆中的内存块的大小，但 **_aligned_msize_dbg**添加了一种调试功能： 它包括在返回大小阻止内存的用户部分两侧的缓冲区。

此函数验证其参数。 如果*memblock*是空指针或*对齐*不是 2 的幂 **_msize**中所述将调用无效参数处理程序，[参数验证](../../c-runtime-library/parameter-validation.md). 如果处理了错误，该函数将设置**errno**到**EINVAL**并返回-1。

有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 有关分配块类型及其使用方式的信息，请参阅[调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。 有关在应用程序的调试版本中调用标准堆函数及其调试版本之间差异的信息，请参阅[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_aligned_msize_dbg**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="see-also"></a>请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
