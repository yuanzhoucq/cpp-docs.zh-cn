---
title: feraiseexcept
ms.date: 04/05/2018
api_name:
- feraiseexcept
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
api_type:
- HeaderDef
f1_keywords:
- feraiseexcept
- fenv/feraiseexcept
helpviewer_keywords:
- feraiseexcept function
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
ms.openlocfilehash: 07c8a79e0a9569db80607e1ec1e16cd4b502783c
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857822"
---
# <a name="feraiseexcept"></a>feraiseexcept

引发指定的浮点异常。

## <a name="syntax"></a>语法

```C
int feraiseexcept(
   int excepts
);
```

### <a name="parameters"></a>参数

*excepts*<br/>
要引发的浮点异常。

## <a name="return-value"></a>返回值

如果指定的所有异常都成功引发，则返回 0。

## <a name="remarks"></a>备注

**Feraiseexcept**函数尝试引发*removed*指定的浮点异常。   **Feraiseexcept**函数支持在 \<v. > 中定义的这些异常宏：

|异常宏|描述|
|---------------------|-----------------|
|FE_DIVBYZERO|在早期的浮点运算中出现了奇点或极点错误；创建了无限值。|
|FE_INEXACT|此函数被强制舍入早期浮点运算的存储结果。|
|FE_INVALID|早期浮点运算中发生域错误。|
|FE_OVERFLOW|范围出错；早期浮点运算结果过大而无法表示。|
|FE_UNDERFLOW|早期的浮点运算结果因为过小而无法以完整的精度表示；创建了非常规值。|
|FE_ALLEXCEPT|所有受支持的浮点异常的按位 OR。|

*Removed*参数可以为零、一个异常宏值，或者两个或多个受支持的异常宏的按位 or。 如果一个指定的异常宏是 FE_OVERFLOW 或 FE_UNDERFLOW，FE_INEXACT 异常可能会引发副作用。

若要使用此函数，必须在调用前先使用 `#pragma fenv_access(on)` 指令关闭可能会阻止访问的浮点优化。 有关详细信息，请参阅 [fenv_access](../../preprocessor/fenv-access.md)。

**特定于 Microsoft 的：** 在*removed*中指定的异常将按 FE_INVALID、FE_DIVBYZERO、FE_OVERFLOW、FE_UNDERFLOW、FE_INEXACT 的顺序引发。 但是，在引发 FE_OVERFLOW 或 FE_UNDERFLOW 时，即使未在*removed*中指定，也可以引发 FE_INEXACT。

## <a name="requirements"></a>需求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|*feraiseexcept*|\<fenv.h>|\<cfenv>|

有关其他兼容性信息，请参见 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
