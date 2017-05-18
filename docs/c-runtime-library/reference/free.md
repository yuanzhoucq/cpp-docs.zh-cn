---
title: "free | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- free
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- free
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, deallocating
- free function
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
caps.latest.revision: 14
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
ms.openlocfilehash: fa4dd487cc0a3f1f14f0bca955ca9059c4bbb964
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="free"></a>free
解除分配或释放内存块。  
  
## <a name="syntax"></a>语法  
  
```  
void free(   
   void *memblock   
);  
```  
  
#### <a name="parameters"></a>参数  
 `memblock`  
 要释放的以前分配的内存块。  
  
## <a name="remarks"></a>备注  
 `free` 函数释放以前通过调用 `calloc`、`malloc` 或 `realloc` 分配的内存块 (`memblock`)。 已释放的字节数等于分配块时（在 `realloc` 情况下则为重新分配）请求的字节数。 如果 `memblock` 是 `NULL`，将忽略指针并立即返回 `free`。 尝试释放无效指针（指向并非由 `calloc`、`malloc` 或 `realloc` 分配的内存块的指针）可能会影响后续分配请求，并导致错误。  
  
 如果在释放内存时发生错误，则根据操作系统中关于错误性质的信息设置 `errno`。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 释放内存块后， [_heapmin](../../c-runtime-library/reference/heapmin.md) 通过合并未使用的区域并将其释放回到操作系统，将堆上的可用内存量降至最低。 未释放给操作系统的已释放内存还原到可用池，并且可用于重新分配。  
  
 当应用程序与调试版的 C 运行时库链接时，`free` 将解析为 [_free_dbg](../../c-runtime-library/reference/free-dbg.md)。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。  
  
 `free` 标记为 `__declspec(noalias)`，这表示该函数保证不会修改全局变量。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md)。  
  
 若要释放使用 [_malloca](../../c-runtime-library/reference/malloca.md) 分配的内存，请使用 [_freea](../../c-runtime-library/reference/freea.md)。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`free`|\<stdlib.h> 和 \<malloc.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 请参阅 [malloc](../../c-runtime-library/reference/malloc.md) 的示例。  
  
## <a name="see-also"></a>另请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [_alloca](../../c-runtime-library/reference/alloca.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_free_dbg](../../c-runtime-library/reference/free-dbg.md)   
 [_heapmin](../../c-runtime-library/reference/heapmin.md)   
 [_freea](../../c-runtime-library/reference/freea.md)
