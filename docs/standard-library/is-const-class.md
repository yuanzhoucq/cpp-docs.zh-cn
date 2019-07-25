---
title: is_const 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_const
helpviewer_keywords:
- is_const class
- is_const
ms.assetid: 55b8e887-9c3f-4a1d-823a-4a257337b205
ms.openlocfilehash: 92059f43e73c4b76f45ea9aeae61daf573367b43
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452878"
---
# <a name="isconst-class"></a>is_const 类

测试类型是否为常量。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_const;
```

### <a name="parameters"></a>参数

*Ty*\
要查询的类型。

## <a name="remarks"></a>备注

如果*Ty*为`const-qualified`, 则类型谓词的实例为 true。

## <a name="example"></a>示例

```cpp
// std__type_traits__is_const.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
{
    int val;
};

int main()
{
    std::cout << "is_const<trivial> == " << std::boolalpha
        << std::is_const<trivial>::value << std::endl;
    std::cout << "is_const<const trivial> == " << std::boolalpha
        << std::is_const<const trivial>::value << std::endl;
    std::cout << "is_const<int> == " << std::boolalpha
        << std::is_const<int>::value << std::endl;
    std::cout << "is_const<const int> == " << std::boolalpha
        << std::is_const<const int>::value << std::endl;

    return (0);
}
```

```Output
is_const<trivial> == false
is_const<const trivial> == true
is_const<int> == false
is_const<const int> == true
```

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)\
[is_volatile 类](../standard-library/is-volatile-class.md)
