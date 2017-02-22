---
title: "_set_printf_count_output | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_printf_count_output"
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
  - "set_printf_count_output"
  - "_set_printf_count_output"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "%n 格式"
  - "_set_printf_count_output 函数"
  - "set_printf_count_output 函数"
ms.assetid: d8259ec5-764e-42d0-9169-72172e95163b
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# _set_printf_count_output
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

启用或禁用 `%n` 格式 \- 函数族的支持。[printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)的。  
  
## 语法  
  
```  
int _set_printf_count_output(  
   int enable  
);  
```  
  
#### 参数  
 `enable`  
 通过 `%n` 支持的非零值，0 支持禁用 `%n`。  
  
## 属性值\/返回值  
 `%n` 支持的状态。调用此函数的前面：非零 `%n`，则支持，0，则禁用。  
  
## 备注  
 由于安全原因，`%n` 格式说明符。支持 `printf` 及其所有变量默认情况下禁用。  如果 `%n` 位于 `printf` 格式规范遇到，默认行为是调用的参数无效处理程序如下所述。[参数验证](../../c-runtime-library/parameter-validation.md) 调用具有非零的参数 `_set_printf_count_output` 将导致 `printf`。介绍 `%n` 的函数族。如 [printf 类型字段字符](../../c-runtime-library/printf-type-field-characters.md)所述。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_set_printf_count_output`|\<stdio.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_set_printf_count_output.c  
#include <stdio.h>  
  
int main()  
{  
   int e;  
   int i;  
   e = _set_printf_count_output( 1 );  
   printf( "%%n support was %sabled.\n",  
        e ? "en" : "dis" );  
   printf( "%%n support is now %sabled.\n",  
        _get_printf_count_output() ? "en" : "dis" );  
   printf( "12345%n6789\n", &i ); // %n format should set i to 5  
   printf( "i = %d\n", i );  
}  
```  
  
## Output  
  
```  
%n support was disabled.  
%n support is now enabled.  
123456789  
i = 5  
```  
  
## .NET Framework Equivalent  
 不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [\_get\_printf\_count\_output](../../c-runtime-library/reference/get-printf-count-output.md)