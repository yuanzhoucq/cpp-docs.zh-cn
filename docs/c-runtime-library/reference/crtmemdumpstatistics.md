---
title: "_CrtMemDumpStatistics | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtMemDumpStatistics"
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
  - "CrtMemDumpStatistics"
  - "_CrtMemDumpStatistics"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CrtMemDumpStatistics 函数"
  - "CrtMemDumpStatistics 函数"
ms.assetid: 27b9d731-3184-4a2d-b9a7-6566ab28a9fe
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _CrtMemDumpStatistics
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

以用户可读的形式转储指定堆状态的调试标头信息（仅限调试版本）。  
  
## 语法  
  
```  
void _CrtMemDumpStatistics(   
   const _CrtMemState *state   
);  
```  
  
#### 参数  
 `state`  
 指向要转储的堆状态的指针。  
  
## 备注  
 `_CrtMemDumpStatistics` 函数以用户可读的形式转储指定堆状态的调试标头信息。 应用程序可以使用转储统计信息来跟踪分配并检测内存问题。 内存状态可以包含特定的堆状态或两个状态之间的差异。 未定义 [\_DEBUG](../../c-runtime-library/debug.md) 时，将在预处理过程中删除对 `_CrtMemDumpStatistics` 的调用。  
  
 `state` 参数必须是指向 `_CrtMemState` 结构的指针，该结构由 [\_CrtMemCheckpoint](../../c-runtime-library/reference/crtmemcheckpoint.md) 填充，或者在调用 `_CrtMemDumpStatistics` 之前由 [\_CrtMemDifference](../../c-runtime-library/reference/crtmemdifference.md) 返回。 如果 `state` 为 `NULL`，则调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将 `errno` 设置为 `EINVAL`，并且不执行任何操作。 有关详细信息，请参阅 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 有关堆状态函数和 `_CrtMemState` 结构的详细信息，请参阅[Heap State Reporting Functions](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Heap_State_Reporting_Functions)。 有关如何在基堆的调试版本中分配、初始化和管理内存块的详细信息，请参阅 [CRT 调试堆详细信息](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_CrtMemDumpStatistics`|\<crtdbg.h\>|\<errno.h\>|  
  
 有关兼容性的详细信息，请参阅“简介”中的 [兼容性](../../c-runtime-library/compatibility.md)。  
  
 **库：**仅限 [CRT 库功能](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## .NET Framework 等效项  
 <xref:System.Diagnostics.PerformanceCounter?displayProperty=fullName>  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)