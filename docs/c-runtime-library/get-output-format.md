---
title: "_get_output_format | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_get_output_format"
apilocation: 
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
  - "msvcrt.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
  - "msvcr110.dll"
apitype: "DLLExport"
f1_keywords: 
  - "get_output_format"
  - "_get_output_format"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_get_output_format 函数"
  - "get_output_format 函数"
  - "输出格式设置"
ms.assetid: 0ce42f3b-3479-41c4-bcbf-1d21f7ee37e7
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# _get_output_format
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取输出格式标志的当前值。  
  
> [!IMPORTANT]
>  此函数已过时。 从 Visual Studio 2015 开始，CRT 中不再提供此函数。  
  
## 语法  
  
```  
unsigned int _get_output_format();  
```  
  
## 返回值  
 输出格式标志的当前值。  
  
## 备注  
 输出格式标志控制格式化 I\/O 的功能。 当前标记有两个可能值：0 和 `_TWO_DIGIT_EXPONENT`。 如果设置了 `_TWO_DIGIT_EXPONENT`，则输出的浮点数的指数只有两位，除非指数的大小需要第三位数。 如果标志为零，浮点输出将显示指数的三个位，并在必要时使用零将值填充为三个位。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_get_output_format`|\<stdio.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [printf\_s、\_printf\_s\_l、wprintf\_s、\_wprintf\_s\_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)   
 [printf 类型字段字符](../c-runtime-library/printf-type-field-characters.md)   
 [\_set\_output\_format](../c-runtime-library/set-output-format.md)