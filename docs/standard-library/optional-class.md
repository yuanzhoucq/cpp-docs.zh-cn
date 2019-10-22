---
title: 可选类
ms.date: 11/04/2016
f1_keywords:
- optional/std::optional
- optional/std::optional::has_value
- optional/std::optional::reset
- optional/std::optional::value
- optional/std::optional::value_or
helpviewer_keywords:
- optional/std::optional
- optional/std::optional::has_value
- optional/std::optional::reset
- optional/std::optional::value
- optional/std::optional::value_or
ms.openlocfilehash: d9c4bf5356e6ff163ecdf7e1a80bc55453d59003
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689151"
---
# <a name="optional-class"></a>可选类

类模板 `optional<T>` 描述一个对象，该对象可能包含也可能不包含 `T` 类型的值，称为*包含值*。

当的实例 `optional<T>` 包含一个值时，包含的值将在 `optional` 对象的存储中分配，该区域在为类型 `T` 进行了适当对齐的区域中。 将 `optional<T>` 转换为 `bool` 时，如果该对象包含一个值，则将 `true` 结果;否则，`false`。

@No__t_0 包含的对象类型不得为[in_place_t](in-place-t-struct.md)或[nullopt_t](nullopt-t-structure.md)。 `T` 必须是*易损坏*，也就是说，其析构函数必须回收所有拥有的资源，并且可能不会引发异常。

@No__t_0 类是 c + + 17 中的新类。

## <a name="syntax"></a>语法

```cpp
template <class T>
class optional
{
    using value_type = T;
};

template<class T> optional(T) -> optional<T>;
```

## <a name="members"></a>Members

### <a name="constructors"></a>构造函数

|||
|-|-|
| **构造函数和析构函数** | |
|[optional](#optional) | 构造 `optional` 类型的对象。 |
|[~ 可选](#optional-destructor) | 销毁 `optional` 类型的对象。 |
| **赋值** | |
| [operator=](#op_eq) | 使用另一个 `optional` 的副本替换 `optional`。 |
| [emplace](#op_eq) | 用指定的参数初始化包含的值。 |
| **Swap** | |
| [swap](#swap) | 将包含的值或空状态替换为其他 `optional`。 |
| **监视** | |
| [has_value](#has_value) | 返回 `optional` 对象是否包含值。 |
| [value](#value) | 返回包含的值。 |
| [value_or](#value_or) | 返回包含的值; 如果不存在任何值，则返回替代项。 |
| [operator->](#op_as) | 引用 `optional` 对象的包含值。 |
| [operator*](#op_mem) | 引用 `optional` 对象的包含值。 |
| [operator bool](#op_bool) | 返回 `optional` 对象是否包含值。 |
| **修饰符** | |
| [reset](#reset) | 通过销毁任何包含的值来重置 `optional`。 |

## <a name="has_value"></a>has_value

```cpp
constexpr bool has_value() const noexcept;
```

## <a name="optional"></a>可选构造函数

构造 `optional` 类型的对象。

```cpp
constexpr optional() noexcept;
constexpr optional(nullopt_t nullopt) noexcept;
constexpr optional(const optional& rhs);
constexpr optional(optional&& rhs) noexcept;

template <class... Args>
constexpr explicit optional(in_place_t, Args&&... args);

template <class U, class... Args>
constexpr explicit optional(in_place_t, initializer_list<U> i_list, Args&&... args);

template <class U = T>
explicit constexpr optional(U&& rhs);

template <class U>
explicit optional(const optional<U>& rhs);

template <class U>
explicit optional(optional<U>&& rhs);
```

### <a name="parameters"></a>参数

*rhs* \
要复制或移动的 `optional` 构造包含的值。

*i_list* \
要从其构造包含的值的初始值设定项列表。

*args* \
要从其构造包含的值的参数列表。

### <a name="remarks"></a>备注

`constexpr optional() noexcept;` 
 `constexpr optional(nullopt_t nullopt) noexcept;` 这些构造函数构造的 `optional` 不包含值。

`constexpr optional(const optional& rhs);` 复制构造函数将从参数的包含值初始化包含的值。 如果 `is_copy_constructible_v<T>` 为 true，则将其定义为**已删除**，如果 `is_trivially_copy_constructible_v<T>` 为 true，则会很简单。

`constexpr optional(optional&& rhs) noexcept;` 移动构造函数通过从参数包含的值移动来初始化包含的值。 除非 `is_move_constructible_v<T>` 为 true，否则它不参与重载决策，如果 `is_trivially_move_constructible_v<T>` 为 true，则很简单。

`template <class... Args> constexpr explicit optional(in_place_t, Args&&... args);` 直接初始化包含的值，就像使用 `std::forward<Args>(args)` 的参数。 如果使用的 `T` 构造函数 `constexpr`，则 `constexpr` 此构造函数。 除非 `is_constructible_v<T, Args...>` 为 true，否则它不参与重载决策。

`template <class U, class... Args> constexpr explicit optional(in_place_t, initializer_list<U> i_list, Args&&... args);` 直接初始化包含的值，就像使用 `i_list, std::forward<Args>(args)` 的参数。 如果使用的 `T` 构造函数 `constexpr`，则 `constexpr` 此构造函数。 除非 `is_constructible_v<T, initializer_list<U>&, Args&&...>` 为 true，否则它不参与重载决策。

`template <class U = T> explicit constexpr optional(U&& rhs);` 直接初始化包含的值，就像使用 `std::forward<U>(v)` 一样。 如果使用的 `T` 构造函数 `constexpr`，则 `constexpr` 此构造函数。 如果 `is_constructible_v<T, U&&>` 为 true，则它不参与重载决策，并且 `is_same_v<remove_cvref_t<U>, in_place_t>` 并且 `is_same_v<remove_cvref_t<U>, optional>` 为 false。

`template <class U> explicit optional(const optional<U>& rhs);` 如果*rhs*包含值，请直接从参数的包含值初始化包含的值。 除非 `is_constructible_v<T, const U&>` 为 true，并且 `is_constructible_v<T, optional<U>&>`、`is_constructible_v<T, optional<U>&&>`、`is_constructible_v<T, const optional<U>&>`、`is_constructible_v<T, const optional<U>&&>`、`is_convertible_v<optional<U>&, T>`、`is_convertible_v<optional<U>&&, T>`、`is_convertible_v<const optional<U>&, T>` 和 `is_convertible_v<const optional<U>&&, T>` 均为 false，否则它不参与重载决策。

`template <class U> explicit optional(optional<U>&& rhs);` 如果*rhs*包含值，请直接初始化包含的值，就像使用 `std::move(*rhs)` 一样。 除非 `is_constructible_v<T, U&&>` 为 true，并且 `is_constructible_v<T, optional<U>&>`、`is_constructible_v<T, optional<U>&&>`、`is_constructible_v<T, const optional<U>&>`、`is_constructible_v<T, const optional<U>&&>`、`is_convertible_v<optional<U>&, T>`、`is_convertible_v<optional<U>&&, T>`、`is_convertible_v<const optional<U>&, T>` 和 `is_convertible_v<const optional<U>&&, T>` 均为 false，否则它不参与重载决策。

## <a name="optional-destructor"></a>~ 可选析构函数

通过调用其析构函数，销毁任何非完全易损坏包含值（如果存在）。

```cpp
~optional();
```

### <a name="remarks"></a>备注

如果 `T` 是完全易损坏，则 `optional<T>` 也是完全易损坏。

## <a name="op_eq"></a>operator =

使用复制或从另一个 `optional` 包含的值中移动来替换 `optional` 的包含值。

```cpp
optional& operator=(nullopt_t) noexcept;
optional& operator=(const optional& rhs);
optional& operator=(optional&&) noexcept( /* see below */ );

template <class U = T>
    optional& operator=(U&&);

template <class U>
optional& operator=(const optional<U>&);

template <class U>
    optional& operator=(optional<U>&&);

template <class... Args>
T& emplace(Args&&...);

template <class U, class... Args>
T& emplace(initializer_list<U>, Args&&...);
```

## <a name="op_as"></a>operator->

取消对 `optional` 对象的包含值的引用。

```cpp
constexpr const T* operator->() const;
constexpr T* operator->();
```

## <a name="op_mem"></a>操作员

取消对 `optional` 对象的包含值的引用。

```cpp
constexpr const T& operator*() const&;
constexpr T& operator*() &;
constexpr T&& operator*() &&;
constexpr const T&& operator*() const&&;
```

## <a name="op_bool"></a>operator bool

报告 `optional` 对象是否具有包含的值。

```cpp
constexpr explicit operator bool() const noexcept;
```

## <a name="reset"></a>&

有效地调用包含的对象的析构函数（如果有），并将其设置为未初始化的状态。

```cpp
void reset() noexcept;
```

## <a name="swap"></a>购

```cpp
template<class T>
void swap(optional<T>&, optional<T>&) noexcept;
```

## <a name="value"></a>负值

```cpp
constexpr const T& value() const&;
constexpr T& value() &;
constexpr T&& value() &&;
constexpr const T&& value() const&&;
```

## <a name="value_or"></a>value_or

```cpp
template <class U>
    constexpr T value_or(U&&) const&;
template <class U>
    constexpr T value_or(U&&) &&;
```

## <a name="see-also"></a>请参阅

[\<optional >](optional.md)
