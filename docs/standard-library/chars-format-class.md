---
title: chars_format 枚举
ms.date: 07/22/2020
f1_keywords:
- charconv/std::chars_format
helpviewer_keywords:
- std::chars_format
ms.openlocfilehash: 4c1d495c943be02b66d52d1986a783b29a8009c5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230177"
---
# <a name="chars_format-enum"></a>chars_format 枚举

与库一起使用 [\<charconv>](charconv.md) ，为基元数值转换指定浮点格式。

## <a name="syntax"></a>语法

```cpp
enum class chars_format {
    scientific = unspecified,
    fixed = unspecified,
    hex = unspecified,
    general = fixed | scientific
};
```

### <a name="members"></a>成员

|元素|描述|
|-|-|
| `scientific` | 导致 `from_chars()` 预期并分析指数。 它类似于 `'e'` `printf()` 格式说明符，格式说明符用于科学记数法，例如`"1.729e+01"` |
| `fixed` | 导致 `from_chars()` 不需要或分析指数。 它类似于 `'f'` `printf()` 格式说明符，格式说明符用于浮点的格式，如 `"17.29"` 。|
| `hex` | 如果 `from_chars()` 没有前导 "0x"，则会将数字的格式设置为十六进制格式。 |
| `general` | 导致 `from_chars()` 接受（但不要求）指数。 对于 `to_chars()` ，它类似于 `g` printf （）格式说明符，它在科学记数法或固定之间切换。 它将考虑指数的作用，以便能够生成合理的输出。 例如：将 `1e-5` 生成 `"1e-05"` ，但会 `1e-4` 生成 `"0.001"` 。 `1e5`结果为 `100000` ，而 `1e6` 结果为 `1e+06` 。 `1e0`生成 `1` 。|

## <a name="remarks"></a>备注

对于[from_chars](charconv-functions.md#from_chars)函数，此枚举描述预期的输入类型。
对于[to_chars](charconv-functions.md#to_chars)函数，它描述要发出的输出类型。

## <a name="see-also"></a>另请参阅

[\<charconv>](../standard-library/charconv.md)  
[printf （）格式说明符](..\c-runtime-library\format-specification-syntax-printf-and-wprintf-functions.md)
