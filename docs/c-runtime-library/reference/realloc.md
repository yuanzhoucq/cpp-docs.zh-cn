---
title: "realloc | Microsoft Docs"
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
  - "realloc"
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
  - "_brealloc"
  - "_nrealloc"
  - "realloc"
  - "_frealloc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_brealloc 函数"
  - "realloc 函数"
  - "nrealloc 函数"
  - "frealloc 函数"
  - "_nrealloc 函数"
  - "内存块, 重新分配"
  - "内存, 重新分配"
  - "_frealloc 函数"
  - "重新分配内存块"
ms.assetid: 2b2239de-810b-4b11-9438-32ab0a244185
caps.latest.revision: 20
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# realloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

重新分配内存块.  
  
## 语法  
  
```  
void *realloc(  
   void *memblock,  
   size_t size   
);  
```  
  
#### 参数  
 `memblock`  
 以前分配的内存块的指针。  
  
 `size`  
 新的大小 \(以字节为单位\)。  
  
## 返回值  
 `realloc` 返回一`void`指针用来重分配的 \(可能移动）内存块。  
  
 如果不展开块的足够的可用内存的特定范围，则块仍保持不变，并且，则返回 `NULL`。  
  
 如果 `size` 为零，则块由 `memblock` 指向释放；返回值是 `NULL`，因此，`memblock` 保留点已释放的块。  
  
 返回值指向保证适当地存储任何类型的对象的对齐的存储空间。  若要获得指向类型的指针而不是 `void`，请对返回值进行类型转换。  
  
## 备注  
 `realloc` 功能将一个分配的存储区的大小。  `memblock` 指向存储区的开头的参数的位置。  如果 `memblock` 为 `NULL`，则 `realloc` 的相同的行为与 `malloc` 并将 `size` 指派字节新块。  如果 `memblock` 不是 `NULL`，它应该是对的上一调用返回的指针为 `calloc`、`malloc`或 `realloc`。  
  
 `size` 参数给出新块的字节大小。  块的内容保持不变的定短新值和旧范围，但新块可以在其他位置。  由于新块可以在新的内存位置，\_返回的指针`realloc` 不一定是指针传递 `memblock`参数。  `realloc` 不为最近分配的内存。缓冲区不断增大。  
  
 如果内存分配失败，或者请求的内存数量超过 `_HEAP_MAXREQ`，那么 `realloc` 设置 `errno` 为 `ENOMEM`。  有关这和其他错误代码的信息，请参阅 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 `realloc` 调用`malloc` 以使用 [\_set\_new\_mode](../../c-runtime-library/reference/set-new-mode.md) C\+\+ 函数将新处理程序模式。  新的处理程序模式指示，在失败时，`malloc` 是否就像 [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md) 设置的那样调用新的处理程序实例。  默认情况下，`malloc` 不调用发生故障的新处理程序例程去分配内存。  您可重写此默认行为，这样一来，当 `realloc` 无法分配内存时， `malloc` 调用新的处理程序例程，其方式与出于相同原因的 `new` 运算符的操作相同。  重写默认值、调用  
  
```  
_set_new_mode(1)  
```  
  
 在您程序的早期，或链接到 NEWMODE.OBJ（请参阅 [链接选项](../../c-runtime-library/link-options.md)）。  
  
 当应用程序与调试版本的 C 运行时库连接时，`realloc` 解析为 [\_realloc\_dbg](../../c-runtime-library/reference/realloc-dbg.md)。  有关在调试过程中如何托管堆的详细信息，请参阅  [The CRT Debug Heap](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
 `realloc` 标记为 `__declspec(noalias)` 和 `__declspec(restrict)`这意味着函数保证不修改全局变量，和返回的指针不用做别名。  有关更多信息，请参见 [没有别名](../../cpp/noalias.md) 和 [限制](../../cpp/restrict.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`realloc`|\<stdlib.h\> 和 \<malloc.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_realloc.c  
// This program allocates a block of memory for  
// buffer and then uses _msize to display the size of that  
// block. Next, it uses realloc to expand the amount of  
// memory used by buffer and then calls _msize again to  
// display the new amount of memory allocated to buffer.  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   long *buffer, *oldbuffer;  
   size_t size;  
  
   if( (buffer = (long *)malloc( 1000 * sizeof( long ) )) == NULL )  
      exit( 1 );  
  
   size = _msize( buffer );  
   printf_s( "Size of block after malloc of 1000 longs: %u\n", size );  
  
   // Reallocate and show new size:  
   oldbuffer = buffer;     // save pointer in case realloc fails  
   if( (buffer = realloc( buffer, size + (1000 * sizeof( long )) ))   
        ==  NULL )  
   {  
      free( oldbuffer );  // free original block  
      exit( 1 );  
   }  
   size = _msize( buffer );  
   printf_s( "Size of block after realloc of 1000 more longs: %u\n",   
            size );  
  
   free( buffer );  
   exit( 0 );  
}  
```  
  
  **在分配1000 后的块的的大小：4000**  
**块的大小在 realloc 的 1000 之后：更长 8000**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)