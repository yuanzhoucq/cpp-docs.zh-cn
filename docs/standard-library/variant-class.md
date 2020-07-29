---
title: variant 类
ms.date: 04/04/2019
f1_keywords:
- variant/std::variant
- variant/std::variant::emplace
- variant/std::variant::index
- variant/std::variant::valueless_by_exception
helpviewer_keywords:
- variant/std::variant
- variant/std::variant::emplace
- variant/std::variant::index
- variant/std::variant::valueless_by_exception
ms.openlocfilehash: e34704b0ad8cf8fbaf8ee9514583f9597be40122
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215395"
---
# <a name="variant-class"></a>variant 类

任何给定时间的任何变体实例都可保存其替代类型之一的值，或者不包含任何值。

## <a name="syntax"></a>语法

```cpp
template <class... Types>
    class variant
```

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|||
|-|-|
|[变量](#variant)|构造 `variant` 类型的对象。|

### <a name="functions"></a>函数

|||
|-|-|
|[emplace](#emplace)|创建新的包含值。|
|[index](#index)|返回包含的值的索引。|
|[swap](#swap)||
|[valueless_by_exception](#emplace)|**`false`** 如果变量包含值，则返回。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator =](#op_eq)|将变体替换为另一种变体的副本。|

## <a name="emplace"></a><a name="emplace"></a>emplace

创建新的包含值。

```cpp
template <class T, class... Args>
    T& emplace(Args&&...);
template <class T, class U, class... Args>
    T& emplace(initializer_list<U>, Args&&...);
template <size_t I, class... Args>
    variant_alternative_t<I, variant<Types...>>& emplace(Args&&...);
template <size_t I, class U, class... Args>
    variant_alternative_t<I, variant<Types...>>& emplace(initializer_list<U>, Args&&...);
```

## <a name="index"></a><a name="index"></a>编入

返回包含的值的索引。

```cpp
constexpr size_t index() const noexcept;
```

## <a name="variant"></a><a name="variant"></a>变体

构造 `variant` 类型的对象。 还包含析构函数。

```cpp
constexpr variant() noexcept(see below);
variant(const variant&);
variant(variant&&) noexcept(see below);
template <class T>
    constexpr variant(T&&) noexcept(see below);
template <class T, class... Args>
    constexpr explicit variant(in_place_type_t<T>, Args&&...);
template <class T, class U, class... Args>
    constexpr explicit variant(in_place_type_t<T>, initializer_list<U>, Args&&...);
template <size_t I, class... Args>
    constexpr explicit variant(in_place_index_t<I>, Args&&...);
template <size_t I, class U, class... Args>
    constexpr explicit variant(in_place_index_t<I>, initializer_list<U>, Args&&...);

template <class Alloc>
    variant(allocator_arg_t, const Al&);
template <class Alloc>
    variant(allocator_arg_t, const Al&, const variant&);
template <class Alloc>
    variant(allocator_arg_t, const Al&, variant&&);
template <class Alloc, class T>
    variant(allocator_arg_t, const Al&, T&&);
template <class Alloc, class T, class... Args>
    variant(allocator_arg_t, const Al&, in_place_type_t<T>, Args&&...);
template <class Alloc, class T, class U, class... Args>
    variant(allocator_arg_t, const Al&, in_place_type_t<T>, initializer_list<U>, Args&&...);
template <class Alloc, size_t I, class... Args>
    variant(allocator_arg_t, const Al&, in_place_index_t<I>, Args&&...);
template <class Alloc, size_t I, class U, class... Args>
    variant(allocator_arg_t, const Al&, in_place_index_t<I>, initializer_list<U>, Args&&...);

~variant();
```

### <a name="parameters"></a>参数

*Fc-al*\
要用于此对象的分配器类。

## <a name="operator"></a><a name="op_eq"></a>operator =

将变体替换为另一种变体的副本。

```cpp
variant& operator=(const variant&);
variant& operator=(variant&&) noexcept(see below);
template <class T>
    variant& operator=(T&&) noexcept(see below);
```

## <a name="swap"></a><a name="swap"></a>购

```cpp
void swap(variant&) noexcept(see below);
```

## <a name="valueless_by_exception"></a><a name="valueless"></a>valueless_by_exception

**`false`** 如果变量包含值，则返回。

```cpp
constexpr bool valueless_by_exception() const noexcept;
```
