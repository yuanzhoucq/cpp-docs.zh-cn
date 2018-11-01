---
title: nan、nanf、nanl
ms.date: 94/05/2018
apiname:
- nanf
- nan
- nanl
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
- nan
- nanl
- nanf
helpviewer_keywords:
- nan function
- nanf function
- nanl function
ms.assetid: 790e9158-80ab-43e0-8f5a-096198553fd9
ms.openlocfilehash: 22b0e14094a0b6f0f3571c4d7551552210177a22
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610257"
---
# <a name="nan-nanf-nanl"></a>nan、nanf、nanl

返回 quiet NaN 值。

## <a name="syntax"></a>语法

```C
double nan( const char* input );
float nanf( const char* input );
long double nanl( const char* input );
```

### <a name="parameters"></a>参数

*input*<br/>
字符串值。

## <a name="return-value"></a>返回值

**Nan**函数将返回 quiet NaN 值。

## <a name="remarks"></a>备注

**Nan**函数返回 quiet (非 signalling) NaN 对应的浮点值。 *输入*值将被忽略。 有关如何表示用于输出的 NaN 的信息，请参阅 [printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**nan**， **nanf**， **nanl**|\<math.h>|\<cmath> 或 \<math.h>|

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[_finite、_finitef](finite-finitef.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
