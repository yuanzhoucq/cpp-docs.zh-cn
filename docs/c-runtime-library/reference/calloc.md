---
title: "calloc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "calloc"
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
  - "calloc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "内存分配, 数组"
  - "calloc 函数"
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# calloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

分配内存中数组与初始化的元素为 0。  
  
## 语法  
  
```  
void *calloc(   
   size_t num,  
   size_t size   
);  
```  
  
#### 参数  
 `num`  
 元素的数目  
  
 `size`  
 每个元素字节长度。  
  
## 返回值  
 `calloc` 返回指向分配的空间。  返回值指向保证适当地存储任何类型的对象的对齐的存储空间。  若要获得指向类型的指针而不是 `void`，请对返回值进行类型转换。  
  
## 备注  
 `calloc` 函数分配数组的 `num` 元素，每个存储区长度 `size` 字节。  每个元素初始化为 0。  
  
 如果内存分配失败，或者请求的内存数量超过 `_HEAP_MAXREQ`，那么 `calloc` 设置 `errno` 为 `ENOMEM`。  有关这和其他错误代码的信息，请参阅 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 `calloc` 调用 `malloc` 以使用 [\_set\_new\_mode](../../c-runtime-library/reference/set-new-mode.md) C\+\+ 函数将新处理程序模式。  新的处理程序模式指示，在失败时，`malloc` 是否就像 [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md) 设置的那样调用新的处理程序实例。  默认情况下，`malloc` 不调用发生故障的新处理程序例程去分配内存。  您可重写此默认行为，这样一来，当 `calloc` 无法分配内存时， `malloc` 调用新的处理程序例程，其方式与出于相同原因的 `new` 运算符的操作相同。  重写默认值、调用  
  
```  
_set_new_mode(1)  
```  
  
 在您程序的早期，或链接到 NEWMODE.OBJ（请参阅 [链接选项](../../c-runtime-library/link-options.md)）。  
  
 当应用程序与调试版本的 C 运行时库连接时，`calloc` 解析为 [\_calloc\_dbg](../../c-runtime-library/reference/calloc-dbg.md)。  有关在调试过程中如何托管堆的详细信息，请参阅  [The CRT Debug Heap](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
 `calloc` 标记为 `__declspec(noalias)` 和 `__declspec(restrict)`这意味着函数保证不修改全局变量，和返回的指针不用做别名。  有关更多信息，请参见 [没有别名](../../cpp/noalias.md) 和 [限制](../../cpp/restrict.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`calloc`|\<stdlib.h\> 和 \<malloc.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_calloc.c  
// This program uses calloc to allocate space for  
// 40 long integers. It initializes each element to zero.  
  
#include <stdio.h>  
#include <malloc.h>  
  
int main( void )  
{  
   long *buffer;  
  
   buffer = (long *)calloc( 40, sizeof( long ) );  
   if( buffer != NULL )  
      printf( "Allocated 40 long integers\n" );  
   else  
      printf( "Can't allocate memory\n" );  
   free( buffer );  
}  
```  
  
  **分配长为40的整数**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)