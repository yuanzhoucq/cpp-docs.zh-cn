---
title: "_CrtCheckMemory | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _CrtCheckMemory
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
- CrtCheckMemory
- _CrtCheckMemory
dev_langs:
- C++
helpviewer_keywords:
- _CrtCheckMemory function
- CrtCheckMemory function
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 36ae2b6e4edc1190859d39b658dedf9a5c0c3acd
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="crtcheckmemory"></a>_CrtCheckMemory
确认在调试堆中分配的内存块的完整性（仅限调试版）。  
  
## <a name="syntax"></a>语法  
  
```  
  
int _CrtCheckMemory( void );  
```  
  
## <a name="return-value"></a>返回值  
 如果成功，`_CrtCheckMemory` 返回 TRUE；否则，函数返回 FALSE。  
  
## <a name="remarks"></a>备注  
 `_CrtCheckMemory` 函数通过验证基础基堆并检查每个内存块来验证由调试堆管理器分配的内存。 如果在基础基堆、调试标头信息或覆盖缓冲区中遇到错误或内存不一致，`_CrtCheckMemory` 将生成调试报告，其中包括描述错误条件的信息。 未定义 [_DEBUG](../../c-runtime-library/debug.md) 时，会在预处理过程中删除对 `_CrtCheckMemory` 的调用。  
  
 可使用 [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) 函数设置 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) 标志的位字段来控制 `_CrtCheckMemory` 的行为。 启用 **_CRTDBG_CHECK_ALWAYS_DF** 位字段将导致每次请求内存分配操作时调用 `_CrtCheckMemory`。 尽管此方法减慢了执行速度，但它对快速捕获错误很有用。 禁用 **_CRTDBG_ALLOC_MEM_DF** 位字段会导致 `_CrtCheckMemory` 不验证堆并立即返回 **TRUE**。  
  
 因为此函数返回 **TRUE** 或 **FALSE**，因此可将它传递到其中一个 [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 宏，以创建一种简单的调试错误处理机制。 在堆中检测到损坏时，下面的示例将导致断言失败：  
  
```  
_ASSERTE( _CrtCheckMemory( ) );  
```  
  
 有关如何将 `_CrtCheckMemory` 与其他调试函数一起使用的详细信息，请参阅[堆状态报告函数](/visualstudio/debugger/crt-debug-heap-details)。 有关内存管理和调试堆的概述，请参阅 [CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_CrtCheckMemory`|\<crtdbg.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## <a name="example"></a>示例  
 有关如何使用 `_CrtCheckMemory` 的示例，请参阅 [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1)。  
  
## <a name="see-also"></a>请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)   
 [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md)