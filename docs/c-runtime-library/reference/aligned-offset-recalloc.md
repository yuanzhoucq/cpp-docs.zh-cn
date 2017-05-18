---
title: "_aligned_offset_recalloc | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _aligned_offset_recalloc
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
- aligned_offset_recalloc
- _aligned_offset_recalloc
dev_langs:
- C++
helpviewer_keywords:
- aligned_offset_recalloc function
- _aligned_offset_recalloc function
ms.assetid: a258f54e-eeb4-4853-96fc-007d710f98e9
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
ms.openlocfilehash: c2586cdd836795a31e457edcba42292a6901ec6f
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="alignedoffsetrecalloc"></a>_aligned_offset_recalloc
更改使用 [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小，并将该内存初始化为 0。  
  
## <a name="syntax"></a>语法  
  
```  
void * _aligned_offset_recalloc(  
   void *memblock,   
   size_t num,   
   size_t size,   
   size_t alignment,  
   size_t offset  
);  
```  
  
#### <a name="parameters"></a>参数  
 `memblock`  
 当前的内存块指针。  
  
 `num`  
 元素数量。  
  
 `size`  
 每个元素的长度（以字节为单位）。  
  
 `alignment`  
 对齐值，必须是 2 的整数次幂。  
  
 `offset`  
 用于强制对齐的内存分配中的偏移量。  
  
## <a name="return-value"></a>返回值  
 `_aligned_offset_recalloc` 将返回指向重新分配的（并且可能已移动的）内存块的 void 指针。 如果大小为零且缓冲区参数不为 `NULL`，或内存不足以将块展开到给定的大小，则返回值为 `NULL`。 在第一种情况下，会释放原始块。 在第二种情况下，将不会更改原始块。 返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要获取指向类型而非 void 的指针，请在返回值上使用类型转换。  
  
 `_aligned_offset_recalloc` 被标记为 `__declspec(noalias)` 和 `__declspec(restrict)`，也就是说确保该函数不能修改全局变量，并且指针返回不使用别名。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md) 和[限制](../../cpp/restrict.md)。  
  
## <a name="remarks"></a>备注  
 与 [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 相同，`_aligned_offset_recalloc` 也允许在结构内的某个偏移量上对齐结构。  
  
 `_aligned_offset_recalloc` 基于 `malloc`。 有关使用 `_aligned_offset_malloc` 的详细信息，请参阅 [malloc](../../c-runtime-library/reference/malloc.md)。 如果 `memblock` 是 `NULL`，则函数从内部调用 `_aligned_offset_malloc`。  
  
 如果内存分配失败或请求的大小 (`num` * `size`) 大于 `_HEAP_MAXREQ`，则此函数会将 `errno` 设置为 `ENOMEM`。 有关 `errno` 的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外，`_aligned_offset_recalloc` 将验证其参数。 如果 `alignment` 不是 2 的幂或 `offset` 大于或等于请求的大小且非零，则此函数调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数将返回 `NULL` 并将 `errno` 设置为 `EINVAL`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_aligned_offset_recalloc`|\<malloc.h>|  
  
## <a name="see-also"></a>另请参阅  
 [数据对齐](../../c-runtime-library/data-alignment.md)   
 [_recalloc](../../c-runtime-library/reference/recalloc.md)   
 [_aligned_recalloc](../../c-runtime-library/reference/aligned-recalloc.md)
