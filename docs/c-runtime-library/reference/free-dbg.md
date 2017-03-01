---
title: "_free_dbg | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _free_dbg
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
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, deallocating
- freeing memory
- _free_dbg function
- free_dbg function
ms.assetid: fc5e8299-616d-48a0-b979-e037117278c6
caps.latest.revision: 16
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 7ab13da1c51d75979656c4b70c4874566296e845
ms.lasthandoff: 02/24/2017

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
  
 有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。 有关分配块类型及其使用方式的信息，请参阅[调试堆上的块类型](/visualstudio/debugger/crt-debug-heap-details)。 有关在应用程序的调试版本中调用标准堆函数及其调试版本之间差异的信息，请参阅[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_free_dbg`|\<crtdbg.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 有关如何使用 `_free_dbg` 的示例，请参阅 [crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)
