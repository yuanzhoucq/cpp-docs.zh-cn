---
title: "_free_dbg | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _free_dbg
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
- _free_dbg
- free_dbg
dev_langs: C++
helpviewer_keywords:
- memory blocks, deallocating
- freeing memory
- _free_dbg function
- free_dbg function
ms.assetid: fc5e8299-616d-48a0-b979-e037117278c6
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fccae4629bc4c1c9b6af71f254c28311210ec0e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="freedbg"></a>_free_dbg
释放堆中的内存块（仅限调试版本）。  
  
## <a name="syntax"></a>语法  
  
```  
void _free_dbg(   
   void *userData,  
   int blockType   
);  
```  
  
#### <a name="parameters"></a>参数  
 `userData`  
 指向要释放的已分配内存块的指针。  
  
 `blockType`  
 要释放的已分配内存块类型：`_CLIENT_BLOCK`、`_NORMAL_BLOCK` 或 `_IGNORE_BLOCK`。  
  
## <a name="remarks"></a>备注  
 `_free_dbg` 函数是 [free](../../c-runtime-library/reference/free.md) 函数的调试版本。 未定义 [_DEBUG](../../c-runtime-library/debug.md) 时，每个对 `_free_dbg` 的调用都会减少到对 `free` 的调用。 `free` 和 `_free_dbg` 都可释放基堆中的内存块，但是 `_free_dbg` 还包含两个调试功能：能够在堆链接列表中保留已释放的块，以便模拟内存不足的情况，以及释放特定分配类型的块类型参数。  
  
 在执行释放操作之前，`_free_dbg` 将在所有指定的文件和块位置上执行有效性检查。 应用程序不应该提供此信息。 当释放内存块时，调试堆管理器自动检查用户部分两侧的缓冲区的完整性，如果发生覆盖，将发出错误报告。 如果设置了 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) 标志的 `_CRTDBG_DELAY_FREE_MEM_DF` 位域，则将使用值 0xDD 填充释放的块、为其分配 `_FREE_BLOCK` 块类型，以及将其保留在内存块的堆链接列表中。  
  
 如果在释放内存时发生错误，则根据操作系统中关于错误性质的信息设置 `errno`。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 有关分配块类型及其使用方式的信息，请参阅[调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。 有关在应用程序的调试版本中调用标准堆函数及其调试版本之间差异的信息，请参阅[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_free_dbg`|\<crtdbg.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
 有关如何使用 `_free_dbg` 的示例，请参阅 [crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)。  
  
## <a name="see-also"></a>请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)