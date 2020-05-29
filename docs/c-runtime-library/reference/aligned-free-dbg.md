---
title: _aligned_free_dbg
ms.date: 11/04/2016
api_name:
- _aligned_free_dbg
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
- _aligned_free_dbg
- aligned_free_dbg
helpviewer_keywords:
- _aligned_free_dbg function
- aligned_free_dbg function
ms.assetid: eb0cb3c8-0992-4db8-bac3-65f1b8311ca6
ms.openlocfilehash: 18c1a23d666070afaf1eff687c7d33b0240f0ac3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171276"
---
# <a name="_aligned_free_dbg"></a>_aligned_free_dbg

释放使用 [_aligned_malloc](aligned-malloc.md) 或 [_aligned_offset_malloc](aligned-offset-malloc.md) 分配的内存块（仅限调试）。

## <a name="syntax"></a>语法

```C
void _aligned_free_dbg(
   void *memblock
);
```

### <a name="parameters"></a>parameters

*memblock*<br/>
指向[_aligned_malloc](aligned-malloc.md)或[_aligned_offset_malloc](aligned-offset-malloc.md)函数返回的内存块的指针。

## <a name="remarks"></a>备注

**_Aligned_free_dbg**函数是[_aligned_free](aligned-free.md)函数的调试版本。 未定义[_DEBUG](../../c-runtime-library/debug.md)时，对 **_aligned_free_dbg**的每次调用都会减少到对 `_aligned_free`的调用。 `_aligned_free` 和 **_aligned_free_dbg**可在基堆中释放内存块，但 **_aligned_free_dbg**可容纳调试功能：能够在堆的链接列表中保留已释放的块，以便模拟内存不足的情况。

**_aligned_free_dbg**在执行免费操作之前在所有指定的文件和块位置上执行有效性检查。 应用程序不应该提供此信息。 当释放内存块时，调试堆管理器自动检查用户部分两侧的缓冲区的完整性，如果发生覆盖，将发出错误报告。 如果设置了[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)标志的 _CRTDBG_DELAY_FREE_MEM_DF 位字段，则会用值0xDD 填充已释放的块，并为其分配了 _FREE_BLOCK 块类型，并将其保留在堆的链接内存块列表中。

如果在释放内存时发生错误，则根据操作系统中关于错误性质的信息设置 `errno`。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。 有关分配块类型及其使用方式的信息，请参阅[调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。 有关在应用程序的调试版本中调用标准堆函数及其调试版本之间差异的信息，请参阅[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_aligned_free_dbg**|\<crtdbg.h>|

有关兼容性的详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[调试例程](../../c-runtime-library/debug-routines.md)
