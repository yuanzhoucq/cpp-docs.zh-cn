---
title: "_CrtDumpMemoryLeaks | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtDumpMemoryLeaks"
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
  - "CRTDBG_LEAK_CHECK_DF"
  - "CRTDBG_CHECK_CRT_DF"
  - "_CRTDBG_LEAK_CHECK_DF"
  - "CrtDumpMemoryLeaks"
  - "_CrtDumpMemoryLeaks"
  - "_CRTDBG_CHECK_CRT_DF"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CrtDumpMemoryLeaks 函数"
  - "CRTDBG_LEAK_CHECK_DF 宏"
  - "_CRTDBG_LEAK_CHECK_DF 宏"
  - "_CrtDumpMemoryLeaks 函数"
  - "CRTDBG_CHECK_CRT_DF 宏"
  - "_CRTDBG_CHECK_CRT_DF 宏"
ms.assetid: 71b2eab4-7f55-44e8-a55a-bfea4f32d34c
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _CrtDumpMemoryLeaks
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当发生内存泄漏时，转储所有调试堆中的内存块（只限调试版本）  
  
## 语法  
  
```  
  
int _CrtDumpMemoryLeaks( void );  
```  
  
## 返回值  
 如果发生内存泄露，则 `_CrtDumpMemoryLeaks` 返回 TRUE。  否则，该函数返回 FALSE。  
  
## 备注  
 `_CrtDumpMemoryLeaks` 函数决定自项目开始执行是否发生内存泄漏。  当发现泄漏时，在堆中的所有对象的调试头信息转储速率为用户可读形式。  当 [\_DEBUG](../../c-runtime-library/debug.md) 未定义时，在预处理期间移除对 `_CrtDumpMemoryLeaks` 的调用。  
  
 `_CrtDumpMemoryLeaks` 经常在项目执行最后被调用，以验证所有通过应用程序分配的内存全部被释放。  通过使用[\_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) 函数打开 [\_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) 标志的 `_CRTDBG_LEAK_CHECK_DF` 位字段来在程序终端能自动调用该函数。  
  
 `_CrtDumpMemoryLeaks` 调用 [\_CrtMemCheckpoint](../../c-runtime-library/reference/crtmemcheckpoint.md) 获取堆得当前状态，然后扫描未释放块的状态。  当碰到未释放块时，`_CrtDumpMemoryLeaks` 调用 [\_CrtMemDumpAllObjectsSince](../../c-runtime-library/reference/crtmemdumpallobjectssince.md) 为从项目执行开始堆中国的所有项目转储信息。  
  
 默认情况下，内部 C 运行时块 \(`_CRT_BLOCK`\) 不包括内存转储操作。  [\_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) 函数可以用来打开`_crtDbgFlag`的 `_CRTDBG_CHECK_CRT_DF` 位用来包含在泄漏检测进程中的这些块。  
  
 有关堆状态函数的详细信息和 `_CrtMemState`结构，请参见 [堆状态报告函数](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Heap_State_Reporting_Functions)。  有关在调试版本中的基位置堆中内存如何分配，初始化和管理的详细信息，请参见 [CRT 调试堆详细信息](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_CrtDumpMemoryLeaks`|\<crtdbg.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## 示例  
 对于如何使用 `_CrtDumpMemoryLeaks` 的例子，请参阅 [crt\_dbg1](http://msdn.microsoft.com/zh-cn/17b4b20c-e849-48f5-8eb5-dca6509cbaf9)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)