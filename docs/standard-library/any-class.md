---
title: 任何类
ms.date: 04/04/2019
f1_keywords:
- any/std::any
- any/std::any::emplace
- any/std::any::has_value
- any/std::any::reset
- any/std::any::swap
- any/std::any::type
helpviewer_keywords:
- any/std::any
- any/std::any::emplace
- any/std::any::has_value
- any/std::any::reset
- any/std::any::swap
- any/std::any::type
ms.openlocfilehash: 050276da665ab6ed3eb53d9e65bfea06b88bcbea
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268749"
---
# <a name="any-class"></a>任何类

存储满足构造函数要求或其任何类型的实例具有任何值，这是调用类的状态的任何对象。

存储的实例称为包含的值。 如果二者都提供任何值，或同时拥有值和包含的值是相同的两个状态都是相同的。

## <a name="syntax"></a>语法

```cpp
class any
```

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|||
|-|-|
|[any](#any)|构造 `any` 类型的对象。|

### <a name="functions"></a>函数

|||
|-|-|
|[emplace](#emplace)|设置任何值。|
|[has_value](#has_value)|返回 **，则返回 true**如果任何具有一个值。|
|[reset](#reset)|重置了任何。|
|[swap](#swap)|交换两个任何对象。|
|[type](#type)|返回的任何类型。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator=](#op_eq)|任何替换任何使用的另一个副本。|

## <a name="any"></a> 任何

构造 `any` 类型的对象。 此外包括析构函数。

```cpp
constexpr any() noexcept;
any(const any& other);
any(any&& other) noexcept;
template <class T>
    any(T&& value);
template <class T, class... Args>
    explicit any(in_place_type_t<T>, Args&&...);
template <class T, class U, class... Args>
    explicit any(in_place_type_t<T>, initializer_list<U>, Args&&...);

~any();
```

## <a name="emplace"></a> emplace

设置任何值。

```cpp
template <class T, class... Args>
    decay_t<T>& emplace(Args&& ...);
template <class T, class U, class... Args>
    decay_t<T>& emplace(initializer_list<U>, Args&&...);
```

## <a name="has_value"></a> has_value

返回 **，则返回 true**如果任何具有一个值。

```cpp
bool has_value() const noexcept;
```

## <a name="op_eq"></a> 运算符 =

任何替换任何使用的另一个副本。

```cpp
any& operator=(const any& right);
any& operator=(any&& right) noexcept;
template <class T>
    any& operator=(T&& right);
```

### <a name="parameters"></a>参数

*右侧*\
任何要复制到任何。

## <a name="reset"></a> 重置

重置了任何。

```cpp
void reset() noexcept;
```

## <a name="swap"></a> 交换

交换两个任何对象。

```cpp
void swap(any& rhs) noexcept;
```

## <a name="type"></a> 类型

返回的任何类型。

```cpp
const type_info& type() const noexcept;
```
