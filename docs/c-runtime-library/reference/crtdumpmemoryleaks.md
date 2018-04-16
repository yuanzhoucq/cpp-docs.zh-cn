---
title: "_CrtDumpMemoryLeaks | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _CrtDumpMemoryLeaks
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
- CRTDBG_LEAK_CHECK_DF
- CRTDBG_CHECK_CRT_DF
- _CRTDBG_LEAK_CHECK_DF
- CrtDumpMemoryLeaks
- _CrtDumpMemoryLeaks
- _CRTDBG_CHECK_CRT_DF
dev_langs:
- C++
helpviewer_keywords:
- CrtDumpMemoryLeaks function
- CRTDBG_LEAK_CHECK_DF macro
- _CRTDBG_LEAK_CHECK_DF macro
- _CrtDumpMemoryLeaks function
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: 71b2eab4-7f55-44e8-a55a-bfea4f32d34c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f71e37da509d4e8dd05c5a41afa9fe539294347
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="crtdumpmemoryleaks"></a>_CrtDumpMemoryLeaks
发生内存泄漏时，转储调试堆中的所有内存块（仅限调试版本）。  
  
## <a name="syntax"></a>语法  
  
```  
  
int _CrtDumpMemoryLeaks( void );  
```  
  
## <a name="return-value"></a>返回值  
 如果发现内存泄漏，则 `_CrtDumpMemoryLeaks` 返回 TRUE。 否则，此函数返回 FALSE。  
  
## <a name="remarks"></a>备注  
 `_CrtDumpMemoryLeaks` 函数确定自程序开始执行以来是否发生内存泄漏。 当发现泄漏时，以用户可读形式转储堆中所有对象的调试标头信息。 未定义 [_DEBUG](../../c-runtime-library/debug.md) 时，会在预处理过程中删除对 `_CrtDumpMemoryLeaks` 的调用。  
  
 在程序执行结束时频繁调用 `_CrtDumpMemoryLeaks`，以验证由应用程序分配的所有内存是否已释放。 使用 [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md)函数打开 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) 标志的 `_CRTDBG_LEAK_CHECK_DF` 位域，可以在程序终止时自动调用该函数。  
  
 `_CrtDumpMemoryLeaks` 调用 [_CrtMemCheckpoint](../../c-runtime-library/reference/crtmemcheckpoint.md) 以获取堆的当前状态，然后扫描尚未释放的块的状态。 当遇到未释放的块时，`_CrtDumpMemoryLeaks` 调用 [_CrtMemDumpAllObjectsSince](../../c-runtime-library/reference/crtmemdumpallobjectssince.md)，转储自程序开始执行时堆中分配的所有对象的信息。  
  
 默认情况下，内存转储操作不包含内部 C 运行时块 (`_CRT_BLOCK`)。 [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) 函数可用来打开 `_crtDbgFlag` 的 `_CRTDBG_CHECK_CRT_DF` 位，以将这些块包含在泄漏检测进程中。  
  
 有关堆状态函数和 `_CrtMemState` 结构的详细信息，请参阅 [Heap State Reporting Functions](/visualstudio/debugger/crt-debug-heap-details)。 有关如何在基堆的调试版本中分配、初始化和管理内存块的详细信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_CrtDumpMemoryLeaks`|\<crtdbg.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## <a name="example"></a>示例  
 有关如何使用 `_CrtDumpMemoryLeaks` 的示例，请参阅 [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1)。  
  
## <a name="see-also"></a>请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)