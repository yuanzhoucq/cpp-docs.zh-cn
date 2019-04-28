---
title: _aligned_free_dbg
ms.date: 11/04/2016
apiname:
- _aligned_free_dbg
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
- _aligned_free_dbg
- aligned_free_dbg
helpviewer_keywords:
- _aligned_free_dbg function
- aligned_free_dbg function
ms.assetid: eb0cb3c8-0992-4db8-bac3-65f1b8311ca6
ms.openlocfilehash: f51b9b9573ab2e23a0a60979c55a33d2e5cff747
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341892"
---
# <a name="alignedfreedbg"></a>_aligned_free_dbg

释放使用 [_aligned_malloc](aligned-malloc.md) 或 [_aligned_offset_malloc](aligned-offset-malloc.md) 分配的内存块（仅限调试）。

## <a name="syntax"></a>语法

```C
void _aligned_free_dbg(
   void *memblock
);
```

### <a name="parameters"></a>参数

*memblock*<br/>
返回到的内存块的指针[_aligned_malloc](aligned-malloc.md)或[_aligned_offset_malloc](aligned-offset-malloc.md)函数。

## <a name="remarks"></a>备注

**_Aligned_free_dbg**函数是调试版[_aligned_free](aligned-free.md)函数。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，则每次调用 **_aligned_free_dbg**缩减为调用`_aligned_free`。 这两`_aligned_free`并 **_aligned_free_dbg**释放基堆中的内存块，但 **_aligned_free_dbg**还包含一种调试功能： 能够保留已释放的块中的堆链接列表模拟内存不足的情况。

**_aligned_free_dbg**执行有效性检查所有指定的文件和块位置上执行释放操作之前。 应用程序不应该提供此信息。 当释放内存块时，调试堆管理器自动检查用户部分两侧的缓冲区的完整性，如果发生覆盖，将发出错误报告。 如果 _CRTDBG_DELAY_FREE_MEM_DF 位字段[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)设置标志，则将使用值 0xDD 填充、 分配 _FREE_BLOCK 块类型，并保留在堆链接列表的内存块释放的块。

如果在释放内存时发生错误，则根据操作系统中关于错误性质的信息设置 `errno`。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 有关分配块类型及其使用方式的信息，请参阅[调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。 有关在应用程序的调试版本中调用标准堆函数及其调试版本之间差异的信息，请参阅[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_aligned_free_dbg**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)