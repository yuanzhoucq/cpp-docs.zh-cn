---
title: '&lt;limits&gt; 枚举'
ms.date: 11/04/2016
f1_keywords:
- limits/std::float_denorm_style
- limits/std::float_round_style
ms.assetid: c86680a2-ba97-4ed9-8c20-a448857d7dc5
ms.openlocfilehash: 567e0538f59c40d57f85d652a8919be6e034cf0b
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245359"
---
# <a name="ltlimitsgt-enums"></a>&lt;limits&gt; 枚举

## <a name="float_denorm_style"></a> float_denorm_style

此枚举描述实现可以选择用于表示非标准化浮点值的各种方法，这种浮点值由于太小而无法表示为规范化值：

```cpp
enum float_denorm_style {
    denorm_indeterminate = -1,
    denorm_absent = 0,
    denorm_present = 1    };
```

### <a name="return-value"></a>返回值

此枚举返回：

- `denorm_indeterminate` 如果不能在转换时确定是否存在非规范化窗体。

- `denorm_absent` 如果不存在非规范化窗体。

- `denorm_present` 如果存在非规范化窗体。

### <a name="example"></a>示例

有关可访问此枚举的值的示例，请参阅 [numeric_limits::has_denorm](../standard-library/numeric-limits-class.md#has_denorm)。

## <a name="float_round_style"></a> float_round_style

此枚举描述实现可以选择用于将浮点值舍入为整数值的各种方法。

```cpp
enum float_round_style {
    round_indeterminate = -1,
    round_toward_zero = 0,
    round_to_nearest = 1,
    round_toward_infinity = 2,
    round_toward_neg_infinity = 3    };
```

### <a name="return-value"></a>返回值

此枚举返回：

- `round_indeterminate` 如果无法确定舍入方法。

- `round_toward_zero` 如果向零舍入。

- `round_to_nearest` 如果舍入到最接近的整数。

- `round_toward_infinity` 如果远离零方向舍入。

- `round_toward_neg_infinity` 如果舍入到更负整数。

### <a name="example"></a>示例

有关可访问此枚举的值的示例，请参阅 [numeric_limits::round_style](../standard-library/numeric-limits-class.md#round_style)。
