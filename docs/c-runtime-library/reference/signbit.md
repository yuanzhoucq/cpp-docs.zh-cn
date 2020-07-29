---
title: signbit
ms.date: 01/31/2019
f1_keywords:
- signbit
- math/signbit
helpviewer_keywords:
- signbit function
ms.openlocfilehash: 7f8399c16d2abc70a50740b0629bc5d9b3a1f067
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216734"
---
# <a name="signbit"></a>signbit

确定浮点值是否为负。

## <a name="syntax"></a>语法

```C
int signbit(
   /* floating-point */ x
); /* C-only macro */

inline bool signbit(
   float x
) throw(); /* C++-only overloaded function */

inline bool signbit(
   double x
) throw(); /* C++-only overloaded function */

inline bool signbit(
   long double x
) throw(); /* C++-only overloaded function */
```

### <a name="parameters"></a>参数

*x*<br/>
要测试的浮点值。

## <a name="return-value"></a>返回值

**signbit** **`true`** 如果参数*x*为负或负无穷，则 signbit 返回非零值（在 c + + 中为）。 **`false`** 如果参数为非负数、正无穷或 NAN，则返回0（在 c + + 中为）。

## <a name="remarks"></a>备注

在编译为 C 时， **signbit**是宏，而在编译为 c + + 时则是重载内联函数。

## <a name="requirements"></a>要求

|函数|必需的标头 (C)|必需的标头 (C++)|
|--------------|---------------------------|-------------------------------|
|**signbit**|\<math.h>|\<math.h> 或 \<cmath>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite、_finite、_finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
