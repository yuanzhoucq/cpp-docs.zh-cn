---
title: "_calloc_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_calloc_dbg"
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
  - "_calloc_dbg"
  - "calloc_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_calloc_dbg 函数"
  - "calloc_dbg 函数"
ms.assetid: 7f62c42b-eb9f-4de5-87d0-df57036c87de
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# _calloc_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为调试标头耦合重写缓冲区在堆中用额外的空间分配一些内存块 \(仅限调试版本\)。  
  
## 语法  
  
```  
void *_calloc_dbg(   
   size_t num,  
   size_t size,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### 参数  
 `num`  
 请求的内存块数量。  
  
 `size`  
 每个内存块请求的大小 \(字节\)。  
  
 `blockType`  
 内存块的请求类型的：`_CLIENT_BLOCK` 或 `_NORMAL_BLOCK`。  
  
 有关分配块的类型以及它们是如何使用的信息，请参阅 [调试堆中的块类型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  
  
 `filename`  
 指向请求分配操作或者`NULL`的源文件的名称的指针。  
  
 `linenumber`  
 在请求的分配操作数或为 `NULL` 的源文件中的行号。  
  
 `filename` 和 `linenumber` 的参数只有在 `_calloc_dbg` 被明确调用或[\_CRTDBG\_MAP\_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)预处理器被持续定义时才有效。  
  
## 返回值  
 成功完成后，此函数返回指向最新分配内存块的用户部分的指针，调用新的处理程序函数或返回 `NULL`。  对于返回行为的完整描述，请参阅备注部分。  有关如何使用新的处理函数的详细信息，请参阅 [calloc](../../c-runtime-library/reference/calloc.md) 函数。  
  
## 备注  
 `_calloc_dbg` 是  [calloc](../../c-runtime-library/reference/calloc.md) 函数的一种调试版本。  当 [\_DEBUG](../../c-runtime-library/debug.md) 未定义时，每次减少调用`_calloc_dbg` 而去调用 `calloc`。  `calloc` 和 `_calloc_dbg` 都分配在基堆中的`num` 内存块，但是 `_calloc_dbg` 提供一些调试特性：  
  
-   块的用户部分的任意侧的缓冲区用来测试是否泄漏。  
  
-   一个块类型的参数用来跟踪特定分配类型。  
  
-   `filename`\/`linenumber` 信息用来确定分配请求的来源。  
  
 `_calloc_dbg` 分配每个比请求的`size` 稍微更多空间的内存块。  通过调试堆管理器来连接调试内存块并且提供应用程序调试头信息和重写缓冲区来使用额外的空间。  当分配块时，块的用户部分用 0xCD 值填充，并且每个覆盖缓冲区用 0xFD 值填充。  
  
 如果内存分配失败， 则`_calloc_dbg` 将 `ENOMEM` 设置为`errno` ；如果需要的内存数（包括之前提到的开销）超过`_HEAP_MAXREQ`，则返回 `EINVAL` 。  有关这和其他错误代码的信息，请参阅 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 有关在调试版本中的基位置堆中内存如何分配，初始化和管理的详细信息，请参阅 [CRT 调试堆详细信息](../Topic/CRT%20Debug%20Heap%20Details.md)。  有关调用一个标准的堆函数及其调试版本在应用程序的调试版本之间的差异，请参阅[堆分配函数的“Debug”版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_calloc_dbg`|\<crtdbg.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_callocd.c  
/*  
 * This program uses _calloc_dbg to allocate space for  
 * 40 long integers. It initializes each element to zero.  
 */  
#include <stdio.h>  
#include <malloc.h>  
#include <crtdbg.h>  
  
int main( void )  
{  
        long *bufferN, *bufferC;  
  
        /*   
         * Call _calloc_dbg to include the filename and line number  
         * of our allocation request in the header and also so we can  
         * allocate CLIENT type blocks specifically  
         */  
        bufferN = (long *)_calloc_dbg( 40, sizeof(long), _NORMAL_BLOCK, __FILE__, __LINE__ );  
        bufferC = (long *)_calloc_dbg( 40, sizeof(long), _CLIENT_BLOCK, __FILE__, __LINE__ );  
        if( bufferN != NULL && bufferC != NULL )  
              printf( "Allocated memory successfully\n" );  
        else  
              printf( "Problem allocating memory\n" );  
  
        /*   
         * _free_dbg must be called to free CLIENT type blocks  
         */  
        free( bufferN );  
        _free_dbg( bufferC, _CLIENT_BLOCK );  
}  
```  
  
  **成功分配内存**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)   
 [\_DEBUG](../../c-runtime-library/debug.md)