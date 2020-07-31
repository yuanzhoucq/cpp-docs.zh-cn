---
title: fmod、fmodf、fmodl
ms.date: 4/2/2020
api_name:
- fmod
- fmodf
- fmodl
- _o_fmod
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fmod
- _fmodl
- fmodf
helpviewer_keywords:
- calculating floating-point remainders
- fmodf function
- fmodl function
- fmod function
- floating-point numbers, calculating remainders
ms.assetid: 6962d369-d11f-40b1-a6d7-6f67239f8a23
ms.openlocfilehash: 4fa3df46358932b8a62a6b8529baed4a5c9e5c49
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216968"
---
# <a name="fmod-fmodf-fmodl"></a>fmod、fmodf、fmodl

计算浮点余数。

## <a name="syntax"></a>语法

```C
double fmod(
   double x,
   double y
);
float fmod(
   float x,
   float y
);  // C++ only
long double fmod(
   long double x,
   long double y
);  // C++ only
float fmodf(
   float x,
   float y
);
long double fmodl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>参数

*x*、 *y*<br/>
浮点值。

## <a name="return-value"></a>返回值

**fmod**返回*x*  /  *y*的浮点余数。 如果*y*的值为0.0，则**fmod**将返回静默的 NaN。 有关**printf**系列的 quiet NaN 表示形式的信息，请参阅[printf](printf-printf-l-wprintf-wprintf-l.md)。

## <a name="remarks"></a>备注

**Fmod**函数计算*x*y 的浮点余数*f*  /  *y* ，这是*x*  =  *i* \* *y*  +  *f*，其中*i*是整数， *f*与*x*具有相同的符号， *f*的绝对值小于*y*的绝对值。

C + + 允许重载，因此你可以调用**fmod**的重载，该重载采用和返回 **`float`** 和 **`long double`** 值。 在 C 程序中， **fmod**始终采用两个 **`double`** 参数，并返回 **`double`** 。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fmod**、 **fmodf**、 **fmodl**|\<math.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_fmod.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = fmod( w, x );
   printf( "The remainder of %.2f / %.2f is %f\n", w, x, z );
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[ceil、ceilf、ceill](ceil-ceilf-ceill.md)<br/>
[fabs、fabsf、fabsl](fabs-fabsf-fabsl.md)<br/>
[floor、floorf、floorl](floor-floorf-floorl.md)<br/>
[_CIfmod](../../c-runtime-library/cifmod.md)<br/>
