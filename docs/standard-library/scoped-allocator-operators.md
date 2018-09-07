---
title: '&lt;scoped_allocator&gt; 运算符 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
dev_langs:
- C++
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
ms.openlocfilehash: 0dda1415ea875b01c943a0a275122458f399f69c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105869"
---
# <a name="ltscopedallocatorgt-operators"></a>&lt;scoped_allocator&gt; 运算符

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>operator!=

测试两个 `scoped_allocator_adaptor` 对象是否不相等。

```cpp
template <class Outer, class... Inner>
bool operator!=(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>参数

*left*<br/>
左 `scoped_allocator_adaptor` 对象。

*right*<br/>
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

### <a name="parameters"></a>参数

*left*<br/>
左 `scoped_allocator_adaptor` 对象。

*right*<br/>
正确的 `scoped_allocator_adaptor` 对象。

### <a name="return-value"></a>返回值

`left.outer_allocator() == right.outer_allocator() && left.inner_allocator() == right.inner_allocator()`

## <a name="see-also"></a>请参阅

[<scoped_allocator>](../standard-library/scoped-allocator.md)<br/>
