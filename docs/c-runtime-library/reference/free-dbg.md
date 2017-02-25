---
title: "_free_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_free_dbg"
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
  - "_free_dbg"
  - "free_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "内存块, 解除分配"
  - "释放内存"
  - "_free_dbg 函数"
  - "free_dbg 函数"
ms.assetid: fc5e8299-616d-48a0-b979-e037117278c6
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# _free_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

释放一个堆中的内存块（仅限调试版本）。  
  
## 语法  
  
```  
void _free_dbg(   
   void *userData,  
   int blockType   
);  
```  
  
#### 参数  
 `userData`  
 指向被释放已分配的内存块的指针。  
  
 `blockType`  
 被释放的内存块的类型：`_CLIENT_BLOCK`, `_NORMAL_BLOCK` 或 `_IGNORE_BLOCK`。  
  
## 备注  
 `_free_dbg` 函数是 [free](../../c-runtime-library/reference/free.md) 函数的调试版本。  当 [\_DEBUG](../../c-runtime-library/debug.md) 未定义时，每次减少调用`_free_dbg` 而去调用 `free`。  `free` 和 `_free_dbg` 释放基堆中的一个内存块，但是 `_free_dbg`  提供两个调试特性：保持堆的链表来模拟内存不足条件和块类型参数来释放特定的分配类型的能力。  
  
 在执行释放操作前，`_free_dbg`在所有指定的文件和块位置执行验证检查。  该应用程序预计不会提供此信息。  当释放内存块时，调试堆管理器自动检查用户部分两侧的缓冲区的完整性，如果发生覆盖，将发出错误报告。  如果设置 [\_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) 标记的 `_CRTDBG_DELAY_FREE_MEM_DF`  位字段，则用 0xDD 值来填充释放的块，给其分配 `_FREE_BLOCK` 块类型，以及将其保存到堆中内存块的链表中。  
  
 如果在释放内存时发生错误，则将 `errno` 设置为操作系统故障的特性信息。  有关详细信息，请参阅[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 有关在调试版本中的基位置堆中内存如何分配，初始化和管理的详细信息，请参阅 [CRT 调试堆详细信息](../Topic/CRT%20Debug%20Heap%20Details.md)。  有关分配块的类型以及它们是如何使用的信息，请参阅 [调试堆中的块类型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  有关调用一个标准的堆函数及其调试版本在应用程序的调试版本之间的差异，请参阅[堆分配函数的“Debug”版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_free_dbg`|\<crtdbg.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 对于如何使用 `_free_dbg` 的例子，请参阅 [crt\_dbg2](http://msdn.microsoft.com/zh-cn/21e1346a-6a17-4f57-b275-c76813089167)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)