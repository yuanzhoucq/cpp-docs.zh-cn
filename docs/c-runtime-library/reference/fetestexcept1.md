---
title: fetestexcept
ms.date: 04/05/2018
api_name:
- fetestexcept
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
- fetestexcept
- fenv/fetestexcept
helpviewer_keywords:
- fetestexept function
ms.assetid: ca4dc43f-5573-440d-bc19-ead7571b13dc
ms.openlocfilehash: 61a68b4569d52b550da3fad12c077b82bb067fa9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941015"
---
# <a name="fetestexcept"></a>fetestexcept

确定当前设置了哪些指定的浮点异常状态标志。

## <a name="syntax"></a>语法

```C
int fetestexcept(
   int excepts
);
```

### <a name="parameters"></a>参数

*excepts*<br/>
要测试的浮点     状态标志的按位 OR。

## <a name="return-value"></a>返回值

如果成功，返回一个包含与当前设置的异常状态标志对应的浮点异常宏的按位 OR 的位掩码。 如果没有设置异常，则返回 0。

## <a name="remarks"></a>备注

使用 fetestexcept 函数来确定哪些异常由浮点运算引发。 使用*removed*参数来指定要测试的异常状态标志。 **Fetestexcept**函数使用\< *removed*中 v. > 中定义的这些异常宏和返回值：

|异常宏|描述|
|---------------------|-----------------|
|FE_DIVBYZERO|在早期的浮点运算中出现了奇点或极点错误；创建了无限值。|
|FE_INEXACT|此函数被强制舍入早期浮点运算的存储结果。|
|FE_INVALID|早期浮点运算中发生域错误。|
|FE_OVERFLOW|范围出错；早期浮点运算结果过大而无法表示。|
|FE_UNDERFLOW|早期的浮点运算结果因为过小而无法以完整的精度表示；创建了非常规值。|
|FE_ALLEXCEPT|所有受支持的浮点异常的按位 OR。|

指定的*removed*参数可以是0、支持的浮点异常宏之一，或者两个或多个宏的按位 or。 任何其他*removed*参数值的效果均为 undefined。

若要使用此函数，必须在调用前先使用 `#pragma fenv_access(on)` 指令关闭可能会阻止访问的浮点优化。 有关详细信息，请参阅 [fenv_access](../../preprocessor/fenv-access.md)。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**fetestexcept**|\<fenv.h>|\<cfenv>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feraiseexcept](feraiseexcept.md)<br/>
