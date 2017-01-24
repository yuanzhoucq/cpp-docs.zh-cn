---
title: "_heapset | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_heapset"
apilocation: 
  - "msvcr90.dll"
  - "msvcr80.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcrt.dll"
  - "msvcr120.dll"
  - "msvcr100.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_heapset"
  - "heapset"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_heapset 函数"
  - "检查堆"
  - "调试 [CRT], 与堆有关的问题"
  - "堆, 检查"
  - "heapset 函数"
ms.assetid: 9667eeb0-55bc-4c19-af5f-d1fd0a142b3c
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _heapset
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

检查堆是否符合最小一致性，并将可用项设置为指定值。  
  
> [!IMPORTANT]
>  此函数已过时。 从 Visual Studio 2015 开始，CRT 中不再提供此函数。  
  
## 语法  
  
```  
int _heapset(   
   unsigned int fill   
);  
```  
  
#### 参数  
 `fill`  
 填充字符。  
  
## 返回值  
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
  
## 备注  
 `_heapset` 函数表示可用内存位置或已经被无意覆盖的节点。  
  
 `_heapset` 检查堆上的最小一致性，然后将堆的可用项的每个字节设置为 `fill` 值。 此已知值表示堆的哪些内存位置包含可用节点，以及哪些位置包含为了释放内存而无意写入的数据。 如果操作系统不支持 `_heapset`（例如 Windows 98），此函数则返回 `_HEAPOK`，并将 `errno` 设置为 `ENOSYS`。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_heapset`|\<malloc.h\>|\<errno.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_heapset.c // This program checks the heap and // fills in free entries with the character 'Z'. #include <malloc.h> #include <stdio.h> #include <stdlib.h> int main( void ) { int heapstatus; char *buffer; if( (buffer = malloc( 1 )) == NULL ) // Make sure heap is exit( 0 );                        //    initialized heapstatus = _heapset( 'Z' );        // Fill in free entries switch( heapstatus ) { case _HEAPOK: printf( "OK - heap is fine\n" ); break; case _HEAPEMPTY: printf( "OK - heap is empty\n" ); break; case _HEAPBADBEGIN: printf( "ERROR - bad start of heap\n" ); break; case _HEAPBADNODE: printf( "ERROR - bad node in heap\n" ); break; } free( buffer ); }  
```  
  
```Output  
确定 - 堆没有问题  
```  
  
## .NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [内存分配](../c-runtime-library/memory-allocation.md)   
 [\_heapadd](../c-runtime-library/heapadd.md)   
 [\_heapchk](../c-runtime-library/reference/heapchk.md)   
 [\_heapmin](../c-runtime-library/reference/heapmin.md)   
 [\_heapwalk](../c-runtime-library/reference/heapwalk.md)