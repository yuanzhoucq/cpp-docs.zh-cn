---
title: "_heapmin | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_heapmin"
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
  - "_heapmin"
  - "heapmin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_heapmin 函数"
  - "堆内存"
  - "heapmin 函数"
  - "堆, 释放未使用的内存"
  - "内存, 释放"
  - "将堆最小化"
ms.assetid: c0bccdf6-2d14-4d7b-a7ff-d6a17bdb410f
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _heapmin
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

释放操作系统未使用的堆内存。  
  
## 语法  
  
```  
int _heapmin( void );  
```  
  
## 返回值  
 如果成功，则 `_heapmin` 返回 0;否则，函数返回 \- 1 并将 `errno` 设置为 `ENOSYS`。  
  
 有关这些属性和其他的更多信息返回代码示例，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `_heapmin` 函数通过释放操作系统未使用的堆内存。  如果操作系统不支持 `_heapmin`\(例如，Windows 98\)，则该函数返回\-1， 并设置`errno` 为`ENOSYS` 。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_heapmin`|\<malloc.h\>|\<errno.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [\_heapadd](../../c-runtime-library/heapadd.md)   
 [\_heapchk](../../c-runtime-library/reference/heapchk.md)   
 [\_heapset](../../c-runtime-library/heapset.md)   
 [\_heapwalk](../../c-runtime-library/reference/heapwalk.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)