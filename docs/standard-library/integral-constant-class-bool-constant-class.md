---
title: integral_constant 类、bool_constant 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::integral_constant
- XTR1COMMON/std::integral_constant
- type_traits/std::bool_constant
- XTR1COMMON/std::bool_constant
helpviewer_keywords:
- std::integral_constant [C++]
- std::bool_constant [C++]
ms.assetid: 11c002c6-4d31-4042-9341-f2543f43e108
ms.openlocfilehash: 30e00fdc166b4a6f2db64a3552a3bb87335c7e32
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233140"
---
# <a name="integral_constant-class-bool_constant-class"></a>integral_constant 类、bool_constant 类

从类型和值生成整型常量。

## <a name="syntax"></a>语法

```cpp
template<class T, T v>
struct integral_constant {
   static constexpr T value = v;
   typedef T value_type;
   typedef integral_constant<T, v> type;
   constexpr operator value_type() const noexcept;
   constexpr value_type operator()() const noexcept;
   };
```

### <a name="parameters"></a>参数

*关心*\
常量的类型。

*向量*\
常量的值。

## <a name="remarks"></a>备注

`integral_constant`当使用整数类型*T*和该类型的值*v*进行专用化时，类模板表示一个对象，该对象包含具有指定值的该整型类型的常量。 名为 `type` 的成员是生成的模板专用化类型的别名，`value` 成员具有用于创建此专用化的值 *v*。

`bool_constant`类模板是 `integral_constant` **`bool`** 作为*T*参数使用的的显式部分专用化。

## <a name="example"></a>示例

```cpp
// std__type_traits__integral_constant.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "integral_constant<int, 5> == "
        << std::integral_constant<int, 5>::value << std::endl;
    std::cout << "integral_constant<bool, false> == " << std::boolalpha
        << std::integral_constant<bool, false>::value << std::endl;

    return (0);
    }
```

```Output
integral_constant<int, 5> == 5
integral_constant<bool, false> == false
```

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>另请参阅

[<type_traits>](../standard-library/type-traits.md)\
[false_type](../standard-library/type-traits-typedefs.md#false_type)\
[true_type](../standard-library/type-traits-typedefs.md#true_type)
