---
title: is_signed 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_signed
helpviewer_keywords:
- is_signed class
- is_signed
ms.assetid: 20ae44d9-22ad-4fbd-b26a-f18c62689451
ms.openlocfilehash: 5384e1ca8efc24e9cd85968255d4f856a10cafa8
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519654"
---
# <a name="issigned-class"></a>is_signed 类

测试类型是否为带符号整数。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_signed;
```

### <a name="parameters"></a>参数

*Ty*<br/>
要查询的类型。

## <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*Ty*是有符号的整型或`cv-qualified`带符号整型类型，否则为 false。

## <a name="example"></a>示例

```cpp
// std__type_traits__is_signed.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_signed<trivial> == " << std::boolalpha
        << std::is_signed<trivial>::value << std::endl;
    std::cout << "is_signed<int> == " << std::boolalpha
        << std::is_signed<int>::value << std::endl;
    std::cout << "is_signed<unsigned int> == " << std::boolalpha
        << std::is_signed<unsigned int>::value << std::endl;
    std::cout << "is_signed<float> == " << std::boolalpha
        << std::is_signed<float>::value << std::endl;

    return (0);
    }
```

```Output
is_signed<trivial> == false
is_signed<int> == true
is_signed<unsigned int> == false
is_signed<float> == false
```

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_unsigned 类](../standard-library/is-unsigned-class.md)<br/>
