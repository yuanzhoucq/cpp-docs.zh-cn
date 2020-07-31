---
title: is_class 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_class
helpviewer_keywords:
- is_class class
- is_class
ms.assetid: 96fc34a3-a81b-4ec6-b7fb-baafde1a0f4e
ms.openlocfilehash: 4122ad2b4adbd0ed290f26428560c569b3754d7d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222441"
---
# <a name="is_class-class"></a>is_class 类

测试类型是否为一个类。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_class;
```

### <a name="parameters"></a>参数

*Ty*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型*Ty*是定义为或的类型或其中一个类型的形式，则类型谓词的实例为 true **`class`** **`struct`** `cv-qualified` ; 否则为 false。

## <a name="example"></a>示例

```cpp
// std__type_traits__is_class.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_class<trivial> == " << std::boolalpha
        << std::is_class<trivial>::value << std::endl;
    std::cout << "is_class<int> == " << std::boolalpha
        << std::is_class<int>::value << std::endl;

    return (0);
    }
```

```Output
is_class<trivial> == true
is_class<int> == false
```

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>另请参阅

[<type_traits>](../standard-library/type-traits.md)\
[is_compound 类](../standard-library/is-compound-class.md)\
[is_union 类](../standard-library/is-union-class.md)
