---
title: is_integral 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_integral
helpviewer_keywords:
- is_integral class
- is_integral
ms.assetid: fe9279d0-4495-4e88-bf23-153cc6602397
ms.openlocfilehash: a3d618b77d69f5d80736ac20304c9184c5963b25
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217761"
---
# <a name="is_integral-class"></a>is_integral 类

测试类型是否为整型。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_integral;
```

### <a name="parameters"></a>参数

*Ty*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型*Ty*为整型类型之一，或类型为整数类型之一的形式，则类型谓词的实例为 true `cv-qualified` ; 否则为 false。

整型类型是 **`bool`** 、 **`char`** 、、 **`unsigned char`** **`signed char`** 、 **`wchar_t`** 、 **`short`** **`unsigned short`** **`int`** **`unsigned int`** **`long`** **`unsigned long`** 、、、、和之一。 此外，对于提供这些类型的编译器，整型类型可以是 **`long long`** 、、 **`unsigned long long`** **`__int64`** 和**无符号 __int64**之一。

## <a name="example"></a>示例

```cpp
// std__type_traits__is_integral.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_integral<trivial> == " << std::boolalpha
        << std::is_integral<trivial>::value << std::endl;
    std::cout << "is_integral<int> == " << std::boolalpha
        << std::is_integral<int>::value << std::endl;
    std::cout << "is_integral<float> == " << std::boolalpha
        << std::is_integral<float>::value << std::endl;

    return (0);
    }
```

```Output
is_integral<trivial> == false
is_integral<int> == true
is_integral<float> == false
```

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>另请参阅

[<type_traits>](../standard-library/type-traits.md)\
[is_enum 类](../standard-library/is-enum-class.md)\
[is_floating_point 类](../standard-library/is-floating-point-class.md)
