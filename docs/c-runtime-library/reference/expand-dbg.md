---
title: "_expand_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_expand_dbg"
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
  - "expand_dbg"
  - "_expand_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "内存块，更改大小"
  - "expand_dbg 函数"
  - "_expand_dbg 函数"
ms.assetid: dc58c91f-72a8-48c6-b643-fe130fb6c1fd
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# _expand_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通过展开或收缩块调整指定的块在堆中的内存 \(只有调试版本\)。  
  
## 语法  
  
```  
void *_expand_dbg(   
   void *userData,  
   size_t newSize,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### 参数  
 `userData`  
 以前指定内存块的指针。  
  
 `newSize`  
 请求块的新的大小 \(以字节为单位\)。  
  
 `blockType`  
 重置大小块的请求类型：`_CLIENT_BLOCK`  或 `_NORMAL_BLOCK`。  
  
 `filename`  
 需要额外操作或者`NULL`的源文件的名称的指针。  
  
 `linenumber`  
 在请求的扩展操作数或 `NULL` 的源文件中的行号。  
  
 `filename` 和 `linenumber` 的参数只有在 `_expand_dbg` 被明确调用或[\_CRTDBG\_MAP\_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)预处理器被持续定义时才有效。  
  
## 返回值  
 当编译成功，`_expand_dbg` 返回一个重置内存块的指针。  由于内存不会移动，该地址与用户数据一样。  如果错误发生或者内存不能分配请求的块，它返回`NULL`。  如果错误发生，`errno` 返回关于故障错误的操作系统的信息。  有关 `errno`的更多信息，请参见[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `_expand_dbg` 函数是 \_[expand](../../c-runtime-library/reference/expand.md) 函数的调试版本。  当 [\_DEBUG](../../c-runtime-library/debug.md) 未定义时，每次减少调用 `_expand_dbg`  而去调用 `_expand`。   `_expand`  和 `_expand_dbg`  在基堆中重置内存块，但是 `_expand_dbg` 提供一些调试特征：块中用户部分任意侧的缓冲区测试是否泄漏，块类型参数跟踪特定的分配类型，并且`filename`\/`linenumber` 信息决定分配请求的来源。  
  
 `_expand_dbg` 重置比请求的`newSize` 稍微更多空间的内存块。  `newSize`可能比初始分配的内存块大小更多或者更少。  通过调试堆管理器来连接调试内存块并且提供应用程序调试头信息和重写缓冲区来使用额外的空间。  调整大小完成是通过或扩展或缩短原始存储区域。  `_expand_dbg` 不能移动内存块，和 [\_realloc\_dbg](../../c-runtime-library/reference/realloc-dbg.md) 函数一样。  
  
 当 `newSize` 比原始的块还要大，说明内存块被扩展了。  在扩展时，如果内存块不能扩展到请求的大小，`NULL` 被返回。  当 `newSize` 比原始的块还要小，说明内存块被收缩了知道新的大小被获得。  
  
 有关在调试版本中的基位置堆中内存如何分配，初始化和管理的详细信息，请参阅 [CRT 调试堆详细信息](../Topic/CRT%20Debug%20Heap%20Details.md)。  有关分配块的类型以及它们是如何使用的信息，请参阅 [调试堆中的块类型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  有关调用一个标准的堆函数及其调试版本在应用程序的调试版本之间的差异，请参阅[堆分配函数的“Debug”版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)。  
  
 此函数验证其参数。  如果 `memblock` 是无效的指针，或者大小比 `_HEAP_MAXREQ` 大，则函数调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许执行继续，`errno`设置为`EINVAL`，并且函数返回`NULL`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_expand_dbg`|\<crtdbg.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 仅限 [C 运行时](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## 示例  
  
```  
// crt_expand_dbg.c  
//  
// This program allocates a block of memory using _malloc_dbg  
// and then calls _msize_dbg to display the size of that block.  
// Next, it uses _expand_dbg to expand the amount of  
// memory used by the buffer and then calls _msize_dbg again to  
// display the new amount of memory allocated to the buffer.  
//  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
#include <crtdbg.h>  
  
int main( void )  
{  
   long *buffer;  
   size_t size;  
  
   // Call _malloc_dbg to include the filename and line number  
   // of our allocation request in the header  
   buffer = (long *)_malloc_dbg( 40 * sizeof(long),  
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );  
   if( buffer == NULL )  
      exit( 1 );  
  
   // Get the size of the buffer by calling _msize_dbg  
   size = _msize_dbg( buffer, _NORMAL_BLOCK );  
   printf( "Size of block after _malloc_dbg of 40 longs: %u\n", size );  
  
   // Expand the buffer using _expand_dbg and show the new size  
   buffer = (long *)_expand_dbg( buffer, size + sizeof(long),  
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );  
  
   if( buffer == NULL )  
      exit( 1 );  
   size = _msize_dbg( buffer, _NORMAL_BLOCK );  
   printf( "Size of block after _expand_dbg of 1 more long: %u\n",  
           size );  
  
   free( buffer );  
   exit( 0 );  
}  
```  
  
  **在\_malloc\_dbg 40 后的块的的大小：160**  
**在\_malloc\_dbg 1 后的块的的大小：164**   
## Comment  
 该程序的输出取决于您的计算机的扩展的所有部分的能力。  如果所有的部分都是展开的，输出反映在输出部分。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)