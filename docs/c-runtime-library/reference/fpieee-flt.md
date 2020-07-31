---
title: _fpieee_flt
ms.date: 04/05/2018
api_name:
- _fpieee_flt
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fpieee_flt
- _fpieee_flt
helpviewer_keywords:
- _fpieee_flt function
- exception handling, floating-point
- floating-point exception handling
- fpieee_flt function
ms.assetid: 2bc4801e-0eed-4e73-b518-215da8cc9740
ms.openlocfilehash: c6a77dcba06b58191781900d4e24202c6335cfb8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213562"
---
# <a name="_fpieee_flt"></a>_fpieee_flt

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

*函数*<br/>
指向用户的 IEEE 陷阱处理程序例程的指针。

## <a name="return-value"></a>返回值

**_Fpieee_flt**的返回值是*处理程序*返回的值。 同样的，IEEE 筛选器例程可用于结构化异常处理 (SEH) 机制的 except 子句。

## <a name="remarks"></a>备注

**_Fpieee_flt**函数为 IEEE 浮点异常调用用户定义的陷阱处理程序，并为其提供所有相关信息。 此例程用作 SEH 机制中的异常筛选器，它会在必要时调用您的 IEEE 异常处理程序。

Fpieee.h 中定义的 **_FPIEEE_RECORD**结构包含有关 IEEE 浮点异常的信息。 此结构通过 **_fpieee_flt**传递给用户定义的陷阱处理程序。

|_FPIEEE_RECORD 字段|描述|
|----------------------------|-----------------|
|**Roundingmode.awayfromzero**<br/>**精度**|这些 **`unsigned int`** 字段包含发生异常时浮点环境的相关信息。|
|**操作**|此 **`unsigned int`** 字段指示导致陷阱的操作的类型。 如果类型是比较（**_FpCodeCompare**），则可以在 "结果" 的 "**值**" 字段中提供一个特殊的 **_FPIEEE_COMPARE_RESULT**值（在 fpieee.h 中定义）。 转换类型（**_FpCodeConvert**）指示在执行浮点转换操作期间出现了陷阱。 您可以查看**Operand1**和**结果**类型以确定要尝试的转换类型。|
|**Operand1**<br/>**Operand2**<br/>**结果**|这些 **_FPIEEE_VALUE**结构指示建议的结果和操作数的类型和值。 每个结构都包含以下字段：<br /><br /> **OperandValid** -指示响应值是否有效的标志。<br />相应值的**格式**-数据类型。 可返回格式类型，即使相应的值无效。<br />**值**-结果或操作数的数据值。|
|**原因**<br/>**启用**<br/>**Status**|对于每种类型的浮点异常 **_FPIEEE_EXCEPTION_FLAGS**包含一个位字段。 这些字段和用于屏蔽提供给 [_controlfp](control87-controlfp-control87-2.md) 的异常的自变量之间存在对应关系。 每个位的确切含义取决于上下文：<br /><br /> **原因**-每个设置位指示已引发的特定异常。<br />**启用**-每个设置位指示特定异常当前已取消屏蔽。<br />**状态**-每个设置位指示特定异常当前处于挂起状态。 这包括因 **_controlfp**屏蔽而未引发的异常。|

已禁用的挂起的异常在您启用它们之后将会引发。 当使用 **_fpieee_flt**作为异常筛选器时，这可能会导致未定义的行为。 在启用浮点异常之前，始终调用 [_clearfp](clear87-clearfp.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_fpieee_flt**|\<fpieee.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[_control87、_controlfp \_ _control87_2](control87-controlfp-control87-2.md)<br/>
[_controlfp_s](controlfp-s.md)<br/>
