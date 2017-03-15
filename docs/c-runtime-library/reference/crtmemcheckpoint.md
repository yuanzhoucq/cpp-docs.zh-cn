---
title: "_CrtMemCheckpoint | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtMemCheckpoint
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
dev_langs:
- C++
helpviewer_keywords:
- CrtMemCheckpoint function
- _CrtMemCheckpoint function
ms.assetid: f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 5f9b0615a51318ea0e783a90d7a450b6e11372d2
ms.lasthandoff: 02/24/2017

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
 `_CrtMemCheckpoint` 函数可在任意给定时刻创建调试堆当前状态的快照。 此快照可由其他堆状态函数（如 [_CrtMemDifference](../../c-runtime-library/reference/crtmemdifference.md)）用来帮助检测内存泄漏和其他问题。 未定义 [_DEBUG](../../c-runtime-library/debug.md) 时，会在预处理过程中删除对 `_CrtMemState` 的调用。  
  
 应用程序必须在 `_CrtMemState` 参数中按照 Crtdbg.h 所定义的将指针传递给 `state` 结构以前分配的实例。 如果 `_CrtMemCheckpoint` 在检查点创建期间遇到错误，该函数将生成一份描述问题的 `_CRT_WARN` 调试报告。  
  
 有关堆状态函数和 `_CrtMemState` 结构的详细信息，请参阅[堆状态报告函数](/visualstudio/debugger/crt-debug-heap-details)。 有关如何在基堆的调试版本中分配、初始化和管理内存块的详细信息，请参阅 [CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。  
  
 如果 `state` 为 `NULL`，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 设置为 `EINVAL` 并返回该函数。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_CrtMemCheckpoint`|\<crtdbg.h>、\<errno.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
 **库：** 仅限 UCRT 的调试版本。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [_CrtMemDifference](../../c-runtime-library/reference/crtmemdifference.md)
