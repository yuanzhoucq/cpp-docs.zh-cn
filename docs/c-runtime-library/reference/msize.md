---
title: "_msize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_msize"
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
  - "api-ms-win-crt-heap-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "msize"
  - "_msize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_msize 函数"
  - "内存块"
  - "msize 函数"
ms.assetid: 02b1f89e-d0d7-4f12-938a-9eeba48a0f88
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _msize
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回堆中分配的存储块大小。  
  
## 语法  
  
```  
  
      size_t _msize(  
   void *memblock   
);  
```  
  
#### 参数  
 `memblock`  
 内存块的指针。  
  
## 返回值  
 `_msize`返回\(以字节为单位\) 作为无符号整数的大小。  
  
## 备注  
 `_msize` 函数通过调用`calloc` ，`malloc`或 `realloc`，返回分配的内存块字节大小。  
  
 当应用程序与调试版本的 C 运行时库连接时，`_msize` 解析为 [\_malloc\_dbg](../../c-runtime-library/reference/msize-dbg.md)。  有关在调试过程中如何托管堆的详细信息，请参阅  [The CRT Debug Heap](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
 此函数验证其参数。  如果 `memblock` 是一个空指针， `_msize` 调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果错误被处理，函数设置 `errno` 到 `EINVAL` 并返回\-1。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_msize`|\<malloc.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
 请参见[realloc](../../c-runtime-library/reference/realloc.md)示例。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [\_expand](../../c-runtime-library/reference/expand.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)