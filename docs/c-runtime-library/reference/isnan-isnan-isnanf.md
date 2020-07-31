---
title: isnan、_isnan、_isnanf
ms.date: 01/31/2019
api_name:
- _isnan
- _isnanf
- isnan
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
- _isnan
- isnan
- math/isnan
- math/_isnan
- math/_isnanf
- _isnanf
helpviewer_keywords:
- NAN (not a number)
- _isnan function
- IEEE floating-point representation
- Not a Number (NANs)
- isnan function
ms.assetid: 391fbc5b-89a4-4fba-997e-68f1131caf82
ms.openlocfilehash: 5aebacd15000e0202a26f600614900390c1ba7a4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213536"
---
# <a name="isnan-_isnan-_isnanf"></a>isnan、_isnan、_isnanf

测试浮点值是否不是一个数字 (NAN)。

## <a name="syntax"></a>语法

```C
int isnan(
   /* floating-point */ x
); /* C-only macro */

int _isnan(
   double x
);

int _isnanf(
   float x
); /* x64 only */

template <class T>
bool isnan(
   T x
) throw(); /* C++ only */
```

### <a name="parameters"></a>参数

*x*<br/>
要测试的浮点值。

## <a name="return-value"></a>返回值

在 C 中，如果参数*x*是 NAN，则**isnan**宏和 **_isnan**和 **_isnanf**函数返回非零值;否则，它们将返回0。

在 c + + **isnan**中， **`true`** 如果参数*x*是 NaN，则 isnan 模板函数将返回; 否则返回 **`false`** 。

## <a name="remarks"></a>备注

因为 NaN 值的比较结果不等于任何其他 NaN 值，所以您必须使用这些函数或宏之一来检测一个。 当无法以 IEEE-754 浮点格式为指定类型表示浮点运算的结果时，将生成 NaN。 有关如何为输出表示 NaN 的信息，请参阅[printf](printf-printf-l-wprintf-wprintf-l.md)。

在编译为 c + + 时，未定义**isnan**宏，而是定义**isnan**模板函数。 它的行为与宏的行为方式相同，但返回的是类型的值 **`bool`** 而不是整数。

**_Isnan**和 **_Isnanf**函数是 Microsoft 特定的。 仅当为 x64 编译时， **_isnanf**函数才可用。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头 (C)|必需的标头 (C++)|
|-------------|---------------------------|-------------------------------|
|**isnan**、 **_isnanf**|\<math.h>|\<math.h> 或 \<cmath>|
|**_isnan**|\<float.h>|\<float.h> 或 \<cfloat>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isfinite、_finite、_finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnormal](isnormal.md)<br/>
