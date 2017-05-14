---
title: "_aligned_msize_dbg | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _aligned_msize_dbg
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
- _aligned_msize_dbg
dev_langs:
- C++
helpviewer_keywords:
- _aligned_msize_dbg
ms.assetid: f1c44af0-3f66-4033-81d1-d71d3afecba0
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
ms.openlocfilehash: 5a924af887defa6473c4fa8c8beeccb1d27b1411
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="alignedmsizedbg"></a>_aligned_msize_dbg
返回在堆中分配的内存块的大小（仅限调试版本）。  
  
## <a name="syntax"></a>语法  
  
```  
size_t _aligned_msize_dbg(  
   void *memblock,  
   size_t alignment,  
   size_t offset  
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `memblock`  
 指向内存块的指针。  
  
 [in] `alignment`  
 对齐值，必须是 2 的整数次幂。  
  
 [in] `offset`  
 用于强制对齐的内存分配中的偏移量。  
  
## <a name="return-value"></a>返回值  
 返回无符号整数形式的大小（以字节为单位）。  
  
## <a name="remarks"></a>备注  
 `alignment` 和 `offset` 值必须与传递给分配该块的函数的值相同。  
  
 `_aligned_msize_dbg` 是 [_aligned_msize](../../c-runtime-library/reference/aligned-msize.md) 函数的调试版本。 未定义 [_DEBUG](../../c-runtime-library/debug.md) 时，每个对 `_aligned_msize_dbg` 的调用都会减少到对 `_aligned_msize` 的调用。 `_aligned_msize` 和 `_aligned_msize_dbg` 都计算基堆中的内存块的大小，但 `_aligned_msize_dbg` 增加了一个调试功能：它在返回大小的内存块用户部分的任一侧包括缓冲区。  
  
 此函数验证其参数。 如果 `memblock` 为空指针或 `alignment` 不是 2 的幂，则 `_msize` 会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果处理了错误，则该函数将 `errno` 设置为 `EINVAL` 并返回 -1。  
  
 有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。 有关分配块类型及其使用方式的信息，请参阅[调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。 有关在应用程序的调试版本中调用标准堆函数及其调试版本之间差异的信息，请参阅[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_aligned_msize_dbg`|\<crtdbg.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## <a name="see-also"></a>另请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)
