---
title: "_heapchk | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_heapchk"
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
  - "_heapchk"
  - "heapchk"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_heapchk 函数"
  - "堆的一致性检查"
  - "调试 [CRT], 与堆有关的问题"
  - "heapchk 函数"
  - "堆, 检查一致性"
ms.assetid: 859619a5-1e35-4f02-9e09-11d9fa266ec0
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# _heapchk
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在堆上进行一致性检查。  
  
## 语法  
  
```  
int _heapchk( void );  
```  
  
## 返回值  
 `_heapchk` 返回在 Malloc.h 定义的以下整数清单常数之一。  
  
 `_HEAPBADBEGIN`  
 初始的头信息是错误的的或未能找到。  
  
 `_HEAPBADNODE`  
 错误节点已找到或堆已经损坏。  
  
 `_HEAPBADPTR`  
 在堆中指针是无效的。  
  
 `_HEAPEMPTY`  
 堆尚未初始化。  
  
 `_HEAPOK`  
 堆应该是一致的。  
  
 此外，如果发生错误，`_heapchk` 设置 `errno` 到 `ENOSYS`。  
  
## 备注  
 `_heapchk` 函数可通过检查堆最小的一致性帮助调试堆相关的问题。  如果操作系统不支持 `_heapchk`\(例如，Windows 98\)，则该函数返回 `_HEAPOK` 并设置`errno` 为 `ENOSYS`。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_heapchk`|\<malloc.h\>|\<errno.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_heapchk.c  
// This program checks the heap for  
// consistency and prints an appropriate message.  
  
#include <malloc.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int  heapstatus;  
   char *buffer;  
  
   // Allocate and deallocate some memory  
   if( (buffer = (char *)malloc( 100 )) != NULL )  
      free( buffer );  
  
   // Check heap status  
   heapstatus = _heapchk();  
   switch( heapstatus )  
   {  
   case _HEAPOK:  
      printf(" OK - heap is fine\n" );  
      break;  
   case _HEAPEMPTY:  
      printf(" OK - heap is empty\n" );  
      break;  
   case _HEAPBADBEGIN:  
      printf( "ERROR - bad start of heap\n" );  
      break;  
   case _HEAPBADNODE:  
      printf( "ERROR - bad node in heap\n" );  
      break;  
   }  
}  
```  
  
  **好的\-堆是好的**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [\_heapadd](../../c-runtime-library/heapadd.md)   
 [\_heapmin](../../c-runtime-library/reference/heapmin.md)   
 [\_heapset](../../c-runtime-library/heapset.md)   
 [\_heapwalk](../../c-runtime-library/reference/heapwalk.md)