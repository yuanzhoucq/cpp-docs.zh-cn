---
title: "_aligned_offset_recalloc_dbg | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _aligned_offset_recalloc_dbg
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
- aligned_offset_recalloc_dbg
- _aligned_offset_recalloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- aligned_offset_recalloc_dbg function
- _aligned_offset_recalloc_dbg function
ms.assetid: 7ab719c3-77e0-4d2e-934f-01529d062fbf
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 7c65c73075c282f3a1b0dac83692c0adfe527c58
ms.contentlocale: zh-cn
ms.lasthandoff: 04/04/2017

---
# <a name="alignedoffsetrecallocdbg"></a>_aligned_offset_recalloc_dbg
更改使用 [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小，并将该内存初始化为 0（仅限调试版本）。  
  
## <a name="syntax"></a>语法  
  
```  
void * _aligned_offset_recalloc_dbg(  
   void *memblock,   
   size_t num,   
   size_t size,   
   size_t alignment,  
   size_t offset,  
   const char *filename,  
   int linenumber  
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `memblock`  
 当前的内存块指针。  
  
 [in] `num`  
 元素数量。  
  
 [in] `size`  
 每个元素的长度（以字节为单位）。  
  
 [in] `alignment`  
 对齐值，必须是 2 的整数次幂。  
  
 [in] `offset`  
 用于强制对齐的内存分配中的偏移量。  
  
 [in] `filename`  
 指向已请求 `realloc` 操作的源文件名的指针或 NULL。  
  
 [in] `linenumber`  
 请求 `realloc` 操作所在的源文件中的行数或 NULL。  
  
## <a name="return-value"></a>返回值  
 `_aligned_offset_recalloc_dbg` 将返回指向重新分配的（并且可能已移动的）内存块的 void 指针。 如果大小为零且缓冲区参数不为 `NULL`，或内存不足以将块展开到给定的大小，则返回值为 `NULL`。 在第一种情况下，会释放原始块。 在第二种情况下，将不会更改原始块。 返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要获取指向类型而非 void 的指针，请在返回值上使用类型转换。  
  
## <a name="remarks"></a>备注  
 `_aligned_offset_realloc_dbg` 是 [_aligned_offset_recalloc](../../c-runtime-library/reference/aligned-offset-recalloc.md) 函数的调试版本。 未定义 [_DEBUG](../../c-runtime-library/debug.md) 时，每个对 `_aligned_offset_recalloc_dbg` 的调用都会减少到对 `_aligned_offset_recalloc` 的调用。 `_aligned_offset_recalloc` 和 `_aligned_offset_recalloc_dbg` 都可重新分配基堆中的内存块，但是 `_aligned_offset_recalloc_dbg` 还包含几种调试功能：用于测试泄漏的块的用户部分两侧的缓冲区、用于跟踪特定分配类型的块类型参数，以及用于确定分配请求的源的 `filename`/`linenumber` 信息。  
  
 `_aligned_offset_realloc_dbg` 将使用比请求的 `newSize` 稍多的空间重新分配指定的内存块。 `newSize` 可能会大于或小于最初分配的内存块的大小。 其他空间将由调试堆管理器用于链接调试内存块，以及提供具有调试标头信息的应用程序和覆盖缓冲区。 重新分配可能会导致将原始内存块移动到堆中的其他位置，也可能会导致内存块的大小发生更改。 如果移动内存块，将覆盖原始块中的内容。  
  
 如果内存分配失败或请求的大小 (`num` * `size`) 大于 `_HEAP_MAXREQ`，则此函数会将 `errno` 设置为 `ENOMEM`。 有关 `errno` 的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外，`_aligned_offset_recalloc_dbg` 将验证其参数。 如果 `alignment` 不是 2 的幂或 `offset` 大于或等于请求的大小且非零，则此函数调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数将返回 `NULL` 并将 `errno` 设置为 `EINVAL`。  
  
 有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。 有关分配块类型及其使用方式的信息，请参阅[调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。 有关在应用程序的调试版本中调用标准堆函数及其调试版本之间差异的信息，请参阅[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_aligned_offset_recalloc_dbg`|\<malloc.h>|  
  
## <a name="see-also"></a>另请参阅  
 [数据对齐](../../c-runtime-library/data-alignment.md)
