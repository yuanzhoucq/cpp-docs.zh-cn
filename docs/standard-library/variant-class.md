---
title: 变体类
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
ms.openlocfilehash: 9bfdf644374a0b825fd0ca02bf4164a766cb42a3
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269299"
---
# <a name="variant-class"></a>变体类

在任何给定时间的变任何的体实例可以包含其替代类型之一的值或不包含任何值。

## <a name="syntax"></a>语法

```cpp
template <class... Types>
    class variant
```

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|||
|-|-|
|[变体](#variant)|构造 `variant` 类型的对象。|

### <a name="functions"></a>函数

|||
|-|-|
|[emplace](#emplace)|创建一个新的包含的值。|
|[index](#index)|返回包含的值的索引。|
|[swap](#swap)||
|[valueless_by_exception](#emplace)|返回**false**如果变体包含一个值。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator=](#op_eq)|将变量替换为另一个变体的副本。|

## <a name="emplace"></a> emplace

创建一个新的包含的值。

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

## <a name="index"></a> 索引

返回包含的值的索引。

```cpp
constexpr size_t index() const noexcept;
```

## <a name="variant"></a> 变体

构造 `variant` 类型的对象。 此外包括析构函数。

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

*Al*\
要用于此对象的分配器类。

## <a name="op_eq"></a> 运算符 =

将变量替换为另一个变体的副本。

```cpp
variant& operator=(const variant&);
variant& operator=(variant&&) noexcept(see below);
template <class T>
    variant& operator=(T&&) noexcept(see below);
```

## <a name="swap"></a> 交换

```cpp
void swap(variant&) noexcept(see below);
```

## <a name="valueless"></a> valueless_by_exception

返回**false**如果变体包含一个值。

```cpp
constexpr bool valueless_by_exception() const noexcept;
```
