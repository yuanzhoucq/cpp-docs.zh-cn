---
title: '&lt;变体&gt;运算符'
ms.date: 04/04/2019
f1_keywords:
- variant/std::operator!=
- variant/std::operator==
- variant/std::operatoroperator&gt;
- variant/std::operatoroperator&gt=;
- variant/std::operatoroperator&lt;
- variant/std::operatoroperator&lt;=
helpviewer_keywords:
- std::operator!= (variant)
- std::operator== (variant)
- std::operatoroperator&gt; (variant)
- std::operatoroperator&gt=; (variant)
- std::operatoroperator&lt; (variant)
- std::operatoroperator&lt;= (variant)
ms.openlocfilehash: 0c4042ca1d89f9835b32924b268ef17a56619009
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268559"
---
# <a name="ltvariantgt-operators"></a>&lt;变体&gt;运算符

## <a name="op_eq_eq"></a> 运算符 = =

测试运算符左侧的转发列表对象是否等于右侧的转发列表对象。

```cpp
template <class... Types>
    constexpr bool operator==(const variant<Types...>&, const variant<Types...>&);
```

## <a name="op_neq"></a> 运算符 ！ =

测试运算符左侧的转发列表对象是否不等于右侧的转发列表对象。

```cpp
template <class... Types>
    constexpr bool operator!=(const variant<Types...>&, const variant<Types...>&);
```

## <a name="op_lt"></a> 运算符&lt;

测试运算符左侧的转发列表对象是否小于右侧的转发列表对象。

```cpp
template <class... Types>
    constexpr bool operator<(const variant<Types...>&, const variant<Types...>&);
```

## <a name="op_lt_eq"></a> 运算符&lt;=

测试运算符左侧的转发列表对象是否小于或等于右侧的转发列表对象。

```cpp
template <class... Types>
    constexpr bool operator<=(const variant<Types...>&, const variant<Types...>&);
```

## <a name="op_gt"></a> 运算符&gt;

测试运算符左侧的转发列表对象是否大于右侧的转发列表对象。

```cpp
template <class... Types> constexpr
    bool operator>(const variant<Types...>&, const variant<Types...>&);
```

## <a name="op_gt_eq"></a> 运算符&gt;=

测试运算符左侧的转发列表对象是否大于或等于右侧的转发列表对象。

```cpp
template <class... Types> constexpr
    bool operator>=(const variant<Types...>&, const variant<Types...>&);
```
