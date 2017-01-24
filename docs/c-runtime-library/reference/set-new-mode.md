---
title: "_set_new_mode | Microsoft Docs"
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
  - "_set_new_mode"
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
  - "set_new_mode"
  - "_set_new_mode"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_set_new_mode 函数"
  - "处理程序模式"
  - "set_new_mode 函数"
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_new_mode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为`malloc`设置新处理程序模式。  
  
## 语法  
  
```  
int _set_new_mode(  
   int newhandlermode   
);  
```  
  
#### 参数  
 `newhandlermode`  
 `malloc`的新处理程序模式；有效值为 0 或 1。  
  
## 返回值  
 返回为`malloc`设置的前处理程序模式。  返回值 1 意味着，分配内存失败，`malloc` 之前调用新处理程序实例；返回值 0意味着成功。  如果 `newhandlermode` 参数不等于 0 或 1，则返回 \-1。\)  
  
## 备注  
 C\+\+ `_set_new_mode` 函数为[malloc](../../c-runtime-library/reference/malloc.md)设置新处理程序模式。  新的处理程序模式指示，在失败时，`malloc` 是否就像 [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md) 设置的那样调用新的处理程序实例。  默认情况下，`malloc` 不调用发生故障的新处理程序例程去分配内存。  您可重写此默认行为，这样一来，当 `malloc` 无法分配内存时， `malloc` 调用新的处理程序例程，其方式与出于相同原因的 `new` 运算符的操作相同。  有关更多信息，请参见 [new](../../cpp/new-operator-cpp.md)和[delete](../../cpp/delete-operator-cpp.md)*C\+\+ 语言参考*中的运算符。  重写默认值、调用:  
  
```  
_set_new_mode(1)  
```  
  
 在程序的早期，或链接到 Newmode.obj （请参阅 [链接选项](../../c-runtime-library/link-options.md)）。  
  
 此函数验证其参数。  如果`newhandlermode` 是 0 或 1 之外的任何数，函数调用参数无效处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许继续执行， **\_**`set_new_mode`返回\-1并设置`errno` 为`EINVAL`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_set_new_mode`|\<new.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [\_query\_new\_handler](../../c-runtime-library/reference/query-new-handler.md)   
 [\_query\_new\_mode](../../c-runtime-library/reference/query-new-mode.md)