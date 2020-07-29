---
title: is_invocable、is_invocable_r、is_nothrow_invocable is_nothrow_invocable_r 类
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::is_invocable
- type_traits/std::is_invocable_r
- type_traits/std::is_nothrow_invocable
- type_traits/std::is_nothrow_invocable_r
helpviewer_keywords:
- is_invocable class
- is_invocable
- is_invocable_r class
- is_invocable_r
- is_nothrow_invocable class
- is_nothrow_invocable
- is_nothrow_invocable_r class
- is_nothrow_invocable_r
ms.openlocfilehash: 47801eff0ea0c41c7b69dfb7a1aa5190a43f1b75
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233101"
---
# <a name="is_invocable-is_invocable_r-is_nothrow_invocable-is_nothrow_invocable_r-classes"></a>is_invocable、is_invocable_r、is_nothrow_invocable is_nothrow_invocable_r 类

这些模板确定是否可以使用指定的参数类型调用类型。 `is_invocable_r``is_nothrow_invocable_r`还确定调用的结果是否可转换为特定类型。 `is_nothrow_invocable``is_nothrow_invocable_r`还确定调用是否已知不会引发异常。 在 c + + 17 中添加。

## <a name="syntax"></a>语法

```cpp
template <class Callable, class... Args>
struct is_invocable;

template <class Convertible, class Callable, class... Args>
struct is_invocable_r;

template <class Callable, class... Args>
struct is_nothrow_invocable;

template <class Convertible, class Callable, class... Args>
struct is_nothrow_invocable_r;

// Helper templates
template <class Callable, class... Args>
inline constexpr bool is_invocable_v =
    std::is_invocable<Callable, Args...>::value;

template <class Convertible, class Callable, class... Args>
inline constexpr bool is_invocable_r_v =
    std::is_invocable_r<Convertible, Callable, Args...>::value;

template <class Callable, class... Args>
inline constexpr bool is_nothrow_invocable_v =
    std::is_nothrow_invocable<Callable, Args...>::value;

template <class Convertible, class Callable, class... Args>
inline constexpr bool is_nothrow_invocable_r_v =
    std::is_nothrow_invocable_r<Convertible, Callable, Args...>::value;
```

### <a name="parameters"></a>参数

*多次*\
要查询的可调用类型。

*Args*\
要查询的参数类型。

*自由*\
可*调用*结果的类型必须可转换为。

## <a name="remarks"></a>备注

`is_invocable`如果可以使用未计算上下文中的 arguments *Callable*参数调用可调用的类型， *Args*则类型谓词保留为 true。

`is_invocable_r`如果可以使用未计算上下文中的 arguments *Callable*参数调用可调用的类型， *Args*则类型谓词为 true，以生成可转换为*可转换*的结果类型。

`is_nothrow_invocable`如果可以使用未计算上下文中的 arguments 参数调用可调用的类型， *Args*则类型谓词为 true，这种调用被认为不会引发异常。 *Callable*

`is_nothrow_invocable_r`如果可以使用未计算上下文中的 arguments *Callable*参数调用可调用的可调用*Args*类型以使结果类型可转换为*可转换*的，则类型谓词为 true，这种调用被认为不会引发异常。

可*转换*、可*调用*和参数包参数中的类型的每个*类型都必须*是完整类型、未知绑定的数组或可能的 cv 限定类型 **`void`** 。 否则，谓词的行为是不确定的。

## <a name="example"></a>示例

```cpp
// std__type_traits__is_invocable.cpp
// compile using: cl /EHsc /std:c++17 std__type_traits__is_invocable.cpp
#include <type_traits>

auto test1(int) noexcept -> int (*)()
{
    return nullptr;
}

auto test2(int) -> int (*)()
{
    return nullptr;
}

int main()
{
    static_assert( std::is_invocable<decltype(test1), short>::value );

    static_assert( std::is_invocable_r<int(*)(), decltype(test1), int>::value );
    static_assert( std::is_invocable_r<long(*)(), decltype(test1), int>::value ); // fails

    static_assert( std::is_nothrow_invocable<decltype(test1), int>::value );
    static_assert( std::is_nothrow_invocable<decltype(test2), int>::value ); // fails

    static_assert( std::is_nothrow_invocable_r<int(*)(), decltype(test1), int>::value );
    static_assert( std::is_nothrow_invocable_r<int(*)(), decltype(test2), int>::value ); // fails
}
```

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>另请参阅

[<type_traits>](../standard-library/type-traits.md)\
[invoke](functional-functions.md#invoke)
