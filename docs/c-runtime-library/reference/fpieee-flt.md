---
title: "_fpieee_flt | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _fpieee_flt
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fpieee_flt
- _fpieee_flt
dev_langs: C++
helpviewer_keywords:
- _fpieee_flt function
- exception handling, floating-point
- floating-point exception handling
- fpieee_flt function
ms.assetid: 2bc4801e-0eed-4e73-b518-215da8cc9740
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 63472ad24a981a39a20e6c0cabb82f7c96d1e59e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fpieeeflt"></a>_fpieee_flt
为 IEEE 浮点异常调用用户定义的陷阱处理程序。  
  
## <a name="syntax"></a>语法  
  
```  
int _fpieee_flt(   
   unsigned long excCode,  
   struct _EXCEPTION_POINTERS *excInfo,  
   int handler(_FPIEEE_RECORD *)   
);  
```  
  
#### <a name="parameters"></a>参数  
 `excCode`  
 异常代码。  
  
 `excInfo`  
 指向 Windows NT 异常信息结构的指针。  
  
 `handler`  
 指向用户的 IEEE 陷阱处理程序例程的指针。  
  
## <a name="return-value"></a>返回值  
 `_fpieee_flt` 的返回值是由 `handler` 返回的值。 同样的，IEEE 筛选器例程可用于结构化异常处理 (SEH) 机制的 except 子句。  
  
## <a name="remarks"></a>备注  
 `_fpieee_flt` 函数为 IEEE 浮点异常调用用户定义的陷阱处理程序并为其提供所有相关信息。 此例程用作 SEH 机制中的异常筛选器，它会在必要时调用您的 IEEE 异常处理程序。  
  
 Fpieee.h 中定义的 `_FPIEEE_RECORD` 结构包含有关 IEEE 浮点异常的信息。 该结构通过 `_fpieee_flt` 传递到用户定义的陷阱处理程序中。  
  
|_FPIEEE_RECORD 字段|描述|  
|----------------------------|-----------------|  
|`unsigned int RoundingMode`, `unsigned int Precision`|这些字段包含发生异常时浮点环境的相关信息。|  
|`unsigned int Operation`|指示导致陷阱的操作的类型。 如果该类型是一个比较 (`_FpCodeCompare`)，您可以提供 `_FPIEEE_COMPARE_RESULT` 字段中某个特殊的 `Result.Value` 值（如 Fpieee.h 中所定义）。 转换类型 (`_FpCodeConvert`) 指示浮点转换操作期间出现了陷阱。 可以查看 `Operand1` 和 `Result` 类型来决定要尝试的转换类型。|  
|`_FPIEEE_VALUE Operand1`, `_FPIEEE_VALUE Operand2`, `_FPIEEE_VALUE Result`|这些结构指示建议的结果和操作数的类型和值：<br /><br /> `OperandValid` 指示响应值是否有效的标志。<br /><br /> `Format` 对应值的数据类型。 可返回格式类型，即使相应的值无效。<br /><br /> `Value` 结果或操作数的数据值。|  
|`_FPIEEE_EXCEPTION_FLAGS Cause`, `_FPIEEE_EXCEPTION_FLAGS Enable`, `_FPIEEE_EXCEPTION_FLAGS Status`|_FPIEEE_EXCEPTION_FLAGS 为每个浮点异常类型包含一个 1 位字段。<br /><br /> 这些字段和用于屏蔽提供给 [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md) 的异常的自变量之间存在对应关系。<br /><br /> 每个位的确切含义取决于上下文：<br /><br /> `Cause` 每个设置位指示已引发的特定异常。<br /><br /> `Enable` 每个设置位指示特定异常当前已取消屏蔽。<br /><br /> `Status` 每个设置位指示特定异常当前处于挂起状态。 这包括因被 `_controlfp` 屏蔽而未引发的异常。|  
  
 已禁用的挂起的异常在您启用它们之后将会引发。 这在将 `_fpieee_flt` 用作异常筛选器时会导致未定义的行为。 在启用浮点异常之前，始终调用 [_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)。  
  
## <a name="requirements"></a>惠?  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`_fpieee_flt`|\<fpieee.h 1>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
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
  
## <a name="see-also"></a>请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [_control87、_controlfp、\__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)   
 [_controlfp_s](../../c-runtime-library/reference/controlfp-s.md)