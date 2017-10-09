---
title: "_aligned_free_dbg | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs:
- C++
helpviewer_keywords:
- _aligned_free_dbg function
- aligned_free_dbg function
ms.assetid: eb0cb3c8-0992-4db8-bac3-65f1b8311ca6
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 724acaed1c99aa2507c33010e97f3f993e1b6de6
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="alignedfreedbg"></a>_aligned_free_dbg
释放使用 [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块（仅限调试）。  
  
## <a name="syntax"></a>语法  
  
```  
void _aligned_free_dbg(  
   void *memblock  
);  
```  
  
#### <a name="parameters"></a>参数  
 `memblock`  
 指向返回到 `_aligned_malloc` 或 `_aligned_offset_malloc` 函数的内存块的指针。  
  
## <a name="remarks"></a>备注  
 `_aligned_free_dbg` 函数是 [_aligned_free](../../c-runtime-library/reference/aligned-free.md) 函数的调试版本。 未定义 [_DEBUG](../../c-runtime-library/debug.md) 时，每个对 `_aligned_free_dbg` 的调用都会减少到对 `_aligned_free` 的调用。 同时`_aligned_free`和`_aligned_free_dbg`释放内存块在基堆中，但`_aligned_free_dbg`还包含一种调试功能： 能够保留已释放在堆链接列表，以便模拟内存不足的情况中块。  
  
 在执行释放操作之前，`_aligned_free_dbg` 将在所有指定的文件和块位置上执行有效性检查。 应用程序不应该提供此信息。 当释放内存块时，调试堆管理器自动检查用户部分两侧的缓冲区的完整性，如果发生覆盖，将发出错误报告。 如果设置了 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) 标志的 `_CRTDBG_DELAY_FREE_MEM_DF` 位域，则将使用值 0xDD 填充释放的块、为其分配 `_FREE_BLOCK` 块类型，以及将其保留在内存块的堆链接列表中。  
  
 如果在释放内存时发生错误，则根据操作系统中关于错误性质的信息设置 `errno`。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。 有关分配块类型及其使用方式的信息，请参阅[调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。 有关在应用程序的调试版本中调用标准堆函数及其调试版本之间差异的信息，请参阅[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_aligned_free_dbg`|\<crtdbg.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>另请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)
