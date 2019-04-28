---
title: is_invocable、 is_invocable_r、 is_nothrow_invocable、 is_nothrow_invocable_r 类
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
ms.openlocfilehash: bb5e75a897029ded2e00e491d93d2df41a3e115b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62336226"
---
# <a name="isinvocable-isinvocabler-isnothrowinvocable-isnothrowinvocabler-classes"></a>is_invocable、 is_invocable_r、 is_nothrow_invocable、 is_nothrow_invocable_r 类

这些模板确定是否类型可以在调用与指定的参数类型。 `is_invocable_r` 和`is_nothrow_invocable_r`还确定是否调用的结果转换为特定类型。 `is_nothrow_invocable` 和`is_nothrow_invocable_r`还确定是否调用是否确定不引发异常。 添加 C + + 17 中。

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

*Callable*<br/>
要查询的可调用类型。

*参数*<br/>
若要查询的参数类型。

*Convertible*<br/>
结果的类型的*Callable*必须可转换为。

## <a name="remarks"></a>备注

`is_invocable`如果 true 保留类型的谓词可调用类型*Callable*可以使用参数来调用*Args*未计算的上下文中。

`is_invocable_r`如果 true 保留类型的谓词可调用类型*Callable*可以使用参数来调用*Args*中的未计算的上下文，以生成一个结果类型可转换为*可转换为*。

`is_nothrow_invocable`如果 true 保留类型的谓词可调用类型*Callable*可以使用参数来调用*Args*在未计算的上下文，并且此类调用是否确定不引发异常。

`is_nothrow_invocable_r`如果 true 保留类型的谓词可调用类型*Callable*可以使用参数来调用*Args*中的未计算的上下文，以生成一个结果类型可转换为*可转换为*，且此类调用已知无法引发异常。

每个类型*可转换*， *Callable*，参数包中的类型*Args*必须是完整类型、 未知边界的数组或可能是 cv 限定**void**。 否则，该谓词的行为是不确定的。

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

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[invoke](functional-functions.md#invoke)<br/>
