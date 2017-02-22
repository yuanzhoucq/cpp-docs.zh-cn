---
title: "_CrtMemDifference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtMemDifference"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_CrtMemDifference"
  - "CrtMemDifference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CrtMemDifference 函数"
  - "_CrtMemDifference 函数"
ms.assetid: 0f327278-b551-482f-958b-76941f796ba4
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# _CrtMemDifference
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

比较两个内存状态，并返回它们的差异（仅限调试版本）。  
  
## 语法  
  
```  
int _CrtMemDifference(   
   _CrtMemState *stateDiff,  
   const _CrtMemState *oldState,  
   const _CrtMemState *newState   
);  
```  
  
#### 参数  
 `stateDiff`  
 指向 `_CrtMemState` 结构的指针，此结构用来存储这两个内存状态（已返回）的差异。  
  
 `oldState`  
 指向较早内存状态（`_CrtMemState` 结构）的指针。  
  
 `newState`  
 指向更后内存状态（`_CrtMemState` 结构）的指针。  
  
## 返回值  
 如果内存状态大不相同，`_CrtMemDifference` 将返回 TRUE。 否则，此函数返回 FALSE。  
  
## 备注  
 `_CrtMemDifference` 函数对比 `oldState` 和 `newState`，并存储它们在 `stateDiff` 中的差异，应用程序随后可使用此差异来检测内存泄露和其他内存问题。 未定义 [\_DEBUG](../../c-runtime-library/debug.md) 时，将在预处理过程中删除对 `_CrtMemDifference` 的调用。  
  
 按 Crtdbg.h 中定义，`newState` 和 `oldState` 必须均为指向 `_CrtMemState` 结构的有效指针，此结构在调用 `_CrtMemDifference` 之前已由 [\_CrtMemCheckpoint](../../c-runtime-library/reference/crtmemcheckpoint.md) 填充。`stateDiff` 必须为一个指针，指向 `_CrtMemState` 结构中先前分配的实例。 如果 `stateDiff`、`newState` 或 `oldState` 是 `NULL`，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。 如果允许继续执行，则将 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 设置为 `EINVAL`，并且此函数返回 FALSE。  
  
 `_CrtMemDifference` 将 `oldState` 中块的 `_CrtMemState` 字段值与 `newState` 中的此类字段值进行比较，并将结果存储在 `stateDiff` 中。 当这两个内存状态的已分配块类型数目或各类型的已分配块数不同时，将这两个状态称为大不相同。`stateDiff` 中还存储了同时向这两个状态分配的最大数之间的差异，以及这两个状态的总分配数之间的差异。  
  
 默认情况下，内存状态操作中不包含内部 C 运行时块 \(`_CRT_BLOCK`\)。[\_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) 函数可用来打开 `_crtDbgFlag` 的 `_CRTDBG_CHECK_CRT_DF` 位，以将这些块包含在泄漏检测和其他内存状态操作中。 已释放的内存块 \(`_FREE_BLOCK`\) 不会导致 `_CrtMemDifference` 返回 TRUE。  
  
 有关堆状态函数和 `_CrtMemState` 结构的详细信息，请参阅[Heap State Reporting Functions](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Heap_State_Reporting_Functions)。 若要了解如何在基堆的调试版本中分配、初始化和管理内存块，请参阅 [CRT 调试堆详细信息](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_CrtMemDifference`|\<crtdbg.h\>|\<errno.h\>|  
  
 有关兼容性的详细信息，请参阅“简介”中的 [兼容性](../../c-runtime-library/compatibility.md)。  
  
 **库：**仅限 [CRT 库功能](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## .NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅 [平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [\_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)