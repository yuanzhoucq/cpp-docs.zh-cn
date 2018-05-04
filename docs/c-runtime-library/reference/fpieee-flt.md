---
title: _fpieee_flt | Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _fpieee_flt
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
dev_langs:
- C++
helpviewer_keywords:
- _fpieee_flt function
- exception handling, floating-point
- floating-point exception handling
- fpieee_flt function
ms.assetid: 2bc4801e-0eed-4e73-b518-215da8cc9740
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 412eef6e3999c18901792643fa7a57ce18d19520
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="fpieeeflt"></a>_fpieee_flt

为 IEEE 浮点异常调用用户定义的陷阱处理程序。

## <a name="syntax"></a>语法

```C
int _fpieee_flt(
   unsigned long excCode,
   struct _EXCEPTION_POINTERS *excInfo,
   int handler(_FPIEEE_RECORD *)
);
```

### <a name="parameters"></a>参数

*excCode*<br/>
异常代码。

*excInfo*<br/>
指向 Windows NT 异常信息结构的指针。

*处理程序*<br/>
指向用户的 IEEE 陷阱处理程序例程的指针。

## <a name="return-value"></a>返回值

返回值 **_fpieee_flt**是通过返回的值*处理程序*。 同样的，IEEE 筛选器例程可用于结构化异常处理 (SEH) 机制的 except 子句。

## <a name="remarks"></a>备注

**_Fpieee_flt**函数调用的用户定义的陷阱处理程序 IEEE 浮点异常，并为其提供所有相关信息。 此例程用作 SEH 机制中的异常筛选器，它会在必要时调用您的 IEEE 异常处理程序。

**_FPIEEE_RECORD** Fpieee.h 中定义的结构包含有关 IEEE 浮点异常的信息。 此结构传递到用户定义的陷阱处理程序通过 **_fpieee_flt**。

|_FPIEEE_RECORD 字段|描述|
|----------------------------|-----------------|
|**RoundingMode**<br/>**精度**|这些**无符号** **int**字段包含有关浮点环境信息时出现异常。|
|**操作**|这**无符号** **int**字段指示导致陷阱的操作的类型。 如果类型为比较 (**_FpCodeCompare**)，你可以提供一个特殊 **_FPIEEE_COMPARE_RESULT**中值 （如 Fpieee.h 中定义） **Result.Value**字段。 转换类型 (**_FpCodeConvert**) 指示浮点转换操作期间出现了陷阱。 你可以查看**Operand1**和**结果**类型以确定要尝试的转换的类型。|
|**operand1**<br/>**operand2**<br/>**结果**|这些 **_FPIEEE_VALUE**结构指示的类型和建议的结果和操作数的值。 每个结构包含以下字段：<br /><br /> **OperandValid** -标志，指示响应值是否有效。<br />**格式**-的对应值的数据类型。 可返回格式类型，即使相应的值无效。<br />**值**的结果或操作数的数据值。|
|**原因**<br/>**启用**<br/>**状态**|**_Fpieee_exception_flags 为**包含一个 1 位字段，每种类型的浮点异常。 这些字段和用于屏蔽提供给 [_controlfp](control87-controlfp-control87-2.md) 的异常的自变量之间存在对应关系。 每个位的确切含义取决于上下文：<br /><br /> **可能的原因**-每个设置位指示已引发的特定异常。<br />**启用**-每个设置位指示特定异常是当前未屏蔽。<br />**状态**-每个设置位指示特定异常当前处于挂起状态。 这包括因为它们已屏蔽而未引发的异常 **_controlfp**。|

已禁用的挂起的异常在您启用它们之后将会引发。 这可能导致未定义的行为，使用时 **_fpieee_flt**作为异常筛选器。 在启用浮点异常之前，始终调用 [_clearfp](clear87-clearfp.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_fpieee_flt**|\<fpieee.h 1>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
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

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[_control87、_controlfp、\__control87_2](control87-controlfp-control87-2.md)<br/>
[_controlfp_s](controlfp-s.md)<br/>
