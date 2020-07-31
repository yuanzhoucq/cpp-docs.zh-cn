---
title: isinf
ms.date: 01/31/2019
f1_keywords:
- isinf
- math/isinf
helpviewer_keywords:
- isinf function
ms.openlocfilehash: 7366f340477bf1bb50ebe1e53bcec1f3e16e0863
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234089"
---
# <a name="isinf"></a>isinf

确定浮点值是否为无穷值。

## <a name="syntax"></a>语法

```C
int isinf(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isinf(
   FloatingType x
) throw(); /* C++-only template function */
```

### <a name="parameters"></a>参数

*x*<br/>
要测试的浮点值。

## <a name="return-value"></a>返回值

**isinf** **`true`** 如果参数*x*为正无穷或负无穷，则 isinf 返回非零值（在 c + + 代码中为）。 **isinf** **`false`** 如果参数是有限的或 NAN，则 isinf 将返回0（在 c + + 代码中）。 正常和次正常浮点值都被视为有限值。

## <a name="remarks"></a>备注

在编译为 C 时， **isinf**是一个宏，在编译为 c + + 时为内联模板函数。

## <a name="requirements"></a>要求

|函数|必需的标头 (C)|必需的标头 (C++)|
|--------------|---------------------------|-------------------------------|
|**isinf**|\<math.h>|\<math.h> 或 \<cmath>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isfinite、_finite、_finitef](finite-finitef.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
