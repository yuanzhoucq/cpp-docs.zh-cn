---
title: "_heapadd | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_heapadd"
apilocation: 
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr80.dll"
  - "msvcrt.dll"
  - "msvcr110.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "heapadd"
  - "_heapadd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_heapadd 函数"
  - "heapadd 函数"
  - "堆, 添加内存"
  - "内存, 添加到堆"
ms.assetid: 4d691fe2-2763-49f4-afb1-62738b7cd3ff
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _heapadd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将内存添加到堆。  
  
> [!IMPORTANT]
>  此函数已过时。 从 Visual Studio 2015 开始，CRT 中不再提供此函数。  
  
## 语法  
  
```  
int _heapadd(   
   void *memblock,  
   size_t size   
);  
```  
  
#### 参数  
 `memblock`  
 指向堆内存的指针。  
  
 `size`  
 要添加的内存大小，以字节为单位。  
  
## 返回值  
 如果成功，`_heapadd` 会返回 0；否则，此函数会返回 –1，并将 `errno` 设置为 `ENOSYS`。  
  
 有关于此代码以及其他返回代码的详细信息，请参阅 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 从 Visual C\+\+ 4.0 版开始，基础堆结构已移至 C 运行时库，以支持新的调试功能。 因此，基于 Win32 API 的任何平台上不再支持 `_heapadd`。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_heapadd`|\<malloc.h\>|\<errno.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [内存分配](../c-runtime-library/memory-allocation.md)   
 [free](../c-runtime-library/reference/free.md)   
 [\_heapchk](../c-runtime-library/reference/heapchk.md)   
 [\_heapmin](../c-runtime-library/reference/heapmin.md)   
 [\_heapset](../c-runtime-library/heapset.md)   
 [\_heapwalk](../c-runtime-library/reference/heapwalk.md)   
 [malloc](../c-runtime-library/reference/malloc.md)   
 [realloc](../c-runtime-library/reference/realloc.md)