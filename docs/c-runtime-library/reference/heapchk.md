---
title: "_heapchk | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _heapchk
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _heapchk
- heapchk
dev_langs: C++
helpviewer_keywords:
- debugging [CRT], heap-related problems
- consistency checking of heaps
- heapchk function
- heaps, checking consistency
- _heapchk function
ms.assetid: 859619a5-1e35-4f02-9e09-11d9fa266ec0
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 790d887009137ccc9115484b2ace57302c94d851
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="heapchk"></a>_heapchk
在堆上运行一致性检查。  
  
## <a name="syntax"></a>语法  
  
```  
int _heapchk( void );  
```  
  
## <a name="return-value"></a>返回值  
 `_heapchk` 返回 Malloc.h 中定义的以下整数清单常量之一。  
  
 `_HEAPBADBEGIN`  
 初始头信息已损坏，或找不到。  
  
 `_HEAPBADNODE`  
 找到错误节点，或堆已损坏。  
  
 `_HEAPBADPTR`  
 指向堆的指针无效。  
  
 `_HEAPEMPTY`  
 尚未初始化堆。  
  
 `_HEAPOK`  
 堆看起来一致。  
  
 此外，如果出现错误，`_heapchk` 会将 `errno` 设置为 `ENOSYS`。  
  
## <a name="remarks"></a>备注  
 `_heapchk` 函数通过检查堆的最小一致性来帮助调试与堆有关的问题。 如果操作系统不支持 `_heapchk`（例如 Windows 98），此函数则返回 `_HEAPOK`，并将 `errno` 设置为 `ENOSYS`。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|可选标头|  
|-------------|---------------------|---------------------|  
|`_heapchk`|\<malloc.h>|\<errno.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
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
  
```Output  
OK - heap is fine  
```  
  
## <a name="see-also"></a>请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [_heapadd](../../c-runtime-library/heapadd.md)   
 [_heapmin](../../c-runtime-library/reference/heapmin.md)   
 [_heapset](../../c-runtime-library/heapset.md)   
 [_heapwalk](../../c-runtime-library/reference/heapwalk.md)