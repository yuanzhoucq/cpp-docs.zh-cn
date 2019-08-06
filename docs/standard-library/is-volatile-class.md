---
title: is_volatile 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_volatile
helpviewer_keywords:
- is_volatile class
- is_volatile
ms.assetid: 54922e8a-db4e-4cae-8931-b3352f0b8d3b
ms.openlocfilehash: daba5dff55e0f3afa1e9996631125bf7ba64d52e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458846"
---
# <a name="isvolatile-class"></a>is_volatile 类

测试类型是否是可变的。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_volatile;
```

### <a name="parameters"></a>参数

*Ty*\
要查询的类型。

## <a name="remarks"></a>备注

如果*Ty*为`volatile-qualified`, 则类型谓词的实例为 true。

## <a name="example"></a>示例

```cpp
// std__type_traits__is_volatile.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_volatile<trivial> == " << std::boolalpha
        << std::is_volatile<trivial>::value << std::endl;
    std::cout << "is_volatile<volatile trivial> == " << std::boolalpha
        << std::is_volatile<volatile trivial>::value << std::endl;
    std::cout << "is_volatile<int> == " << std::boolalpha
        << std::is_volatile<int>::value << std::endl;
    std::cout << "is_volatile<volatile int> == " << std::boolalpha
        << std::is_volatile<volatile int>::value << std::endl;

    return (0);
    }
```

```Output
is_volatile<trivial> == false
is_volatile<volatile trivial> == true
is_volatile<int> == false
is_volatile<volatile int> == true
```

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)\
[is_const 类](../standard-library/is-const-class.md)
