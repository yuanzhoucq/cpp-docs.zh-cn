---
title: "_recalloc_dbg | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _recalloc_dbg
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
- recalloc_dbg
- _recalloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- _recalloc_dbg function
- recalloc_dbg function
ms.assetid: 43c3e9b2-be6d-4508-9b0f-3220c8a47ca3
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
ms.openlocfilehash: 18c1e36c2671c1c04ae8dd317a14234eda4c09a3
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="recallocdbg"></a>_recalloc_dbg
重新分配数组并将其元素初始化为 0（仅限调试版本）。  
  
## <a name="syntax"></a>语法  
  
```  
void *_recalloc_dbg(   
   void *userData,  
   size_t num,  
   size_t size,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>参数  
 `userData`  
 指向之前分配的内存块的指针。  
  
 `num`  
 内存块的请求数量。  
  
 `size`  
 每个内存块的请求大小（以字节为单位）。  
  
 `blockType`  
 内存块的请求类型：`_CLIENT_BLOCK` 或 `_NORMAL_BLOCK`。  
  
 有关分配块类型及其使用方式的信息，请参阅[调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。  
  
 `filename`  
 指向已请求分配操作的源文件名的指针或 `NULL`。  
  
 `linenumber`  
 请求分配操作所在的源文件中的行数或 `NULL`。  
  
 仅当已显式调用 `_recalloc_dbg` 或已定义 [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) 预处理器常量时，才可使用 `filename` 和 `linenumber` 参数。  
  
## <a name="return-value"></a>返回值  
 成功完成时，此函数将返回指向重新分配的内存块的用户部分的指针、调用新处理程序函数，或者返回 NULL。 有关返回行为的完整说明，请参阅以下“备注”部分。 有关如何使用新处理程序函数的详细信息，请参阅 [_recalloc](../../c-runtime-library/reference/recalloc.md) 函数。  
  
## <a name="remarks"></a>备注  
 `_recalloc_dbg` 是 [_recalloc](../../c-runtime-library/reference/recalloc.md) 函数的调试版本。 未定义 [_DEBUG](../../c-runtime-library/debug.md) 时，每个对 `_recalloc_dbg` 的调用都会减少到对 `_recalloc` 的调用。 `_recalloc` 和 `_recalloc_dbg` 都可重新分配基堆中的内存块，但是 `_recalloc_dbg` 还包含几种调试功能：用于测试泄漏的块的用户部分两侧的缓冲区、用于跟踪特定分配类型的块类型参数，以及用于确定分配请求的源的 `filename`/`linenumber` 信息。  
  
 `_recalloc_dbg` 将按照比请求大小 (`num` * `size`) 稍多的空间重新分配指定的内存块，这样请求大小可能会大于或小于最初分配的内存块大小。 其他空间将由调试堆管理器用于链接调试内存块，以及提供具有调试标头信息的应用程序和覆盖缓冲区。 重新分配可能会导致将原始内存块移动到堆中的其他位置，也可能会导致内存块的大小发生更改。 使用值 0xCD 填充该块的用户部分，使用值 0xFD 填充每个覆盖缓冲区。  
  
 如果内存分配失败，则 `_recalloc_dbg` 将 `errno` 设置为 `ENOMEM`；如果所需的内存量（包括之前提到过的开销）超过 `EINVAL`，则返回 `_HEAP_MAXREQ`。 有关此代码及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。 有关在应用程序的调试版本中调用标准堆函数及其调试版本之间差异的信息，请参阅[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_recalloc_dbg`|\<crtdbg.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## <a name="see-also"></a>另请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)
