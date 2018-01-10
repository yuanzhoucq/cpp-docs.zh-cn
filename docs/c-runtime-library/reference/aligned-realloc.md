---
title: "_aligned_realloc | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _aligned_realloc
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
- _aligned_realloc
- aligned_realloc
dev_langs: C++
helpviewer_keywords:
- aligned_realloc function
- _aligned_realloc function
ms.assetid: 80ce96e8-6087-416f-88aa-4dbb8cb1d218
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 293e519cd107ef64d81d59f08cf7f8d4871e8e6a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="alignedrealloc"></a>_aligned_realloc
更改使用 [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小。  
  
## <a name="syntax"></a>语法  
  
```  
void * _aligned_realloc(  
   void *memblock,   
   size_t size,   
   size_t alignment  
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `memblock`  
 当前的内存块指针。  
  
 [in] `size`  
 请求的内存分配的大小。  
  
 [in] `alignment`  
 对齐值，必须是 2 的整数次幂。  
  
## <a name="return-value"></a>返回值  
 `_aligned_realloc` 将返回指向重新分配的（并且可能已移动的）内存块的 void 指针。 如果大小为零且缓冲区参数不为 `NULL`，或内存不足以将块展开到给定的大小，则返回值为 `NULL`。 在第一种情况下，会释放原始块。 在第二种情况下，将不会更改原始块。 返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要获取指向类型而非 void 的指针，请在返回值上使用类型转换。  
  
 重新分配内存并更改块对齐是错误的。  
  
## <a name="remarks"></a>备注  
 `_aligned_realloc` 基于 `malloc`。 有关使用 `_aligned_offset_malloc` 的详细信息，请参阅 [malloc](../../c-runtime-library/reference/malloc.md)。  
  
 如果内存分配失败或请求的大小大于 `errno`，则此函数会将 `ENOMEM` 设置为 `_HEAP_MAXREQ`。 有关 `errno` 的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外，`_aligned_realloc` 将验证其参数。 如果 `alignment` 不是 2 的幂，则此函数调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数将返回 `NULL` 并将 `errno` 设置为 `EINVAL`。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_aligned_realloc`|\<malloc.h>|  
  
## <a name="example"></a>示例  
 有关详细信息，请参阅 [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md)。  
  
## <a name="see-also"></a>请参阅  
 [数据对齐](../../c-runtime-library/data-alignment.md)