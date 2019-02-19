---
title: isgreater、 isgreaterequal、 isless、 islessequal、 islessgreater、 isunordered
ms.date: 01/31/2019
f1_keywords:
- isgreater
- math/isgreater
- isgreaterequal
- math/isgreaterequal
- isless
- math/isless
- islessequal
- math/islessequal
- islessgreater
- math/islessgreater
- isunordered
- math/isunordered
helpviewer_keywords:
- isgreater function
- isgreaterequal function
- isless function
- islessequal function
- islessgreater function
- isunordered function
ms.openlocfilehash: 748360cae1dd0ee43645dee369c60c835246ed03
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703417"
---
# <a name="isgreater-isgreaterequal-isless-islessequal-islessgreater-isunordered"></a>isgreater、 isgreaterequal、 isless、 islessequal、 islessgreater、 isunordered

确定两个浮点值之间的排序关系。

## <a name="syntax"></a>语法

```C
int isgreater(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isgreaterequal(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isless(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int islessequal(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int islessgreater(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isunordered(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */
```

```C++
template <class FloatingType1, class FloatingType2>
inline bool isgreater(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isgreaterequal(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isless(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool islessequal(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool islessgreater(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isunordered(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */
```

### <a name="parameters"></a>参数

*x*， *y*<br/>
要比较的浮点值。

## <a name="return-value"></a>返回值

在所有比较中，相同的符号无穷大比较结果相等。 小于任何有限值或正无穷大，负无穷大。 正无穷大大于任何有限值或负无穷大。 零而不考虑登录相等。 Nan 不小于、 等于还是大于任何值，包括另一的 NaN。

当任一参数是 NaN，排序宏**isgreater**， **isgreaterequal**， **isless**，以及**islessequal**返回非零值如果，则值之间的指定排序关系*x*并*y*保持为 true。 如果一个或两个参数为 Nan 或排序关系为 false，这些宏将返回 0。 函数窗体的行为方式相同，但返回 **，则返回 true**或**false**。

**Islessgreater**宏返回一个非零值，如果这两种*x*并*y*不是 Nan，以及*x*是小于或大于*y*。 如果一个或两个参数为 Nan，或如果值相等，则返回 0。 函数窗体行为方式相同，但返回 **，则返回 true**或**false**。

**Isunordered**宏返回一个非零值，如果任一*x*， *y*，或两者都是 Nan。 否则返回 0。 函数窗体行为方式相同，但返回 **，则返回 true**或**false**。

## <a name="remarks"></a>备注

这些比较操作将作为宏时编译为 C，并作为内联模板函数在作为 c + + 编译时。

## <a name="requirements"></a>要求

|函数|必需的标头 (C)|必需的标头 (C++)|
|--------------|---------------------------|-------------------------------|
| **isgreater**， **isgreaterequal**， **isless**，<br/>**islessequal**， **islessgreater**， **isunordered** | \<math.h> | \<math.h> 或 \<cmath> |

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite，_finite、 _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
