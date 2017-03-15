---
title: "_get_heap_handle | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_get_heap_handle"
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
  - "_get_heap_handle"
  - "get_heap_handle"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "堆函数"
  - "内存分配，堆内存"
  - "_get_heap_handle 函数"
  - "get_heap_handle 函数"
ms.assetid: a4d05049-8528-494a-8281-a470d1e1115c
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# _get_heap_handle
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回 C 运行时系统所用堆的句柄。  
  
## 语法  
  
```  
intptr_t _get_heap_handle( void );  
```  
  
## 返回值  
 返回 C 运行时系统所用 Win32 堆的句柄。  
  
## 备注  
 如果想要针对 CRT 堆调用 [HeapSetInformation](http://msdn.microsoft.com/library/windows/desktop/aa366705) 并启用低分片堆，请使用此函数。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_get_heap_handle`|\<malloc.h\>|  
  
 有关兼容性的详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_get_heap_handle.cpp  
// compile with: /MT  
#include <windows.h>  
#include <malloc.h>  
#include <stdio.h>  
  
int main(void)  
{  
    intptr_t hCrtHeap = _get_heap_handle();  
    ULONG ulEnableLFH = 2;  
    if (HeapSetInformation((PVOID)hCrtHeap,  
                           HeapCompatibilityInformation,  
                           &ulEnableLFH, sizeof(ulEnableLFH)))  
        puts("Enabling Low Fragmentation Heap succeeded");  
    else  
        puts("Enabling Low Fragmentation Heap failed");  
    return 0;  
}  
```  
  
## 请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)