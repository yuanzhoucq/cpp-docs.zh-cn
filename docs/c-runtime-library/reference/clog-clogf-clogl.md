---
title: clog、clogf、clogl
ms.date: 11/04/2016
api_name:
- clog
- clogf
- clogl
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
- clog
- clogf
- clogl
- complex/clog
- complex/clogf
- complex/clogl
helpviewer_keywords:
- clog function
- clogf function
- clogl function
ms.assetid: 870b9b0b-6618-46f3-bfcf-da595cbd5e18
ms.openlocfilehash: 76ee6e4e81c275c8cbed0f74914521c0b44499bb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942922"
---
# <a name="clog-clogf-clogl"></a>clog、clogf、clogl

检索复数的自然对数，沿负实轴进行分支切割。

## <a name="syntax"></a>语法

```C
_Dcomplex clog(
   _Dcomplex z
);
_Fcomplex clog(
   _Fcomplex z
);  // C++ only
_Lcomplex clog(
   _Lcomplex z
);  // C++ only
_Fcomplex clogf(
   _Fcomplex z
);
_Lcomplex clogl(
   _Lcomplex z
);
```

### <a name="parameters"></a>参数

*z*<br/>
对数的底。

## <a name="return-value"></a>返回值

*Z*的自然对数。 沿实轴，并沿虚轴的间隔 [-i π，+ i π] 中，结果是无限的。

可能的返回值为：

|z 参数|返回值|
|-----------------|------------------|
|正|以 10 为底的 z 对数|
|零|- ∞|
|负数|NaN|
|NaN|NaN|
|+ ∞|+ ∞|

## <a name="remarks"></a>备注

由于C++允许重载，因此你可以调用采用并返回 **_Fcomplex**和 **_Lcomplex**值的**阻塞**的重载。 在 C 程序中，**堵塞**始终采用并返回一个 **_Dcomplex**值。

## <a name="requirements"></a>要求

|例程所返回的值|C 标头|C++ 标头|
|-------------|--------------|------------------|
|**阻塞**、 **clogf**、 **clogl**|\<complex.h>|\<ccomplex>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[cexp、cexpf、cexpl](cexp-cexpf-cexpl.md)<br/>
[cpow、cpowf、cpowl](cpow-cpowf-cpowl.md)<br/>
[clog10、clog10f、clog10l](clog10-clog10f-clog10l.md)<br/>
