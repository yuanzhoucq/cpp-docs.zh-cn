---
title: feraiseexcept
ms.date: 04/05/2018
apiname:
- feraiseexcept
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
apitype: HeaderDef
f1_keywords:
- feraiseexcept
- fenv/feraiseexcept
helpviewer_keywords:
- feraiseexcept function
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
ms.openlocfilehash: 581dd4026a20ce7221945c5815af3ae102f132fa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532244"
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

*除*<br/>
要引发的浮点异常。

## <a name="return-value"></a>返回值

如果指定的所有异常都成功引发，则返回 0。

## <a name="remarks"></a>备注

**Feraiseexcept**函数尝试引发由指定的浮点异常*除*。   **Feraiseexcept**函数支持中定义的这些异常宏\<fenv.h >:

|异常宏|描述|
|---------------------|-----------------|
|FE_DIVBYZERO|在早期的浮点运算中出现了奇点或极点错误；创建了无限值。|
|FE_INEXACT|此函数被强制舍入早期浮点运算的存储结果。|
|FE_INVALID|早期浮点运算中发生域错误。|
|FE_OVERFLOW|范围出错；早期浮点运算结果过大而无法表示。|
|FE_UNDERFLOW|早期的浮点运算结果因为过小而无法以完整的精度表示；创建了非常规值。|
|FE_ALLEXCEPT|所有受支持的浮点异常的按位 OR。|

*除*参数可能为零、 一个异常宏值，或按位 OR 的两个或多个受支持的异常宏。 如果一个指定的异常宏是 FE_OVERFLOW 或 FE_UNDERFLOW，FE_INEXACT 异常可能会引发副作用。

若要使用此函数，必须在调用前先使用 `#pragma fenv_access(on)` 指令关闭可能会阻止访问的浮点优化。 有关详细信息，请参阅 [fenv_access](../../preprocessor/fenv-access.md)。

**Microsoft 专用：** 中指定的异常*除*引发顺序 FE_INVALID、 FE_DIVBYZERO、 FE_OVERFLOW、 FE_UNDERFLOW、 FE_INEXACT。 但是，可能引发 FE_INEXACT 当引发 FE_OVERFLOW 或 FE_UNDERFLOW 时，即使在未指定*除*。 **结束 Microsoft 专用**

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|*feraiseexcept*|\<fenv.h>|\<cfenv>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
