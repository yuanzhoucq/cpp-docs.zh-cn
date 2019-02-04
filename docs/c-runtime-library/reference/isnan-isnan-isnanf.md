---
title: isnan、_isnan、_isnanf
ms.date: 01/31/2019
apiname:
- _isnan
- _isnanf
- isnan
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
ms.openlocfilehash: 8a907dd33803cebd7bc5d71789834d115333b6a0
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703085"
---
# <a name="isnan-isnan-isnanf"></a>isnan、_isnan、_isnanf

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

在 C 中， **isnan**宏和 **_isnan**并 **_isnanf**函数返回一个非零值，如果自变量*x*是 NAN; 否则为它们返回 0。

C + + **isnan**模板函数返回**true**如果参数*x*是 NaN; 否则它将返回**false**。

## <a name="remarks"></a>备注

由于 NaN 值不相等，为任何其他 NaN 值，必须使用下列某个函数或宏来检测一个。 不能指定类型的 IEEE 754 浮点格式表示浮点运算的结果，则会生成 NaN。 有关如何表示用于输出的 NaN 的信息，请参阅[printf](printf-printf-l-wprintf-wprintf-l.md)。

在作为 c + +，编译时**isnan**未定义宏，和一个**isnan**改为定义模板函数。 它的行为是相同的宏，但返回类型的值**bool**而不是整数。

**_Isnan**并 **_isnanf**函数是特定于 Microsoft 的。 **_Isnanf**函数才编译 x64 时可用。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头 (C)|必需的标头 (C++)|
|-------------|---------------------------|-------------------------------|
|**isnan**， **_isnanf**|\<math.h>|\<math.h> 或 \<cmath>|
|**_isnan**|\<float.h>|\<float.h> 或 \<cfloat>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isfinite，_finite、 _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnormal](isnormal.md)<br/>
