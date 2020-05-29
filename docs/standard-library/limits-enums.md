---
title: '&lt;limits&gt; 枚举'
ms.date: 11/04/2016
f1_keywords:
- limits/std::float_denorm_style
- limits/std::float_round_style
ms.assetid: c86680a2-ba97-4ed9-8c20-a448857d7dc5
ms.openlocfilehash: 567e0538f59c40d57f85d652a8919be6e034cf0b
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425609"
---
# <a name="ltlimitsgt-enums"></a>&lt;limits&gt; 枚举

## <a name="float_denorm_style"></a>float_denorm_style

此枚举描述实现可以选择用于表示非标准化浮点值的各种方法，这种浮点值由于太小而无法表示为规范化值：

```cpp
enum float_denorm_style {
    denorm_indeterminate = -1,
    denorm_absent = 0,
    denorm_present = 1    };
```

### <a name="return-value"></a>返回值

此枚举返回：

- 如果在翻译时无法确定是否存在非规范化窗体，则 `denorm_indeterminate`。

- 如果不存在非规范化窗体，则 `denorm_absent`。

- 如果存在非规范化窗体，则 `denorm_present`。

### <a name="example"></a>示例

有关可访问此枚举的值的示例，请参阅 [numeric_limits::has_denorm](../standard-library/numeric-limits-class.md#has_denorm)。

## <a name="float_round_style"></a>float_round_style

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

- 如果无法确定舍入方法，则 `round_indeterminate`。

- 如果向零舍入，则 `round_toward_zero`。

- 如果舍入到最接近的整数，则 `round_to_nearest`。

- 如果从零开始舍入，则 `round_toward_infinity`。

- 如果舍入为更大的负整数，则 `round_toward_neg_infinity`。

### <a name="example"></a>示例

有关可访问此枚举的值的示例，请参阅 [numeric_limits::round_style](../standard-library/numeric-limits-class.md#round_style)。
