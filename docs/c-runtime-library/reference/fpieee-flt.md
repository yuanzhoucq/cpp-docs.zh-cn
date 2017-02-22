---
title: "_fpieee_flt | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fpieee_flt"
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
  - "fpieee_flt"
  - "_fpieee_flt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fpieee_flt 函数"
  - "异常处理, 浮点"
  - "浮点异常处理"
  - "fpieee_flt 函数"
ms.assetid: 2bc4801e-0eed-4e73-b518-215da8cc9740
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _fpieee_flt
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为 IEEE 浮点异常调用一个用户自定义的陷阱处理程序。  
  
## 语法  
  
```  
int _fpieee_flt(   
   unsigned long excCode,  
   struct _EXCEPTION_POINTERS *excInfo,  
   int handler(_FPIEEE_RECORD *)   
);  
```  
  
#### 参数  
 `excCode`  
 异常代码。  
  
 `excInfo`  
 指向 windows NT 异常信息结构的指针。  
  
 `handler`  
 指向用户的 IEEE 陷阱处理程序实例的指针。  
  
## 返回值  
 `_fpieee_flt` 的返回值是通过 `handler` 返回的值。  同样，IEEE 筛选器实例可用于结构化异常处理 \(SEH\) 机制的 except 子句。  
  
## 备注  
 `_fpieee_flt` 函数为 IEEE 浮点异常调用用户自定义陷阱处理程序并提供所有相关的信息。  此实例服务为 SEH机制中的异常筛选器，如果需要将调用其自身的 IEEE 异常处理程序。  
  
 在 Fpieee.h 定义`_FPIEEE_RECORD` 结构，包含附属 IEEE 浮点异常的信息。  该结构通过 `_fpieee_flt` 传递到用户自定义陷阱处理程序中。  
  
|\_FPIEEE\_RECORD 字段|描述|  
|-------------------------|--------|  
|`unsigned int RoundingMode`, `unsigned int Precision`|在异常发生时，这些字段包含有关浮点环境的信息。|  
|`unsigned int Operation`|指示引发陷阱操作的类型。  如果该类型是一个对比 \(`_FpCodeCompare`\)，你能使用 `Result.Value` 字段中一个特殊 `_FPIEEE_COMPARE_RESULT` 值（在 pieee.h中定义）。  转换类型（`_FpCodeConvert`）指示陷阱发生在浮点转换操作中。  你可以查看 `Operand1` 和  `Result` 类型来决定试图要转换的类型。|  
|`_FPIEEE_VALUE Operand1`, `_FPIEEE_VALUE Operand2`, `_FPIEEE_VALUE Result`|这些结构指示提议的结果和操作的类型和值为：<br /><br /> `OperandValid` 标志指示响应的值是否有效。<br /><br /> `Format` 对应的值的数据类型。  即使对应的值无效，仍可能返回布局类型。<br /><br /> `Value` 结果或操作数的数据值。|  
|`_FPIEEE_EXCEPTION_FLAGS Cause`, `_FPIEEE_EXCEPTION_FLAGS Enable`, `_FPIEEE_EXCEPTION_FLAGS Status`|\_FPIEEE\_EXCEPTION\_FLAGS 包含每个浮点异常类型的1位字段。<br /><br /> 在这些字段和用于隐藏提供给 [\_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md) 的异常参数之间存在对应关系 。<br /><br /> 每个位的确切含义取决于上下文：<br /><br /> `Cause` 每套位指示提出的特定异常。<br /><br /> `Enable` 每套位指示特定异常目前被揭露。<br /><br /> `Status` 每套位指示特定异常目前待解决。  这包括没有提出的异常，因为它们被 `_controlfp` 隐藏了。|  
  
 当您启用它们时，待解决的未启用异常将引发。  当使用 `_fpieee_flt`  作为异常筛选器，将导致未定义的行为。  在浮点异常出现之前，请一直调用 [\_clearfp](../../c-runtime-library/reference/clear87-clearfp.md) 。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`_fpieee_flt`|\<fpieee.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fpieee.c  
// This program demonstrates the implementation of  
// a user-defined floating-point exception handler using the  
// _fpieee_flt function.  
  
#include <fpieee.h>  
#include <excpt.h>  
#include <float.h>  
#include <stddef.h>  
  
int fpieee_handler( _FPIEEE_RECORD * );  
  
int fpieee_handler( _FPIEEE_RECORD *pieee )  
{  
   // user-defined ieee trap handler routine:  
   // there is one handler for all   
   // IEEE exceptions  
  
   // Assume the user wants all invalid   
   // operations to return 0.  
  
   if ((pieee->Cause.InvalidOperation) &&   
       (pieee->Result.Format == _FpFormatFp32))   
   {  
        pieee->Result.Value.Fp32Value = 0.0F;  
  
        return EXCEPTION_CONTINUE_EXECUTION;  
   }  
   else  
      return EXCEPTION_EXECUTE_HANDLER;  
}  
  
#define _EXC_MASK    \  
    _EM_UNDERFLOW  + \  
    _EM_OVERFLOW   + \  
    _EM_ZERODIVIDE + \  
    _EM_INEXACT  
  
int main( void )  
{  
   // ...  
  
   __try {  
      // unmask invalid operation exception  
      _controlfp_s(NULL, _EXC_MASK, _MCW_EM);   
  
      // code that may generate   
      // fp exceptions goes here  
   }  
   __except ( _fpieee_flt( GetExceptionCode(),  
                GetExceptionInformation(),  
                fpieee_handler ) ){  
  
      // code that gets control   
  
      // if fpieee_handler returns  
      // EXCEPTION_EXECUTE_HANDLER goes here  
  
   }  
  
   // ...  
}  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [\_control87、\_controlfp、\_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)   
 [\_controlfp\_s](../../c-runtime-library/reference/controlfp-s.md)