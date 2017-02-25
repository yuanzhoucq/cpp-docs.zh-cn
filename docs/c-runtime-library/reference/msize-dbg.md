---
title: "_msize_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_msize_dbg"
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
  - "_msize_dbg"
  - "msize_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "内存块"
  - "_msize_dbg 函数"
  - "msize_dbg 函数"
ms.assetid: a333f4b6-f8a2-4e61-bb69-cb34063b8cef
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _msize_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算在堆中内存块的大小 \(仅限调试版本\)。  
  
## 语法  
  
```  
  
      size_t _msize_dbg(  
   void *userData,  
   int blockType   
);  
```  
  
#### 参数  
 `userData`  
 指向用于确定大小的内存块的指针。  
  
 *blockType*  
 指定的内存块类型：`_CLIENT_BLOCK` 或 **\_NORMAL\_BLOCK**。  
  
## 返回值  
 成功完成后，`_msize_dbg` 返回指定内存块的大小（以字节为单位）；否则返回 NULL。  
  
## 备注  
 `_msize_dbg` 是 \_[msize](../../c-runtime-library/reference/msize.md) 函数的一种调试版本。  当 [\_DEBUG](../../c-runtime-library/debug.md) 未定义时，每次减少调用`_msize_dbg` 而去调用 `_msize`。  `_msize` 和 `_msize_dbg` 计算在基堆中的内存块的大小，但是 `_msize_dbg` 添加两个调试特性：它包括在返回大小的内存块中用户部分任意侧的缓存区和允许用于指定块字节大小计算。  
  
 有关在调试版本中的基位置堆中内存如何分配，初始化和管理的详细信息，请参阅 [CRT 调试堆详细信息](../Topic/CRT%20Debug%20Heap%20Details.md)。  有关分配块的类型以及它们是如何使用的信息，请参阅 [调试堆中的块类型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  有关调用一个标准的堆函数及其调试版本在应用程序的调试版本之间的差异，请参阅[堆分配函数的“Debug”版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)。  
  
 此函数验证其参数。  如果 `memblock` 是一个空指针， `_msize` 调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果错误被处理，函数设置 `errno` 到 `EINVAL` 并返回\-1。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_msize_dbg`|\<crtdbg.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## 示例  
  
```  
// crt_msize_dbg.c  
// compile with: /MTd  
/*  
 * This program allocates a block of memory using _malloc_dbg  
 * and then calls _msize_dbg to display the size of that block.  
 * Next, it uses _realloc_dbg to expand the amount of  
 * memory used by the buffer and then calls _msize_dbg again to  
 * display the new amount of memory allocated to the buffer.  
 */  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
#include <crtdbg.h>  
  
int main( void )  
{  
        long *buffer, *newbuffer;  
        size_t size;  
  
        /*   
         * Call _malloc_dbg to include the filename and line number  
         * of our allocation request in the header  
         */  
        buffer = (long *)_malloc_dbg( 40 * sizeof(long), _NORMAL_BLOCK, __FILE__, __LINE__ );  
        if( buffer == NULL )  
               exit( 1 );  
  
        /*   
         * Get the size of the buffer by calling _msize_dbg  
         */  
        size = _msize_dbg( buffer, _NORMAL_BLOCK );  
        printf( "Size of block after _malloc_dbg of 40 longs: %u\n", size );  
  
        /*   
         * Reallocate the buffer using _realloc_dbg and show the new size  
         */  
        newbuffer = _realloc_dbg( buffer, size + (40 * sizeof(long)), _NORMAL_BLOCK, __FILE__, __LINE__ );  
        if( newbuffer == NULL )  
               exit( 1 );  
        buffer = newbuffer;  
        size = _msize_dbg( buffer, _NORMAL_BLOCK );  
        printf( "Size of block after _realloc_dbg of 40 more longs: %u\n", size );  
  
        free( buffer );  
        exit( 0 );  
}  
```  
  
## Output  
  
```  
Size of block after _malloc_dbg of 40 longs: 160  
Size of block after _realloc_dbg of 40 more longs: 320  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)