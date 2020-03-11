---
title: '&lt;scoped_allocator&gt; 运算符'
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
ms.openlocfilehash: 071fc3b73cd3378b110d6d412bb7575e35a77478
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876330"
---
# <a name="ltscoped_allocatorgt-operators"></a>&lt;scoped_allocator&gt; 运算符

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  operator!=

测试两个 `scoped_allocator_adaptor` 对象是否不相等。

```cpp
template <class Outer, class... Inner>
bool operator!=(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>parameters

*左*\
左 `scoped_allocator_adaptor` 对象。

*right*\
正确的 `scoped_allocator_adaptor` 对象。

### <a name="return-value"></a>返回值

`!(left == right)`

## <a name="op_eq_eq"></a>operator==

测试两个 `scoped_allocator_adaptor` 对象是否相等。

```cpp
template <class Outer, class... Inner>
bool operator==(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>parameters

*左*\
左 `scoped_allocator_adaptor` 对象。

*right*\
正确的 `scoped_allocator_adaptor` 对象。

### <a name="return-value"></a>返回值

`left.outer_allocator() == right.outer_allocator() && left.inner_allocator() == right.inner_allocator()`

## <a name="see-also"></a>另请参阅

[<scoped_allocator>](../standard-library/scoped-allocator.md)
