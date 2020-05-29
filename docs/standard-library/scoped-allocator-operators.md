---
title: '&lt;scoped_allocator&gt; 运算符'
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
ms.openlocfilehash: 45da89793c3f4ea131404fc3392413e7aea9ef3e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373380"
---
# <a name="ltscoped_allocatorgt-operators"></a>&lt;scoped_allocator&gt; 运算符

|||
|-|-|
|[操作员！](#op_neq)|[运算符*](#op_eq_eq)|

## <a name="operator"></a><a name="op_neq"></a>操作员！

测试两个 `scoped_allocator_adaptor` 对象是否不相等。

```cpp
template <class Outer, class... Inner>
bool operator!=(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>参数

*离开*\
左 `scoped_allocator_adaptor` 对象。

*对*\
正确的 `scoped_allocator_adaptor` 对象。

### <a name="return-value"></a>返回值

`!(left == right)`

## <a name="operator"></a><a name="op_eq_eq"></a>运算符*

测试两个 `scoped_allocator_adaptor` 对象是否相等。

```cpp
template <class Outer, class... Inner>
bool operator==(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>参数

*离开*\
左 `scoped_allocator_adaptor` 对象。

*对*\
正确的 `scoped_allocator_adaptor` 对象。

### <a name="return-value"></a>返回值

`left.outer_allocator() == right.outer_allocator() && left.inner_allocator() == right.inner_allocator()`

## <a name="see-also"></a>另请参阅

[<scoped_allocator>](../standard-library/scoped-allocator.md)
