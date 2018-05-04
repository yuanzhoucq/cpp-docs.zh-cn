---
title: norm、 normf、 norml |Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- norm
- normf
- norml
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
- norm
- normf
- norml
- complex/norm
- complex/normf
- complex/norml
dev_langs:
- C++
helpviewer_keywords:
- norm function
- normf function
- norml function
ms.assetid: 9786ecfe-0019-4553-b378-0af6c691e15c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 272f43a7b92c069da8fc4eda64a678ff38efd6ab
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="norm-normf-norml"></a>norm、normf、norml1

检索复数的平方量值。

## <a name="syntax"></a>语法

```C
double norm( _Dcomplex z );
float normf( _Fcomplex z );
long double norml( _Lcomplex z );
```

```cpp
float norm( _Fcomplex z );  // C++ only
long double norm( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>参数

*z*<br/>
一个复数。

## <a name="return-value"></a>返回值

平方的量*z*。

## <a name="remarks"></a>备注

由于 c + + 允许重载，你可以调用的重载**norm**采用 **_Fcomplex**或 **_Lcomplex**值，并返回**float**或**长双精度**值。 在 C 程序中， **norm**始终采用 **_Dcomplex**值并返回**double**值。

## <a name="requirements"></a>要求

|例程|C 标头|C++ 标头|
|-------------|--------------|------------------|
|**norm**， **normf**， **norml**|\<complex.h>|\<complex.h>|

**_Fcomplex**， **_Dcomplex**，和 **_Lcomplex**类型是特定于 Microsoft 的等效项的未实现的本机 C99 类型**float _Complex**， **double _Complex**，和**长双精度 _Complex**分别。  有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[creal、crealf、creall](creal-crealf-creall.md)<br/>
[cproj、cprojf、cprojl](cproj-cprojf-cprojl.md)<br/>
[conj、conjf、conjl](conj-conjf-conjl.md)<br/>
[cimag、cimagf、cimagl](cimag-cimagf-cimagl.md)<br/>
[carg、cargf、cargl](carg-cargf-cargl.md)<br/>
[cabs、cabsf、cabsl](cabs-cabsf-cabsl.md)<br/>
