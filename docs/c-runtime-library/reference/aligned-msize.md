---
title: "_aligned_msize | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _aligned_msize
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
- _aligned_msize
- aligned_msize
dev_langs:
- C++
helpviewer_keywords:
- aligned_msize function
- _aligned_msize function
ms.assetid: 10995edc-2110-4212-9ca9-5e0220a464f4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e42427fd5c1c879b82dae4f8580627fbfbe67820
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="alignedmsize"></a>_aligned_msize
返回在堆中分配的存储块的大小。  
  
## <a name="syntax"></a>语法  
  
```  
size_t _msize(  
   void *memblock,  
   size_t alignment,  
   size_t offset  
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `memblock`  
 指向内存块的指针。  
  
 [in] `alignment`  
 对齐值，必须是 2 的整数幂。  
  
 [in] `offset`  
 用于强制对齐的内存分配中的偏移量。  
  
## <a name="return-value"></a>返回值  
 返回无符号整数形式的大小（以字节为单位）。  
  
## <a name="remarks"></a>备注  
 `_aligned_msize` 函数通过调用 [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_realloc](../../c-runtime-library/reference/aligned-realloc.md) 返回分配的内存块的大小（以字节为单位）。 `alignment` 和 `offset` 值必须与传递给分配该块的函数的值相同。  
  
 当应用程序与调试版的 C 运行库链接时，`_aligned_msize` 将解析为 [_aligned_msize_dbg](../../c-runtime-library/reference/aligned-msize-dbg.md)。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。  
  
 此函数验证其参数。 如果 `memblock` 为空指针或 `alignment` 不是 2 的幂，则 `_msize` 会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果处理了错误，则该函数将 `errno` 设置为 `EINVAL` 并返回 -1。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_msize`|\<malloc.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="see-also"></a>请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)