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
ms.assetid: 89a3b805-ab60-4858-b772-5855130c11b1
ms.openlocfilehash: 414b3e608e915ec06dbdf90726151a1c33ea4c60
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269199"
---
# <a name="optional-class"></a>可选类

描述一个对象，也不能包含一个值。

## <a name="syntax"></a>语法

```cpp
template <class T>
class optional
{
    using value_type = T;
};

template<class T> optional(T) -> optional<T>;
```

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|||
|-|-|
|[optional](#optional)|构造 `optional` 类型的对象。|

### <a name="functions"></a>函数

|||
|-|-|
|[has_value](#has_value)|返回 **，则返回 true**如果`optional`包含值。|
|[reset](#reset)|重置`optional`。|
|[值](#value)|计算结果`optional`值。|
|[value_or](#value_or)|计算结果`optional`值。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator=](#op_eq)|将替换`optional`的另一个副本`optional`。|
|[operator->](#op_as)|将值赋给`optional`。|
|[operator*](#op_mem)|引用的内存`optional`。|
|[operator bool](#op_bool)|返回一个布尔值的`optional`值。|

### <a name="has_value"></a> has_value

```cpp
constexpr bool has_value() const noexcept;
```

### <a name="optional"></a> 可选

构造 `optional` 类型的对象。 此外包括析构函数。

```cpp
constexpr optional() noexcept;
constexpr optional(nullopt_t) noexcept;
constexpr optional(const optional&);
constexpr optional(optional&&) noexcept(see below);

template <class... Args>
    constexpr explicit optional(in_place_t, Args&&...);
template <class U, class... Args>
    constexpr explicit optional(in_place_t, initializer_list<U>, Args&&...);
template <class U = T>
    explicit constexpr optional(U&&);
template <class U>
    explicit optional(const optional<U>&);
template <class U>
    explicit optional(optional<U>&&);

~optional();
```

### <a name="op_eq"></a> 运算符 =

将替换`optional`的另一个副本`optional`。

```cpp
optional& operator=(nullopt_t) noexcept;
optional& operator=(const optional&);
optional& operator=(optional&&) noexcept(see below);

template <class U = T>
    optional& operator=(U&&); template <class U> optional& operator=(const optional<U>&);
template <class U>
    optional& operator=(optional<U>&&); template <class... Args> T& emplace(Args&&...);
template <class U, class... Args>
    T& emplace(initializer_list<U>, Args&&...);
```

### <a name="op_as"></a> 运算符->

```cpp
constexpr const T* operator->() const;
constexpr T* operator->();
```

### <a name="op_mem"></a> 运算符 *

```cpp
constexpr const T& operator*() const&;
constexpr T& operator*() &;
constexpr T&& operator*() &&;
constexpr const T&& operator*() const&&;
```

### <a name="op_bool"></a> 布尔运算符

```cpp
constexpr explicit operator bool() const noexcept;
```

### <a name="reset"></a> 重置

```cpp
void reset() noexcept;
```

### <a name="value"></a> 值

```cpp
constexpr const T& value() const&;
constexpr T& value() &;
constexpr T&& value() &&;
constexpr const T&& value() const&&;
```

### <a name="value_or"></a> value_or

```cpp
template <class U>
    constexpr T value_or(U&&) const&;
template <class U>
    constexpr T value_or(U&&) &&;
```
