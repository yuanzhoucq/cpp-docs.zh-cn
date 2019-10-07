---
title: casin、casinf、casinl
ms.date: 11/04/2016
api_name:
- casin
- casinf
- casinl
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
- casin
- casinf
- casinl
- complex/casin
- complex/casinf
- complex/casinl
helpviewer_keywords:
- casin function
- casinf function
- casinl function
ms.assetid: b75d1455-7b1e-43b0-bd46-c530be190be9
ms.openlocfilehash: e3ae944c9808fd0fc6e8d1ffbd02da2a69454cc6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943384"
---
# <a name="casin-casinf-casinl"></a>casin、casinf、casinl

检索复数的反正弦，其中分支切口沿实轴的间隔 [-1，+ 1] 外。

## <a name="syntax"></a>语法

```C
_Dcomplex casin(
   _Dcomplex z
);
_Fcomplex casin(
   _Fcomplex z
);  // C++ only
_Lcomplex casin(
   _Lcomplex z
);  // C++ only
_Fcomplex casinf(
   _Fcomplex z
);
_Lcomplex casinl(
   _Lcomplex z
);
```

### <a name="parameters"></a>参数

*z*<br/>
表示角度的复数（以弧度为单位）。

## <a name="return-value"></a>返回值

*Z*的反正弦（以弧度表示）。 沿虚部未绑定结果，并沿实轴的间隔 [-π/2，+ π/2] 中。

## <a name="remarks"></a>备注

由于C++允许重载，因此可以调用**casin**的重载，该重载采用并返回 **_Fcomplex**和 **_Lcomplex**值。 在 C 程序中， **casin**始终采用并返回 **_Dcomplex**值。

## <a name="requirements"></a>要求

|例程所返回的值|C 标头|C++ 标头|
|-------------|--------------|------------------|
|**casin**、 **casinf**、 **casinl**|\<complex.h>|\<ccomplex>|

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
[ccos、ccosf、ccosl](ccos-ccosf-ccosl.md)<br/>
[csqrt、csqrtf、csqrtl](csqrt-csqrtf-csqrtl.md)<br/>
