---
title: _free_dbg | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _free_dbg
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
- _free_dbg
- free_dbg
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, deallocating
- freeing memory
- _free_dbg function
- free_dbg function
ms.assetid: fc5e8299-616d-48a0-b979-e037117278c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa485eea6f0ffda05b0ef33a808d5ec837255514
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="freedbg"></a>_free_dbg

释放堆中的内存块（仅限调试版本）。

## <a name="syntax"></a>语法

```C
void _free_dbg(
   void *userData,
   int blockType
);
```

### <a name="parameters"></a>参数

*userData*到分配的内存块的指针，用以被释放。

*blockType*用于被释放的分配的内存块的类型： **_CLIENT_BLOCK**， **_NORMAL_BLOCK**，或 **_IGNORE_BLOCK**。

## <a name="remarks"></a>备注

**_Free_dbg**技术支持部门的调试版本[免费](free.md)函数。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，每次调用 **_free_dbg**都会减少到对的调用**免费**。 同时**免费**和 **_free_dbg**释放内存块在基堆中，但 **_free_dbg**还包含两个调试功能： 能够保留已释放在堆中的块若要模拟内存不足的情况和用于释放特定分配类型的块类型参数的链接的列表。

**_free_dbg**执行有效性检查在所有指定的文件和块位置上执行释放操作之前。 应用程序不应该提供此信息。 当释放内存块时，调试堆管理器自动检查用户部分两侧的缓冲区的完整性，如果发生覆盖，将发出错误报告。 如果 **_CRTDBG_DELAY_FREE_MEM_DF**位域[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)设置标志，已释放的块填入分配的值 0xDD， **_FREE_BLOCK**块类型，并保留在堆链接列表的内存块。

如果在释放内存，发生错误**errno**从操作系统的特性的失败的信息，以及设置。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 有关分配块类型及其使用方式的信息，请参阅[调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。 有关在应用程序的调试版本中调用标准堆函数及其调试版本之间差异的信息，请参阅[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_free_dbg**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

有关如何使用的示例 **_free_dbg**，请参阅[crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
