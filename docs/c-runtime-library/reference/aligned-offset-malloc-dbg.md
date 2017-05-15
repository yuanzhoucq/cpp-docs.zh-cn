---
title: "_aligned_offset_malloc_dbg | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: fb6714506013bcaf9e4d5f6064d7bb98f8e56562
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="alignedoffsetmallocdbg"></a>_aligned_offset_malloc_dbg
在指定对齐边界分配内存（仅限调试版本）。  
  
## <a name="syntax"></a>语法  
  
```  
void * _aligned_offset_malloc_dbg(  
   size_t size,   
   size_t alignment,   
   size_t offset,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `size`  
 请求的内存分配的大小。  
  
 [in] `alignment`  
 对齐值，必须是 2 的整数次幂。  
  
 [in] `offset`  
 用于强制对齐的内存分配中的偏移量。  
  
 [in] `filename`  
 指向已请求分配操作的源文件名的指针或 NULL。  
  
 [in] `linenumber`  
 请求分配操作所在的源文件中的行数或 NULL。  
  
## <a name="return-value"></a>返回值  
 指向已分配的内存块的指针或 `NULL`（如果操作失败）。  
  
## <a name="remarks"></a>备注  
 `_aligned_offset_malloc_dbg` 是 [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 函数的调试版本。 未定义 [_DEBUG](../../c-runtime-library/debug.md) 时，每个对 `_aligned_offset_malloc_dbg` 的调用都会减少到对 `_aligned_offset_malloc` 的调用。 `_aligned_offset_malloc` 和 `_aligned_offset_malloc_dbg` 都可分配基堆中的内存块，但是 `_aligned_offset_malloc_dbg` 还提供几种调试功能：用于测试泄漏的块的用户部分两侧的缓冲区、用于跟踪特定分配类型的块类型参数，以及用于确定分配请求的源的 `filename`/`linenumber` 信息。  
  
 `_aligned_offset_malloc_dbg` 将使用比请求的 `size` 稍多的空间分配内存块。 其他空间将由调试堆管理器用于链接调试内存块，以及提供具有调试标头信息的应用程序和覆盖缓冲区。 分配该块后，使用值 0xCD 填充该块的用户部分，使用值 0xFD 填充每个覆盖缓冲区。  
  
 `_aligned_offset_malloc_dbg` 在需要对嵌套元素进行对齐的情况下很有用；例如，嵌套类需要进行对齐的情况。  
  
 `_aligned_offset_malloc_dbg` 基于 `malloc`；有关详细信息，请参阅 [malloc](../../c-runtime-library/reference/malloc.md)。  
  
 如果内存分配失败或请求的大小大于 `errno`，则此函数会将 `ENOMEM` 设置为 `_HEAP_MAXREQ`。 有关 `errno` 的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外，`_aligned_offset_malloc` 将验证其参数。 如果 `alignment` 不是 2 的幂或 `offset` 大于或等于 `size` 且非零，则此函数调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数将返回 `NULL` 并将 `errno` 设置为 `EINVAL`。  
  
 有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。  
  
 有关分配块类型及其使用方式的信息，请参阅[调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_aligned_offset_malloc_dbg`|\<crtdbg.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## <a name="see-also"></a>另请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)
