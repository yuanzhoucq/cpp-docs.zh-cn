---
title: "_query_new_mode | Microsoft Docs"
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
  - "_query_new_mode"
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
  - "query_new_mode"
  - "_query_new_mode"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_query_new_mode 函数"
  - "处理程序模式"
  - "query_new_mode 函数"
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _query_new_mode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回整数指示新处理程序模式设置 `malloc`的 `_set_new_mode`。  
  
## 语法  
  
```  
  
      int _query_new_mode(  
   void   
);  
```  
  
## 返回值  
 返回当新处理程序模式，即 0 或 1，`malloc`。  返回值 1 意味着，分配内存失败，`malloc` 调用新处理程序实例；返回值 0意味着成功。  
  
## 备注  
 C\+\+ `_query_new_mode` 函数返回一新处理程序模式由 [malloc](../../c-runtime-library/reference/malloc.md)[\_set\_new\_mode](../../c-runtime-library/reference/set-new-mode.md) 的 C\+\+ 函数的整数。  新的处理程序模式指示，在失败时分配内存，`malloc` 是否就像 [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md) 设置的那样调用新的处理程序实例。  默认情况下，`malloc` 不调用发生故障的新处理程序。  您可重写此默认行为，这样一来，当 `_set_new_mode` 无法分配内存时， `malloc` 调用新的处理程序例程，其方式与出于相同原因的  运算符的操作相同。  有关更多信息，请参见位于 [删除运算符](../../misc/operator-delete-function.md) [新运算符](../../misc/operator-new-function.md)*的 C\+\+ 语言参考*和函数。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_query_new_mode`|\<new.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [\_query\_new\_handler](../../c-runtime-library/reference/query-new-handler.md)