---
title: "_expand | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_expand"
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
  - "_bexpand"
  - "fexpand"
  - "expand"
  - "nexpand"
  - "_fexpand"
  - "_nexpand"
  - "bexpand"
  - "_expand"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_expand 函数"
  - "expand 函数"
  - "内存块, 更改大小"
ms.assetid: 4ac55410-39c8-45c7-bccd-3f1042ae2ed3
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# _expand
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

更改存储区的大小。  
  
## 语法  
  
```  
void *_expand(   
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
 `_expand` 返回指向分配的存储区的空指针。  `_expand`，与 `realloc`不同的是，无法通过移动块更改其大小。  因而，如果有足够的内存扩展，而无需移动块，则`_expand` 的 `memblock` 参数与返回值相同。  
  
 在操作期间，如果检测到错误，`_expand` 返回 `NULL`。  例如，如果 `_expand`用于缩小存储区，小型块堆或无效的块指针可能检测到失败并返回`NULL`。  
  
 如果无需移动的情况下可用内存不足展开为给定的大小，则函数返回 `NULL`。  `_expand` 从不返回展开的范围小于请求的块。  如果失败，`errno` 指示失败的性质。  有关 `errno`的更多信息，请参见[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 返回值指向保证适当地存储任何类型的对象的对齐的存储空间。  请使用 `_msize`,检查项的新范围。  若要获得指向类型的指针而不是 `void`，请对返回值进行类型转换。  
  
## 备注  
 尝试展开或收缩块，而无需移动其堆位置`_expand` 函数更改以前分配的存储区域的大小。  `memblock` 参数指向块的开始位置。  `size` 参数为新块的字节大小。  块的内容保持不变,大小变为新值和旧值大小的较小者。  `memblock` 不应是已释放的块。  
  
> [!NOTE]
>  在 64 位平台上，如果新的大小小于当前范围，`_expand` 可能不缩小块；特别是，如果，块的大小小于 16K 尺寸并处于低碎片堆分配，`_expand`保留块不变并返回 `memblock`。  
  
 当应用程序与调试版本的 C 运行时库连接时，`_expand` 解析为 [\_expand\_dbg](../../c-runtime-library/reference/expand-dbg.md)。  有关在调试过程中如何托管堆的详细信息，请参阅  [The CRT Debug Heap](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
 此函数验证其参数。  如果 `memblock` 是 null 指针，函数会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续，`errno`设置为`EINVAL`，并且函数返回`NULL`。  如果 `size` 大于 `_HEAP_MAXREQ`，设置`errno` 为 `ENOMEM`，并且函数返回 `NULL`。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`_expand`|\<malloc.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_expand.c  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char *bufchar;  
   printf( "Allocate a 512 element buffer\n" );  
   if( (bufchar = (char *)calloc( 512, sizeof( char ) )) == NULL )  
      exit( 1 );  
   printf( "Allocated %d bytes at %Fp\n",   
         _msize( bufchar ), (void *)bufchar );  
   if( (bufchar = (char *)_expand( bufchar, 1024 )) == NULL )  
      printf( "Can't expand" );  
   else  
      printf( "Expanded block to %d bytes at %Fp\n",   
            _msize( bufchar ), (void *)bufchar );  
   // Free memory   
   free( bufchar );  
   exit( 0 );  
}  
```  
  
  **分配一个 512 元素的缓冲区**  
**在002C12BC分配 512 个字节**  
**在002C12BC扩大块为 1024 字节。**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [\_msize](../../c-runtime-library/reference/msize.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)