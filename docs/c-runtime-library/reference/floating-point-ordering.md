---
title: isgreater、isgreaterequal、isless、islessequal、islessgreater、isunordered
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
ms.openlocfilehash: 907b26f4e1824d7ef5c7c1a36b4e4d8ccb74c978
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220712"
---
# <a name="isgreater-isgreaterequal-isless-islessequal-islessgreater-isunordered"></a>isgreater、isgreaterequal、isless、islessequal、islessgreater、isunordered

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

*x*、 *y*<br/>
要比较的浮点值。

## <a name="return-value"></a>返回值

在所有比较中，相同符号比较的无穷大等于相等。 负无穷小于任何有限值或正无穷。 正无穷大于任何有限值或负无穷。 无论符号如何，0都是相等的。 Nan 不小于、等于或大于任何值（包括另一个 NaN）。

如果这两个参数都不是 NaN，则如果*x*和*y*之间的指定排序关系为 true，则顺序宏**isgreater**、 **isgreaterequal**、 **isless**和**islessequal**将返回非零值。 如果其中一个参数或两个参数均为 Nan，则这些宏将返回 0; 如果排序关系为 false，则返回。 函数窗体的行为方式相同，但返回 **`true`** 或 **`false`** 。

如果*x*和*y*不是 nan 并且*x*小于或大于*y*，则**islessgreater**宏将返回一个非零值。 如果其中一个或两个参数均为 Nan，则返回 0; 如果值相等，则返回。 函数形式的行为方式相同，但返回 **`true`** 或 **`false`** 。

如果*x*、 *y*或两者均为 nan，则**isunordered**宏将返回一个非零值。 否则，返回 0。 函数形式的行为方式相同，但返回 **`true`** 或 **`false`** 。

## <a name="remarks"></a>备注

当编译为 C 时，这些比较运算作为宏实现，在编译为 c + + 时作为内联模板函数实现。

## <a name="requirements"></a>要求

|函数|必需的标头 (C)|必需的标头 (C++)|
|--------------|---------------------------|-------------------------------|
| **isgreater**、 **isgreaterequal**、 **isless**、<br/>**islessequal**、 **islessgreater**、 **isunordered** | \<math.h> | \<math.h> 或 \<cmath> |

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite、_finite、_finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
