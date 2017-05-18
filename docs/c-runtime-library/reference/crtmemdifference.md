---
title: "_CrtMemDifference | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtMemDifference
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
- _CrtMemDifference
- CrtMemDifference
dev_langs:
- C++
helpviewer_keywords:
- CrtMemDifference function
- _CrtMemDifference function
ms.assetid: 0f327278-b551-482f-958b-76941f796ba4
caps.latest.revision: 16
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 9793a58ed76b4c3251936b9016f8308ad06a07fb
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="crtmemdifference"></a>_CrtMemDifference
比较两个内存状态，并返回它们的差异（仅限调试版本）。  
  
## <a name="syntax"></a>语法  
  
```  
int _CrtMemDifference(   
   _CrtMemState *stateDiff,  
   const _CrtMemState *oldState,  
   const _CrtMemState *newState   
);  
```  
  
#### <a name="parameters"></a>参数  
 `stateDiff`  
 指向 `_CrtMemState` 结构的指针，此结构用来存储这两个内存状态（已返回）的差异。  
  
 `oldState`  
 指向较早内存状态（`_CrtMemState` 结构）的指针。  
  
 `newState`  
 指向更后内存状态（`_CrtMemState` 结构）的指针。  
  
## <a name="return-value"></a>返回值  
 如果内存状态大不相同， `_CrtMemDifference` 将返回 TRUE。 否则，此函数返回 FALSE。  
  
## <a name="remarks"></a>备注  
 `_CrtMemDifference` 函数对比 `oldState` 和 `newState` ，并存储它们在 `stateDiff`中的差异，应用程序随后可使用此差异来检测内存泄露和其他内存问题。 未定义 [_DEBUG](../../c-runtime-library/debug.md) 时，将在预处理过程中删除对 `_CrtMemDifference` 的调用。  
  
 `newState` 和 `oldState` 必须均为指向 `_CrtMemState` 结构的有效指针，此结构在调用 [_CrtMemDifference](../../c-runtime-library/reference/crtmemcheckpoint.md) 之前已由 `_CrtMemDifference`填充。 `stateDiff` 必须为一个指针，指向 `_CrtMemState` 结构中先前分配的实例。 如果 `stateDiff`、`newState` 或 `oldState` 为 `NULL`，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 设置为 `EINVAL` 并且该函数返回 FALSE。  
  
 `_CrtMemDifference` 将 `oldState` 中块的 `_CrtMemState` 字段值与 `newState` 中的此类字段值进行比较，并将结果存储在 `stateDiff` 中。 当这两个内存状态的已分配块类型数目或各类型的已分配块数不同时，将这两个状态称为大不相同。 `stateDiff`中还存储了同时向这两个状态分配的最大数之间的差异，以及这两个状态的总分配数之间的差异。  
  
 默认情况下，内存状态操作中不包含内部 C 运行时块 (`_CRT_BLOCK`)。 [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) 函数可用来打开 `_crtDbgFlag` 的 `_CRTDBG_CHECK_CRT_DF` 位，以将这些块包含在泄漏检测和其他内存状态操作中。 已释放的内存块 (`_FREE_BLOCK`) 不会导致 `_CrtMemDifference` 返回 TRUE。  
  
 有关堆状态函数和 `_CrtMemState` 结构的详细信息，请参阅 [Heap State Reporting Functions](/visualstudio/debugger/crt-debug-heap-details)填充。 有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|可选标头|  
|-------------|---------------------|---------------------|  
|`_CrtMemDifference`|\<crtdbg.h>|\<errno.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
 **库：**仅限 [CRT 库功能](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## <a name="see-also"></a>另请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)
