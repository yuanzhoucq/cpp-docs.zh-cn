---
title: isfinite，_finite、 _finitef
ms.date: 01/31/2019
apiname:
- _finite
- _finitef
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
- isfinite
- finite
- _finite
- _finitef
- math/isfinite
- math/_finite
- math/_finitef
- float/_finite
helpviewer_keywords:
- finite function
- _finite function
- _finitef function
ms.assetid: 5a7d7ca7-befb-4e1f-831d-28713c6eb805
ms.openlocfilehash: 1be5aa204a7db3054a49c2e05a8fd77b12ae8a3d
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702747"
---
# <a name="isfinite-finite-finitef"></a>isfinite，_finite、 _finitef

确定浮点值是否是有限的。

## <a name="syntax"></a>语法

```C
int isfinite(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isfinite(
   FloatingType x
) throw(); /* C++-only template function */

int _finite(
   double x
);

int _finitef(
   float x
); /* x64 and ARM/ARM64 only */
```

### <a name="parameters"></a>参数

*x*<br/>
要测试的浮点值。

## <a name="return-value"></a>返回值

`isfinite`宏并`_finite`并`_finitef`函数返回一个非零值，如果*x*可以正常或次正常有限值。 它们将返回 0，如果参数为无限或为 NaN。 C + + 内联模板函数`isfinite`行为方式相同，但会返回**true**或**false**。

## <a name="remarks"></a>备注

`isfinite` 是一个宏时编译为 C 和内联模板函数在作为 c + + 编译时。 `_finite`和`_finitef`函数是特定于 Microsoft 的。 `_finitef` 函数仅在编译 x86、ARM、或 ARM64 平台时可用。

## <a name="requirements"></a>要求

|函数|必需的标头 (C)|必需的标头 (C++)|
|--------------|---------------------------|-------------------------------|
|`_finite`|\<float.h 1> 或 \<math.h 1>|\<float.h 1>、\<math.h 1>、\<cfloat 1> 或 \<cmath 1>|
|`isfinite`， `_finitef`|\<math.h>|\<math.h> 或 \<cmath>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isinf](isinf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
