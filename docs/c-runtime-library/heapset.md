---
title: "_heapset |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _heapset
apilocation:
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _heapset
- heapset
dev_langs: C++
helpviewer_keywords:
- checking heap
- heapset function
- heaps, checking
- debugging [CRT], heap-related problems
- _heapset function
ms.assetid: 9667eeb0-55bc-4c19-af5f-d1fd0a142b3c
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e9449637887a05c64179c6b9d31712c8becfa87b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="heapset"></a>_heapset
检查堆是否符合最小一致性，并将可用项设置为指定值。  
  
> [!IMPORTANT]
>  此函数已过时。 从 Visual Studio 2015 开始，CRT 中不再提供此函数。  
  
## <a name="syntax"></a>语法  
  
```  
int _heapset(   
   unsigned int fill   
);  
```  
  
#### <a name="parameters"></a>参数  
 `fill`  
 填充字符。  
  
## <a name="return-value"></a>返回值  
 `_heapset` 返回 Malloc.h 中定义的以下整数清单常量之一。  
  
 `_HEAPBADBEGIN`  
 初始标头信息无效或未找到。  
  
 `_HEAPBADNODE`  
 堆已损坏或找到错误节点。  
  
 `_HEAPEMPTY`  
 堆未初始化。  
  
 `_HEAPOK`  
 堆看起来一致。  
  
 此外，如果出现错误，`_heapset` 会将 `errno` 设置为 `ENOSYS`。  
  
## <a name="remarks"></a>备注  
 `_heapset` 函数表示可用内存位置或已经被无意覆盖的节点。  
  
 `_heapset` 检查堆上的最小一致性，然后将堆的可用项的每个字节设置为 `fill` 值。 此已知值表示堆的哪些内存位置包含可用节点，以及哪些位置包含为了释放内存而无意写入的数据。 如果操作系统不支持 `_heapset`（例如 Windows 98），此函数则返回 `_HEAPOK`，并将 `errno` 设置为 `ENOSYS`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|可选标头|  
|-------------|---------------------|---------------------|  
|`_heapset`|\<malloc.h>|\<errno.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_heapset.c  
// This program checks the heap and  
// fills in free entries with the character 'Z'.  
  
#include <malloc.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   int heapstatus;  
   char *buffer;  
  
   if( (buffer = malloc( 1 )) == NULL ) // Make sure heap is   
      exit( 0 );                        //    initialized       
   heapstatus = _heapset( 'Z' );        // Fill in free entries   
   switch( heapstatus )  
   {  
   case _HEAPOK:  
      printf( "OK - heap is fine\n" );  
      break;  
   case _HEAPEMPTY:  
      printf( "OK - heap is empty\n" );  
      break;  
   case _HEAPBADBEGIN:  
      printf( "ERROR - bad start of heap\n" );  
      break;  
   case _HEAPBADNODE:  
      printf( "ERROR - bad node in heap\n" );  
      break;  
   }  
   free( buffer );  
}  
```  
  
```Output  
OK - heap is fine  
```  
  
## <a name="see-also"></a>另请参阅  
 [内存分配](../c-runtime-library/memory-allocation.md)   
 [_heapadd](../c-runtime-library/heapadd.md)   
 [_heapchk](../c-runtime-library/reference/heapchk.md)   
 [_heapmin](../c-runtime-library/reference/heapmin.md)   
 [_heapwalk](../c-runtime-library/reference/heapwalk.md)