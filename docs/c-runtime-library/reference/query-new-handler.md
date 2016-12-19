---
title: "_query_new_handler | Microsoft Docs"
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
  - "_query_new_handler"
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
  - "_query_new_handler"
  - "query_new_handler"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_query_new_handler 函数"
  - "错误处理"
  - "处理程序例程"
  - "query_new_handler 函数"
ms.assetid: 9a84b5c3-fe33-4c01-83a0-be87dc3ec518
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _query_new_handler
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回当前新处理例程的地址。  
  
## 语法  
  
```  
  
      _PNH _query_new_handler(  
   void   
);  
```  
  
## 返回值  
 返回当前新处理例程的地址作为 `_set_new_handler` 的设置。  
  
## 备注  
 C\+\+ `_query_new_handler` 的函数返回当前异常处理函数的地址设置到 C\+\+ [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md) 函数。  `_set_new_handler` 用于指定异常处理函数，则 **new** 运算符无法分配内存。  有关更多信息，请参见以及在 *C\+\+ 语言参考的*[新建运算符](../../misc/operator-new-function.md) 和 [删除运算符](../../misc/operator-delete-function.md) 函数的讨论。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_query_new_handler`|\<new.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [free](../../c-runtime-library/reference/free.md)