---
title: "_CrtMemCheckpoint | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtMemCheckpoint
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
- CrtMemCheckpoint
- _CrtMemCheckpoint
- crtdbg/_CrtMemCheckpoint
dev_langs: C++
helpviewer_keywords:
- CrtMemCheckpoint function
- _CrtMemCheckpoint function
ms.assetid: f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 39f2a901404a9c2c34dc9147cb4ed51f070396a9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="crtmemcheckpoint"></a>_CrtMemCheckpoint
获取应用程序提供的 `_CrtMemState` 结构中调试堆和存储的当前状态（仅限调试版本）。  
  
## <a name="syntax"></a>语法  
  
```  
void _CrtMemCheckpoint(  
   _CrtMemState *state   
);  
```  
  
#### <a name="parameters"></a>参数  
 `state`  
 指向 `_CrtMemState` 结构以使用内存检查点进行填充的指针。  
  
## <a name="remarks"></a>备注  
 `_CrtMemCheckpoint` 函数可在任意给定时刻创建调试堆当前状态的快照。 此快照可由其他堆状态函数（如 [_CrtMemDifference](../../c-runtime-library/reference/crtmemdifference.md) ）用来帮助检测内存泄漏和其他问题。 未定义 [_DEBUG](../../c-runtime-library/debug.md) 时，会在预处理过程中删除对 `_CrtMemState` 的调用。  
  
 应用程序必须在 `_CrtMemState` 参数中按照 Crtdbg.h 所定义的将指针传递给 `state` 结构以前分配的实例。 如果 `_CrtMemCheckpoint` 在检查点创建期间遇到错误，该函数将生成一份描述问题的 `_CRT_WARN` 调试报告。  
  
 有关堆状态函数和 `_CrtMemState` 结构的详细信息，请参阅 [Heap State Reporting Functions](/visualstudio/debugger/crt-debug-heap-details)。 有关如何在基堆的调试版本中分配、初始化和管理内存块的详细信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。  
  
 如果 `state` 为 `NULL`，则会调用无效的参数处理程序，如 [Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则将 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 设置为 `EINVAL` 并返回该函数。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_CrtMemCheckpoint`|\<crtdbg.h>、\<errno.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
 **库：** 仅限 UCRT 的调试版本。  
  
## <a name="see-also"></a>请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [_CrtMemDifference](../../c-runtime-library/reference/crtmemdifference.md)