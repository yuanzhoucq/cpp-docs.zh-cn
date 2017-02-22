---
title: "_recalloc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_recalloc"
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
  - "_recalloc"
  - "recalloc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_recalloc 函数"
  - "recalloc 函数"
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# _recalloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`realloc` 和 `calloc` 的组合。  分配内存中数组并初始化其元素为 0。  
  
## 语法  
  
```  
void *_recalloc(   
   void *memblock  
   size_t num,  
   size_t size   
);  
```  
  
#### 参数  
 `memblock`  
 以前分配的内存块的指针。  
  
 `num`  
 元素的数目  
  
 `size`  
 每个元素字节长度。  
  
## 返回值  
 `_recalloc` 返回一`void`指针用来重分配的 \(可能移动）内存块。  
  
 如果不展开块的足够的可用内存的特定范围，则块仍保持不变，并且，则返回 `NULL`。  
  
 如果需求的尺寸为0，由`memblock`指向的块被释放，返回值为`NULL`，`memblock`指向一个被释放的块。  
  
 返回值指向保证适当地存储任何类型的对象的对齐的存储空间。  若要获得指向类型的指针而不是 `void`，请对返回值进行类型转换。  
  
## 备注  
 `recalloc` 功能将一个分配的存储区的大小。  `memblock` 指向存储区的开头的参数的位置。  如果 `memblock` 是 `NULL`，\_`recalloc` 相同的行为。[calloc](../../c-runtime-library/reference/calloc.md) 并分配 `num` \* `size` 字节新块。  每个元素初始化为 0。  如果 `memblock` 不是 `NULL`，它应该是对的上一调用返回的指针为 `calloc`、[malloc](../../c-runtime-library/reference/malloc.md)或 [realloc](../../c-runtime-library/reference/realloc.md)。  
  
 由于新块可以在新的内存位置，\_返回的指针`recalloc` 不一定是指针传递 `memblock` 参数。  
  
 如果内存分配失败，或者请求的内存数量超过 `_HEAP_MAXREQ`，那么 `_recalloc` 设置 `errno` 为 `ENOMEM`。  有关这和其他错误代码的信息，请参阅 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 `recalloc` 调用 `realloc` 以使用 [\_set\_new\_mode](../../c-runtime-library/reference/set-new-mode.md) C\+\+ 函数将新处理程序模式。  新的处理程序模式指示，在失败时，`realloc` 是否就像 [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md) 设置的那样调用新的处理程序实例。  默认情况下，`realloc` 不调用发生故障的新处理程序例程去分配内存。  您可重写此默认行为，这样一来，当 `recalloc` 无法分配内存时， `realloc` 调用新的处理程序例程，其方式与出于相同原因的 `new` 运算符的操作相同。  重写默认值、调用  
  
```  
_set_new_mode(1)  
```  
  
 在您程序的早期，或链接到 NEWMODE.OBJ。  
  
 当应用程序与调试版本的 C 运行时库连接时，`recalloc` 解析为[\_recalloc\_dbg](../../c-runtime-library/reference/recalloc-dbg.md)。  有关在调试过程中如何托管堆的详细信息，请参阅  [The CRT Debug Heap](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
 `_recalloc` 标记为 `__declspec(noalias)` 和 `__declspec(restrict)`这意味着函数保证不修改全局变量，和返回的指针不用做别名。  有关更多信息，请参见 [没有别名](../../cpp/noalias.md) 和 [限制](../../cpp/restrict.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_recalloc`|\<stdlib.h\> 和 \<malloc.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [\_recalloc\_dbg](../../c-runtime-library/reference/recalloc-dbg.md)   
 [\_aligned\_recalloc](../../c-runtime-library/reference/aligned-recalloc.md)   
 [\_aligned\_offset\_recalloc](../../c-runtime-library/reference/aligned-offset-recalloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [链接选项](../../c-runtime-library/link-options.md)