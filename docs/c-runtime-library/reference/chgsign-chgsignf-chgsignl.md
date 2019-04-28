---
title: _chgsign、_chgsignf、_chgsignl
ms.date: 04/05/2018
apiname:
- _chgsignl
- _chgsign
- _chgsignf
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
- _chgsignf
- chgsign
- _chgsignl
- _chgsign
helpviewer_keywords:
- _chgsignl function
- _chgsignf function
- chgsign function
- _chgsign function
ms.assetid: a6646f8e-213d-4564-8617-f43bc66f989f
ms.openlocfilehash: dad60b1fec4d402d340eeb4c87028975ef09e3ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340232"
---
# <a name="chgsign-chgsignf-chgsignl"></a>_chgsign、_chgsignf、_chgsignl

颠倒浮点型参数的符号。

## <a name="syntax"></a>语法

```C
double _chgsign(
   double x
);
float _chgsignf(
   float x
);
long double _chgsignl(
   long double x
);
```

### <a name="parameters"></a>参数

*x*<br/>
要更改的浮点值。

## <a name="return-value"></a>返回值

**_Chgsign**函数返回一个值，它等于浮点型参数*x*，但符号颠倒。 无错误返回。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_chgsign**|\<float.h>|
|**_chgsignf**, **_chgsignl**|\<math.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[fabs、fabsf、fabsl](fabs-fabsf-fabsl.md)<br/>
[copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl](copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)<br/>
