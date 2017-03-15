---
title: "_get_invalid_parameter_handler _get_thread_local_invalid_parameter_handler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_get_invalid_parameter_handler"
  - "_get_thread_local_invalid_parameter_handler"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_get_invalid_parameter_handler"
  - "stdlib/_get_invalid_parameter_handler"
  - "_get_thread_local_invalid_parameter_handler"
  - "stdlib/_get_thread_local_invalid_parameter_handler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_get_thread_local_invalid_parameter_handler 函数"
  - "_get_invalid_parameter_handler 函数"
ms.assetid: a176da0e-38ca-4d99-92bb-b0e2b8072f53
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# _get_invalid_parameter_handler _get_thread_local_invalid_parameter_handler
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取在 CRT 检测到无效的参数时，将调用的函数。  
  
## 语法  
  
```  
_invalid_parameter_handler _get_invalid_parameter_handler(void);  
_invalid_parameter_handler _get_thread_local_invalid_parameter_handler(void);  
```  
  
## 返回值  
 指向当前设置的指针无效参数处理程序函数或如果已设置的任何一个 null 指针。  
  
## 备注  
 `_get_invalid_parameter_handler` 函数获取当前设置全局无效参数处理程序。 如果没有全局无效参数处理程序已设置，则返回 null 指针。 同样， `_get_thread_local_invalid_parameter_handler` 获取当前线程的线程本地无效参数处理调用时，该线程或 null 指针，如果没有处理程序已设置。 有关如何设置全局和线程本地无效参数处理程序的信息，请参阅 [\_set\_invalid\_parameter\_handler \_set\_thread\_local\_invalid\_parameter\_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)。  
  
 返回的无效参数处理程序函数指针具有以下类型︰  
  
```c  
typedef void (__cdecl* _invalid_parameter_handler)(  
    wchar_t const*,  
    wchar_t const*,  
    wchar_t const*,   
    unsigned int,  
    uintptr_t  
    );  
```  
  
 无效参数处理程序的详细信息，请参阅中的原型 [\_set\_invalid\_parameter\_handler \_set\_thread\_local\_invalid\_parameter\_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_get_invalid_parameter_handler`, `_get_thread_local_invalid_parameter_handler`|C: \< stdlib.h \><br /><br /> C \+ \+: \< cstdlib \> 或 \< stdlib.h \>|  
  
 `_get_invalid_parameter_handler` 和 `_get_thread_local_invalid_parameter_handler` 函数是 Microsoft 专用。 有关兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [\_set\_invalid\_parameter\_handler \_set\_thread\_local\_invalid\_parameter\_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)   
 [CRT 函数的安全增强版本](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)