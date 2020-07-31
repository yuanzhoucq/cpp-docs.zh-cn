---
title: isnormal
ms.date: 01/31/2019
f1_keywords:
- isnormal
- math/isnormal
helpviewer_keywords:
- isnormal function
ms.openlocfilehash: 2e12cabb57f2e51c08b4d93af33dae85164d016b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213523"
---
# <a name="isnormal"></a>isnormal

确定浮点值是否为正常值。

## <a name="syntax"></a>语法

```C
int isnormal(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isnormal(
   FloatingType x
) throw(); /* C++-only function template */
```

### <a name="parameters"></a>参数

*x*<br/>
要测试的浮点值。

## <a name="return-value"></a>返回值

**isnormal** **`true`** 如果参数*x*既不是零、次正常、无限大，也不是 NaN，则 isnormal 返回非零值（在 c + + 代码中）。 否则， **isnormal**将返回0（ **`false`** 在 c + + 代码中）。

## <a name="remarks"></a>备注

在编译为 C 时， **isnormal**是宏，而在编译为 c + + 时则是内联函数模板。

## <a name="requirements"></a>要求

|函数|必需的标头 (C)|必需的标头 (C++)|
|--------------|---------------------------|-------------------------------|
|**isnormal**|\<math.h>|\<math.h> 或 \<cmath>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite、_finite、_finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
