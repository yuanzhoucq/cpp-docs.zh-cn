---
title: "_get_printf_count_output | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_get_printf_count_output"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "get_printf_count_output"
  - "_get_printf_count_output"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "%n 格式"
  - "_get_printf_count_output 函数"
  - "get_printf_count_output 函数"
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# _get_printf_count_output
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指明是 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)\- 函数族支持 `%n` 格式。  
  
## 语法  
  
```  
int _get_printf_count_output();  
```  
  
## 返回值  
 非零，如果`%n`是支持的，0，如果`%n`是不支持的。  
  
## 备注  
 如果 `%n` 是不支持的\(默认\)，遇到`%n`的格式字符串的任何 `printf` 函数将调用无效参数处理程序如下所述[参数验证](../../c-runtime-library/parameter-validation.md) 如果`%n` 支持是有效的\(参见 [\_set\_printf\_count\_output](../../c-runtime-library/reference/set-printf-count-output.md)\) 然后`%n` 将运行按照 [printf 类型字段字符](../../c-runtime-library/printf-type-field-characters.md)所述。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_get_printf_count_output`|\<stdio.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参见 [\_set\_printf\_count\_output](../../c-runtime-library/reference/set-printf-count-output.md)中的示例。  
  
## .NET Framework Equivalent  
 不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。