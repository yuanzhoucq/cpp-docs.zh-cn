---
title: isinf
ms.date: 01/31/2019
f1_keywords:
- isinf
- math/isinf
helpviewer_keywords:
- isinf function
ms.openlocfilehash: be99970a0c7b152ba213eabd59b53a7503cd3c54
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703414"
---
# <a name="isinf"></a>isinf

确定浮点值是否为无穷大。

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

**isinf**返回非零值 (**true** c + + 代码中) 如果该参数*x*是正或负无穷大。 **isinf**返回 0 (**false** c + + 代码中) 是否自变量是有限或 NAN。 正常和次正常的浮点值被视为有限。

## <a name="remarks"></a>备注

**isinf**时编译为 C 和 c + + 作为编译时的内联模板函数是宏。

## <a name="requirements"></a>要求

|函数|必需的标头 (C)|必需的标头 (C++)|
|--------------|---------------------------|-------------------------------|
|**isinf**|\<math.h>|\<math.h> 或 \<cmath>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isfinite，_finite、 _finitef](finite-finitef.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
