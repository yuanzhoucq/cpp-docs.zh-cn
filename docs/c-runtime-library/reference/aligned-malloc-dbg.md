---
title: "_aligned_malloc_dbg | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _aligned_malloc_dbg
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
- _aligned_malloc_dbg
- aligned_malloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- aligned_malloc_dbg function
- _aligned_malloc_dbg function
ms.assetid: fb0429c3-685d-4826-9075-2515c5bdc5c6
caps.latest.revision: 8
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: dd7cba44a8352afdf052e570de09499918594e26
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="alignedmallocdbg"></a>_aligned_malloc_dbg
在指定内存边界上为调试标头和覆盖缓冲区分配内存（仅限调试模式）。  
  
## <a name="syntax"></a>语法  
  
```  
void * _aligned_malloc_dbg(  
    size_t size,   
    size_t alignment,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `size`  
 请求的内存分配的大小。  
  
 [in] `alignment`  
 对齐值，必须是 2 的整数次幂。  
  
 [in] `filename`  
 指向已请求分配操作的源文件名的指针或 NULL。  
  
 [in] `linenumber`  
 请求分配操作所在的源文件中的行数或 NULL。  
  
## <a name="return-value"></a>返回值  
 指向已分配的内存块的指针或 `NULL`（如果操作失败）。  
  
## <a name="remarks"></a>备注  
 `_aligned_malloc_dbg` 是 [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) 函数的调试版本。 未定义 [_DEBUG](../../c-runtime-library/debug.md) 时，每个对 `_aligned_malloc_dbg` 的调用都会减少到对 `_aligned_malloc` 的调用。 `_aligned_malloc` 和 `_aligned_malloc_dbg` 都可分配基堆中的内存块，但是 `_aligned_malloc_dbg` 还提供几种调试功能：用于测试泄漏的块的用户部分两侧的缓冲区，以及用于确定分配请求的源的 `filename`/`linenumber` 信息。  
  
 `_aligned_malloc_dbg` 将使用比请求的 `size` 稍多的空间分配内存块。 其他空间将由调试堆管理器用于链接调试内存块，以及提供具有调试标头信息的应用程序和覆盖缓冲区。 分配该块后，使用值 0xCD 填充该块的用户部分，使用值 0xFD 填充每个覆盖缓冲区。  
  
 如果内存分配失败，或者如果所需的内存量（包括之前提到过的开销）超过 `_aligned_malloc_dbg`，则 `errno` 将 `ENOMEM` 设置为 `_HEAP_MAXREQ`。 有关此代码及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外，`_aligned_malloc_dbg` 将验证其参数。 如果 `alignment` 不是 2 的幂或 `size` 是零，则此函数调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数将返回 `NULL` 并将 `errno` 设置为 `EINVAL`。  
  
 有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。 有关分配块类型及其使用方式的信息，请参阅[调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。 有关在应用程序的调试版本中调用标准堆函数及其调试版本之间差异的信息，请参阅[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_aligned_malloc_dbg`|\<crtdbg.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## <a name="see-also"></a>另请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)
