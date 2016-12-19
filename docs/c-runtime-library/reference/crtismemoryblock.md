---
title: "_CrtIsMemoryBlock | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtIsMemoryBlock"
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
  - "CrtlsMemoryBlock"
  - "_CrtIsMemoryBlock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CrtIsMemoryBlock 函数"
  - "CrtIsMemoryBlock 函数"
ms.assetid: f7cbbc60-3690-4da0-a07b-68fd7f250273
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtIsMemoryBlock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

验证指定的内存块是在本地堆中，而且它有一个有效的调试堆块类型标识符（仅调试版本）。  
  
## 语法  
  
```  
int _CrtIsMemoryBlock(   
   const void *userData,  
   unsigned int size,  
   long *requestNumber,  
   char **filename,  
   int *linenumber   
);  
```  
  
#### 参数  
 \[in\] `userData`  
 验证内存块的开头的指针。  
  
 \[in\] `size`  
 （以字节）为单位的特定块大小。  
  
 \[out\] `requestNumber`  
 分配块的数目或 `NULL` 的指针。  
  
 \[out\] `filename`  
 指向请求块或 `NULL` 的源文件的名称的指针。  
  
 \[out\] `linenumber`  
 当前源文件中的行号或 `NULL` 的指针。  
  
## 返回值  
 如果指定的内存块位于本地堆内,并有有效的调试堆块类型标识符,`_CrtIsMemoryBlock` 返回 `TRUE` ，否则，函数返回 `FALSE`。  
  
## 备注  
 `_CrtIsMemoryBlock`函数验证在应用程序的本地堆中的指定的内存块，而且它有一个有效的块类型标识符。  此函数还可用于获取对象分配排序数字，并存储区域分配的源文件名和行号最初请求。  传递non\-NULL值到 `requestNumber`，`filename` 或 `linenumber` 参数，如果它发现该块在本地堆中，会导致 `_CrtIsMemoryBlock` 设置这些参数为内存块的调试头的值。  当 [\_DEBUG](../../c-runtime-library/debug.md) 未定义时，在预处理期间移除对 `_CrtIsMemoryBlock` 的调用。  
  
 如果 `_CrtIsMemoryBlock` 失败，则返回`FALSE` 并初始化输出参数为默认值：`requestNumber` 和 `lineNumber` 被设置为 0 并 `filename` 设置为 `NULL`。  
  
 因为函数返回 `TRUE` 或 `FALSE`， 所以能传递一个 [\_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 宏命令来创建一个简单的调试错误处理机制。  如果指定的地址不在本地堆内，则下面的示例将导致论断失败：  
  
```  
_ASSERTE( _CrtIsMemoryBlock( userData, size, &requestNumber,   
&filename, &linenumber ) );  
```  
  
 有关 `_CrtIsMemoryBlock` 如何可用在其它调试函数和宏命令中的详细信息, 请参阅 [用于报告的宏](../Topic/Macros%20for%20Reporting.md)。  有关在调试版本中的基位置堆中内存如何分配，初始化和管理的详细信息，请参阅 [CRT 调试堆详细信息](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_CrtIsMemoryBlock`|\<crtdbg.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## 示例  
 请参阅 [\_CrtIsValidHeapPointer](../../c-runtime-library/reference/crtisvalidheappointer.md) 主题的示例。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)