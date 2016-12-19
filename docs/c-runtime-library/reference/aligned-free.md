---
title: "_aligned_free | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_aligned_free"
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
  - "aligned_free"
  - "_aligned_free"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_aligned_free 函数"
  - "aligned_free 函数"
ms.assetid: ed1ce952-cdfc-4682-85cc-f75d4101603d
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _aligned_free
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

释放由 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_offset\_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块。  
  
## 语法  
  
```  
void _aligned_free (  
   void *memblock  
);  
```  
  
#### 参数  
 `memblock`  
 由 `_aligned_malloc` 或 `_aligned_offset_malloc` 函数返回的存储区的指针。  
  
## 备注  
 `_aligned_free` 是标记的 `__declspec(noalias)`，这意味着函数可确保不修改全局变量。  有关详细信息，请参阅[noalias](../../cpp/noalias.md)。  
  
 此函数不会验证参数，不同于其他 \_aligned CRT 函数。  如果 `memblock` 是 `NULL` 指针，此函数不执行任何操作。  它不更改 `errno`，并不调用的无效参数处理程序。  如果由于在分配内存块之前不使用aligned函数导致函数错误，或者由于一些不可预见的灾难导致内存不对其，函数从 [\_RPT、\_RPTF、\_RPTW、\_RPTFW 宏](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)生成调试报告。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_aligned_free`|\<malloc.h\>|  
  
## 示例  
 有关详细信息，请参阅 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [数据对齐](../../c-runtime-library/data-alignment.md)