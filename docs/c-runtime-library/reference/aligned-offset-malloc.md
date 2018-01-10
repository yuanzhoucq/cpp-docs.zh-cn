---
title: "_aligned_offset_malloc | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _aligned_offset_malloc
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
- _aligned_offset_malloc
- aligned_offset_malloc
dev_langs: C++
helpviewer_keywords:
- _aligned_offset_malloc function
- aligned_offset_malloc function
ms.assetid: 447681a3-7c95-4655-86ba-fa3a4ca4c521
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 12bb22245619931732d08d3239c89380471f11b2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="alignedoffsetmalloc"></a>_aligned_offset_malloc
在指定对齐边界分配内存。  
  
## <a name="syntax"></a>语法  
  
```  
void * _aligned_offset_malloc(  
   size_t size,   
   size_t alignment,   
   size_t offset  
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `size`  
 请求的内存分配的大小。  
  
 [in] `alignment`  
 对齐值，必须是 2 的整数幂。  
  
 [in] `offset`  
 用于强制对齐的内存分配中的偏移量。  
  
## <a name="return-value"></a>返回值  
 指向已分配的内存块的指针或 `NULL`（如果操作失败）。  
  
## <a name="remarks"></a>备注  
 `_aligned_offset_malloc` 在需要对嵌套元素进行对齐的情况下很有用；例如，嵌套类需要进行对齐的情况。  
  
 `_aligned_offset_malloc` 基于 `malloc`；有关详细信息，请参阅 [malloc](../../c-runtime-library/reference/malloc.md)。  
  
 `_aligned_offset_malloc` 被标记为 `__declspec(noalias)` 和 `__declspec(restrict)`，也就是说确保该函数不能修改全局变量，并且指针返回不使用别名。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md) 和[限制](../../cpp/restrict.md)。  
  
 如果内存分配失败或请求的大小大于 `errno`，则此函数会将 `ENOMEM` 设置为 `_HEAP_MAXREQ`。 有关 `errno` 的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外，`_aligned_offset_malloc` 将验证其参数。 如果 `alignment` 不是 2 的幂或 `offset` 大于或等于 `size` 且非零，则此函数调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数将返回 `NULL` 并将 `errno` 设置为 `EINVAL`。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_aligned_offset_malloc`|\<malloc.h>|  
  
## <a name="example"></a>示例  
 有关详细信息，请参阅 [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md)。  
  
## <a name="see-also"></a>请参阅  
 [数据对齐](../../c-runtime-library/data-alignment.md)