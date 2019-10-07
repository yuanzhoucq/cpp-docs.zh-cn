---
title: csqrt、csqrtf、csqrtl
ms.date: 11/04/2016
api_name:
- csqrt
- csqrtf
- csqrtl
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- csqrt
- csqrtf
- csqrtl
- complex/csqrt
- complex/csqrtf
- complex/csqrtl
helpviewer_keywords:
- csqrt function
- csqrtf function
- csqrtl function
ms.assetid: b65f086b-0f55-4622-a7a3-4e79d9c9c05c
ms.openlocfilehash: 1afc79f0fba9663ec5fbb0a556da52c3a1c55ca6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941990"
---
# <a name="csqrt-csqrtf-csqrtl"></a>csqrt、csqrtf、csqrtl

检索复数的平方根，沿负实轴进行分支切割。

## <a name="syntax"></a>语法

```C
_Dcomplex csqrt(
   _Dcomplex z
);
_Fcomplex csqrt(
   _Fcomplex z
);  // C++ only
_Lcomplex csqrt(
   _Lcomplex z
);  // C++ only
_Fcomplex csqrtf(
   _Fcomplex z
);
_Lcomplex csqrtl(
   _Lcomplex z
);
```

### <a name="parameters"></a>参数

*z*<br/>
一个复数。

## <a name="return-value"></a>返回值

*Z*的平方根。 结果在右半面中。

|输入|SEH 异常|**_matherr**异常|
|-----------|-------------------|--------------------------|
|± QNAN，IND|无|_DOMAIN|
|- ∞|无|_DOMAIN|

## <a name="remarks"></a>备注

由于C++允许重载，因此可以调用**csqrt**的重载，该重载采用并返回 **_Fcomplex**和 **_Lcomplex**值。 在 C 程序中， **csqrt**始终采用并返回 **_Dcomplex**值。

## <a name="requirements"></a>要求

|例程所返回的值|C 标头|C++ 标头|
|-------------|--------------|------------------|
|**csqrt**、 **csqrtf**、 **csqrtl**|\<complex.h>|\<ccomplex>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[catanh、catanhf、catanhl](catanh-catanhf-catanhl.md)<br/>
[ctanh、ctanhf、ctanhl](ctanh-ctanhf-ctanhl.md)<br/>
[catan、catanf、catanl](catan-catanf-catanl.md)<br/>
[csinh、csinhf、csinhl](csinh-csinhf-csinhl.md)<br/>
[casinh、casinhf、casinhl](casinh-casinhf-casinhl.md)<br/>
[ccosh、ccoshf、ccoshl](ccosh-ccoshf-ccoshl.md)<br/>
[cacosh、cacoshf、cacoshl](cacosh-cacoshf-cacoshl.md)<br/>
[cacos、cacosf、cacosl](cacos-cacosf-cacosl.md)<br/>
[ctan、ctanf、ctanl](ctan-ctanf-ctanl.md)<br/>
[csin、csinf、csinl](csin-csinf-csinl.md)<br/>
[casin、casinf、casinl](casin-casinf-casinl.md)<br/>
[ccos、ccosf、ccosl](ccos-ccosf-ccosl.md)<br/>
