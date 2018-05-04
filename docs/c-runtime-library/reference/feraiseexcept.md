---
title: feraiseexcept | Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- feraiseexcept function
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfd60612c92f8e3ff542fd22bbf5b4a01f7b7365
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
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

**Feraiseexcept**函数尝试引发由指定的浮点异常*excepts*。   **Feraiseexcept**函数支持中定义这些异常宏\<v.h >:

|异常宏|描述|
|---------------------|-----------------|
|FE_DIVBYZERO|在早期的浮点运算中出现了奇点或极点错误；创建了无限值。|
|FE_INEXACT|此函数被强制舍入早期浮点运算的存储结果。|
|FE_INVALID|早期浮点运算中发生域错误。|
|FE_OVERFLOW|范围出错；早期浮点运算结果过大而无法表示。|
|FE_UNDERFLOW|早期的浮点运算结果因为过小而无法以完整的精度表示；创建了非常规值。|
|FE_ALLEXCEPT|所有受支持的浮点异常的按位 OR。|

*Excepts*参数可能为零，一个异常宏的值，或按位或两个或多个受支持的异常宏。 如果一个指定的异常宏是 FE_OVERFLOW 或 FE_UNDERFLOW，FE_INEXACT 异常可能会引发副作用。

若要使用此函数，必须在调用前先使用 `#pragma fenv_access(on)` 指令关闭可能会阻止访问的浮点优化。 有关详细信息，请参阅 [fenv_access](../../preprocessor/fenv-access.md)。

**Microsoft 专用：**中指定的异常*excepts* FE_INVALID，顺序引发 FE_DIVBYZERO、 FE_OVERFLOW、 FE_UNDERFLOW、 FE_INEXACT。 但是，FE_INEXACT 可能引发 FE_OVERFLOW 或 FE_UNDERFLOW 发出时，即使中未指定*excepts*。 **结束 Microsoft 专用**

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
