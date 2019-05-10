---
title: is_union 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_union
helpviewer_keywords:
- is_union class
- is_union
ms.assetid: 80eda256-40b8-4db5-9ac1-d58bb8032a3e
ms.openlocfilehash: 511dfba92629cfbf71c805a9ea50b8e27f775c54
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413367"
---
# <a name="isunion-class"></a>is_union 类

测试类型是否为联合。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_union;
```

### <a name="parameters"></a>参数

*Ty*<br/>
要查询的类型。

## <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*Ty*是联合类型或`cv-qualified`形式的联合类型，否则为 false。

## <a name="example"></a>示例

```cpp
// std__type_traits__is_union.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

union ints
    {
    int in;
    long lo;
    };

int main()
    {
    std::cout << "is_union<trivial> == " << std::boolalpha
        << std::is_union<trivial>::value << std::endl;
    std::cout << "is_union<int> == " << std::boolalpha
        << std::is_union<int>::value << std::endl;
    std::cout << "is_union<ints> == " << std::boolalpha
        << std::is_union<ints>::value << std::endl;

    return (0);
    }
```

```Output
is_union<trivial> == false
is_union<int> == false
is_union<ints> == true
```

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_class 类](../standard-library/is-class-class.md)<br/>
