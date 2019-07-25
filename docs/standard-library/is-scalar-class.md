---
title: is_scalar 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_scalar
helpviewer_keywords:
- is_scalar class
- is_scalar
ms.assetid: a0cdfc9a-f27e-4808-890f-6ed7942db60c
ms.openlocfilehash: d562ba4beb037d547846f57e7b40eaceb409a358
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449810"
---
# <a name="isscalar-class"></a>is_scalar 类

测试类型是否为标量。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_scalar;
```

### <a name="parameters"></a>参数

*Ty*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型*Ty*是整数类型、浮点类型、枚举类型、指针类型或指向成员类型的指针或`cv-qualified`其中之一的形式, 则类型谓词的实例为 true; 否则为 false。

## <a name="example"></a>示例

```cpp
// std__type_traits__is_scalar.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_scalar<trivial> == " << std::boolalpha
        << std::is_scalar<trivial>::value << std::endl;
    std::cout << "is_scalar<trivial *> == " << std::boolalpha
        << std::is_scalar<trivial *>::value << std::endl;
    std::cout << "is_scalar<int> == " << std::boolalpha
        << std::is_scalar<int>::value << std::endl;
    std::cout << "is_scalar<float> == " << std::boolalpha
        << std::is_scalar<float>::value << std::endl;

    return (0);
    }
```

```Output
is_scalar<trivial> == false
is_scalar<trivial *> == true
is_scalar<int> == true
is_scalar<float> == true
```

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)\
[is_compound 类](../standard-library/is-compound-class.md)
