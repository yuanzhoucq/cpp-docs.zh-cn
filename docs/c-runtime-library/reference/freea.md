---
title: "_freea | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _freea
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
- freea
- _freea
dev_langs:
- C++
helpviewer_keywords:
- _freea function
- freea function
- memory deallocation
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6bf2bd2d3dacba307f529798727e7af745bf7cf9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="freea"></a>_freea
解除分配或释放内存块。  
  
## <a name="syntax"></a>语法  
  
```  
void _freea(   
   void *memblock   
);  
```  
  
#### <a name="parameters"></a>参数  
 `memblock`  
 要释放的以前分配的内存块。  
  
## <a name="return-value"></a>返回值  
 无。  
  
## <a name="remarks"></a>备注  
 `_freea` 函数释放以前通过调用 [_malloca](../../c-runtime-library/reference/malloca.md) 分配的内存块 (`memblock`)。 `_freea` 检查以确定内存被分配到堆上还是堆栈上。 如果被分配到堆栈上，则 `_freea` 不执行任何操作。 如果被分配到堆上，则已释放的字节数等于分配块时请求的字节数。 如果 `memblock` 是 `NULL`，将忽略指针并立即返回 `_freea`。 尝试释放无效指针（指向并非由 `_malloca` 分配的内存块的指针）可能会影响后续分配请求，并导致错误。  
  
 `_freea` 调用`free`内部如果找到，堆上分配内存。 内存是在堆上还是在堆栈上由内存中的标记决定，该内存地址紧接所分配的内存。  
  
 如果在释放内存时发生错误，则根据操作系统中关于错误性质的信息设置 `errno`。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 释放内存块后， [_heapmin](../../c-runtime-library/reference/heapmin.md) 通过合并未使用的区域并将其释放回到操作系统，将堆上的可用内存量降至最低。 未释放给操作系统的已释放内存还原到可用池，并且可用于重新分配。  
  
 调用 `_freea` 必须附带对所有对 `_malloca` 的调用。 在同一内存中调用 `_freea` 两次也是个错误。 当应用程序与 C 运行时库的调试版本链接时，特别是与通过定义 `_CRTDBG_MAP_ALLOC` 启用的 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md) 功能链接时，更容易查找对 `_freea` 的错过或重复调用。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。  
  
 `_freea` 标记为 `__declspec(noalias)`，这表示该函数保证不会修改全局变量。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md)。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`_freea`|\<stdlib.h> 和 \<malloc.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
 请参见 [_malloca](../../c-runtime-library/reference/malloca.md) 的示例。  
  
## <a name="see-also"></a>请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [_malloca](../../c-runtime-library/reference/malloca.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_free_dbg](../../c-runtime-library/reference/free-dbg.md)   
 [_heapmin](../../c-runtime-library/reference/heapmin.md)