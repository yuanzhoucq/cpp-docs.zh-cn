---
title: clog、clogf、clogl
ms.date: 11/04/2016
apiname:
- clog
- clogf
- clogl
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: fcbc9ba7984898d51f7a3d0beb5ef7c8b6d6892c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340630"
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

自然对数*z*。 结果为无限沿实轴并位于的间隔 [-i π，+ i π] 沿虚轴。

可能的返回值为：

|z 参数|返回值|
|-----------------|------------------|
|正|以 10 为底的 z 对数|
|零|- ∞|
|负数|NaN|
|NaN|NaN|
|+ ∞|+ ∞|

## <a name="remarks"></a>备注

因为C++允许重载，可以调用的重载**clog**采用并返回 **_Fcomplex**并 **_Lcomplex**的值。 在 C 程序中， **clog**始终采用并返回 **_Dcomplex**值。

## <a name="requirements"></a>要求

|例程所返回的值|C 标头|C++ 标头|
|-------------|--------------|------------------|
|**clog**， **clogf**， **clogl**|\<complex.h>|\<ccomplex>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[cexp、cexpf、cexpl](cexp-cexpf-cexpl.md)<br/>
[cpow、cpowf、cpowl](cpow-cpowf-cpowl.md)<br/>
[clog10、clog10f、clog10l](clog10-clog10f-clog10l.md)<br/>
