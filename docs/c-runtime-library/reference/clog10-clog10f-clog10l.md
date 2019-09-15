---
title: clog10、clog10f、clog10l
ms.date: 11/04/2016
api_name:
- clog10
- clog10f
- clog10l
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
- clog10
- clog10f
- clog10l
- complex/clog10
- complex/clog10f
- complex/clog10l
helpviewer_keywords:
- clog10 function
- clog10f function
- clog10l function
ms.assetid: 2ddae00d-ef93-4441-add3-f4d58358401b
ms.openlocfilehash: a840494caf3c34f09d8c90970988e847be712cb4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939116"
---
# <a name="clog10-clog10f-clog10l"></a>clog10、clog10f、clog10l

检索复数的以 10 为底的对数。

## <a name="syntax"></a>语法

```C
_Dcomplex clog10( _Dcomplex z );
_Fcomplex clog10f( _Fcomplex z );
_Lcomplex clog10l( _Lcomplex z );
```

```cpp
_Fcomplex clog10( _Fcomplex z );  // C++ only
_Lcomplex clog10( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>参数

*z*<br/>
对数的底。

## <a name="return-value"></a>返回值

可能的返回值为：

|z 参数|返回值|
|-----------------|------------------|
|正|以 10 为底的 z 对数|
|零|- ∞|
|负数|NaN|
|NaN|NaN|
|+ ∞|+ ∞|

## <a name="remarks"></a>备注

由于C++允许重载，因此可以调用**clog10**的重载，该重载采用并返回 **_Fcomplex**和 **_Lcomplex**值。 在 C 程序中， **clog10**始终采用并返回 **_Dcomplex**值。

## <a name="requirements"></a>要求

|例程所返回的值|C 标头|C++ 标头|
|-------------|--------------|------------------|
|**clog10**、 **clog10f**、 **clogl**|\<complex.h>|\<ccomplex>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[cexp、cexpf、cexpl](cexp-cexpf-cexpl.md)<br/>
[cpow、cpowf、cpowl](cpow-cpowf-cpowl.md)<br/>
[clog、clogf、clogl](clog-clogf-clogl.md)<br/>
